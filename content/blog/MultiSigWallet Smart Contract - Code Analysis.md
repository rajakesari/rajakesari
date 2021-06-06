+++
author = "Raja Kesari"
title = "MultiSigWallet Smart Contract - Code Analysis"
date = "2021-04-21T00:46:01"
description = "How inline Assembly call used to mitigate Short Address Attacks in MultiSig Wallet Smart contract"
tags = [
    "Solidity",
    "InlineAssembly",
]
categories = [
    "Ethereum",
    "Concepts",
]
series = ["Ethereum Concepts"]
aliases = ["Ethereum"]
+++

I wanted to do an exercise from long time - To understand an already created project, by going through each line of code and see why it was written like that.

I randomly choose gnosis Multisig wallet smart contracts. This is a deprecated version and there is a latest safe version. 

There are many thing that I learned while doing this however I want to share one interesting thing I learned.

The contract MultiSigWallet.sol seems to be taken from the Consensys multiSigWallet.sol but the gnosis has done one change in how the execution of call happens in their contract.

Consensys function for executeTransaction


{{< highlight solidity >}}
    /// @dev Allows anyone to execute a confirmed transaction.
    /// @param transactionId Transaction ID.
    function executeTransaction(uint transactionId)
        public
        notExecuted(transactionId)
    {
        if (isConfirmed(transactionId)) {
            Transaction tx = transactions[transactionId];
            tx.executed = true;
            if (tx.destination.call.value(tx.value)(tx.data))
                Execution(transactionId);
            else {
                ExecutionFailure(transactionId);
                tx.executed = false;
            }
        }
    }
{{< /highlight >}}
	

Gnosis function for executeTransaction has separated the call 


{{< highlight solidity >}}
/// @dev Allows anyone to execute a confirmed transaction.
/// @param transactionId Transaction ID.

    function executeTransaction(uint transactionId)
        public
        ownerExists(msg.sender)
        confirmed(transactionId, msg.sender)
        notExecuted(transactionId)
    {
        if (isConfirmed(transactionId)) {
            Transaction storage txn = transactions[transactionId];
            txn.executed = true;
            if (external_call(txn.destination, txn.value, txn.data.length, txn.data))
                Execution(transactionId);
            else {
                ExecutionFailure(transactionId);
                txn.executed = false;
            }
        }
    }

// call has been separated into its own function in order to take advantage
// of the Solidity's code generator to produce a loop that copies tx.data into memory.

    function external_call(address destination, uint value, uint dataLength, bytes data) internal returns (bool) {
        bool result;
        assembly {
            let x := mload(0x40)   // "Allocate" memory for output (0x40 is where "free memory" pointer is stored by convention)
            let d := add(data, 32) // First 32 bytes are the padded length of data, so exclude that
            result := call(
                sub(gas, 34710),   // 34710 is the value that solidity is   currently emitting
                                   // It includes callGas (700) + callVeryLow (3, to pay for SUB) + callValueTransferGas (9000) +
                                   // callNewAccountGas (25000, in case the destination address does not exist and needs creating)
                destination,
                value,
                d,
                dataLength,        // Size of the input (in bytes) - this is what fixes the padding problem
                x,
                0                  // Output is ignored, therefore the output size is zero
            )
        }
        return result;
    }
{{< /highlight >}}


This is to prevent Short Address Attacks. 

The address.call() pads the data it received with zeroes to make it multiple of 32 bytes. This can cause serious security issues if the intended data is less number of bytes but the actual data that is used by the call function is more(padded with zeroes to make it multiples of 32).

The multisig wallet smart contracts first creates the transaction and once confirmed by multiple owners, that transaction will be sent for execution. As we can see in the consensys multisig smart contract function, the data payload(tx.payload) is given to call but not validating the data or its length.

{{< highlight solidity >}}
     tx.destination.call.value(tx.value)(tx.data) 
{{< /highlight >}}

To avoid any failure that could caused by short address attacks, the call is handled separately in gnosis smart contract. The call is written in solidity assembly here. Before going into how this will resolve the issue in context lets see the assembly call syntax.

{{< highlight solidity >}}
//Inline Assembly: Call - syntax 
Let success := call(gas for call, 
                    To Address, 
                    value to be sent, 
                    address where input data present, 
                    length of input data, 
                    address where output data to be stored, 
                    length of output data)

//Returns if call is not successful
{{< /highlight >}}

When we use ‘call’ in assembly code, we can pass the data(or data payload) and its length separately. 

The function is being passed with the data length (data length). We need to extract the data from the ten.data. The below line of code does that.

{{< highlight solidity >}}
  let d := add(data, 32) // First 32 bytes are the padded length of data, so exclude that
{{< /highlight >}}

 This assigns the value present at the ‘data’ from 33rd byte to d.

Now we have both data length(without any unneccessary padding that could have done by the call function and data in ‘d’.

With this, the ‘call’ will not give unpredicted result. 

