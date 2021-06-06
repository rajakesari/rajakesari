+++
author = "Raja Kesari"
title = "Mapping"
date = "2021-05-27T10:48:01"
description = "Mapping in Solidity"
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

For a long time, I, who is a COBOL developer with little awareness of ‘C’, struggled to understand how the Mapping type works in Solidity. I am keeping a separate article for the same reason. 
<!--more-->

Most of you does not need to go through this article as this is very basic concept which you must have already know. 

So let’s see the syntax of Mapping.
{{< highlight html >}}
			mapping(address => uint) public balances;
{{< /highlight >}}

Every Mapping contains 3 parts:
1. Key type: address
2. Value type: uint
3. The name of the mapping: balances(I want to store balance for each account)

The intention of “mapping” is to store the values(Ex. Eth Balances) without storing their corresponding keys yet keep that key-value relation alive.

In Ethereum, every resource is limited. The memory, Storage, the number of steps to be executed have to be minimal.

Mapping achieves the “minimal” requirement both in terms of storage and CPU usage(to access the data)

The below lines from the mentioned link, provides everything we need to understand about how mapping achieves this.

From https://ethereum.stackexchange.com/a/15341

> Mappings do not store their keys, only the value which is stored at the state memory address calculated by a sha3 hash  > of the the key itself. Any lookup into a mapping has to provide that original key or be able to calculate it.

mapping converts any type of key, be it address or uint or a string type,  to a “memory address value” by running a sha3 hash on the key. By doing this, solidity generalizing and bringing down any key form to a hash value that’s  equivalent to a unique memory address.

This makes the mapping to be a map between Memory address -> Value(Ex. Eth Balances).

This way, solidity able to store a key which is constant in length and unique. 

Since the Mapping do not store the key, the key has to be provided every time a value has to be accessed. This is the reason, you might have seen a separate declaration of array of keys in some smart contracts where there was such requirement.

Please observe, I named the mapping in my example as balance with out bothering about Key. This is because I am storing only balances. Mapping is all about what value you are storing. The mapping with Key actually comes into picture only when you provide the key.

Another important thing is Mappings are only allowed for state variables (or as storage reference types in internal functions).