+++
author = "Raja Kesari"
title = "Smart Contract"
date = "2021-05-27T10:48:01"
description = "Smart Contracts in Ethereum"
tags = [
    "Ethereum Concepts",
    "Basics",

]
categories = [
    "Ethereum",
    "Concepts",
]
series = ["Ethereum Concepts"]
aliases = ["Ethereum"]
+++

To understand the need for a smart Contract in Ethereum framework, we should revisit the Transaction where we discussed that all we can do is one kind of Transaction.
<!--more-->

>   The basic Action in Ethereum is called a “Transaction” and it means “One entity sends “value” to another entity”. 

we can call this “Transaction” as the pure-form or Vanilla transaction.

Let me introduce a non-pure form transaction.

A sends “value”* to B; *Terms & Conditions Apply

And by doing so I already introduced you to concept of Smart Contract.

Ethereum provides option to provide the “Terms and conditions” in the form of Smart Contract. Ethereum is not just a passive blockchain that stores the state. It is a generic framework to “transact” with an option to customization using smart Contracts.

The sweetest part of this framework is, how Ethereum considers even a smart contract deployment as a transaction. A smart contract is a deterministic  transaction/state-change, that is going to happen. 

	▪	A wants to send “value”* to B based on a smart contract - not a transaction
	▪	A deploys a smart contract - Transaction between A and Smart Contract
	▪	The smart contract sends the “value” to B when the requirements met - Transaction between Smart Contract and B

Ethereum recognizes each entity with an address. It even recognizes a smart contract by allocating an address to that smart contract when it is deployed.

So the whole value interchange can be rewritten like below.

	▪	A with Address 0xA wants to send “value’* to B with Address 0xB *Based on a Smart contract - Not a transaction
	▪	A with Address 0xA deploys a smart contract on Ethereum - Ethereum stores the smart contract with an address 0xS - Transaction happened between 0xA and 0xS
	▪	The smart contract with Address 0xS sends the “value” to B with Address 0xB when the requirements met - Transaction happened between 0xS and 0xB

Deploying the smart contract stores the EVM byte code corresponding to that smart contract in the transaction.
