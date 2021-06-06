+++
author = "Raja Kesari"
title = "Ethereum Virtual Machine"
date = "2021-05-27T10:48:01"
description = "Ethereum Virtual Machine"
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

Before diving into EVM, let’s try to understand a bit more of What an “Account” meant in Ethereum world and how the “Transaction” effect the World State. Please go through the links, if you have not already done.
<!--more-->

My initial understanding of blockchain was that its a chained database and nothing more it can offer. Later, when I am into learning Ethereum, my idea got changed and I got a conviction that a “blockchain” will do more than just storing the data. Well, I am wrong. Actually, My initial understanding was correct! “Blockchain” cannot offer anything except storing the data.

Yes. Blockchain, at least the Ethereum blockchain can only store the data. When I say blockchain it means only “blockchain”. I am not considering Ethereum Node. The Node is where the actual processing(If any) happens. 

EVM, which resides on the Node, takes the program(Byte-code), data from blockchain and process the data using the program(byte code) and updates the storage on blockchain.

The blockchain captures the transaction. Here, transaction is nothing but  storing some data however, with this data, we can recreate the “change of state” on the Node any number of times. The data(Byte code, storage values) when processed by EVM, always gives the same result. This is the most important property of a blockchain. Determinism.