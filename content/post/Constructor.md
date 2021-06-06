+++
author = "Raja Kesari"
title = "Constructor"
date = "2021-05-27T10:48:01"
description = "Constructor in Solidity"
tags = [
    "Solidity Concepts",
    "Basics",

]
categories = [
    "Solidity",
    "Concepts",
]
series = ["Solidity Concepts"]
aliases = ["Solidity"]
+++

it is recommended to go through the Smart Contract as we touch some of the smart contract concepts from here.
<!--more-->
When A byte code or smart contract provided for the first time, it has to deploy it to the blockchain but from second time onwards, it doesn’t need to deploy the smart contract. It has to execute the functions from the smart contract as directed.

How the EVM identifies if the smart contract has to be deployed? Well…it can’t unless a constructor is present in the smart contract.  

If we don’t explicitly mention the constructor in the smart contract, a default constructor will be added by solidity compiler. 

Let’s divide the smart contract into its logical parts.

Smart Contract = Constructor + run-time code

Run-time code is remaining part of Smart contract that has to be on the blockchain.

Deploying a smart contract on to blockchain is nothing but executing the constructor part of smart contract.

Deploying a smart contract will create a transaction on the blockchain with a)the run-time code and b)initial storage values(if any defined as part of constructor).

We will discuss the technicalities of EVM and the transaction is coming articles