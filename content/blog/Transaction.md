+++
author = "Raja Kesari"
title = "Transaction"
date = "2021-05-27T10:48:01"
description = "Transactions in Ethereum"
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

Taking the same example of a Cricket match from World State, we will see why using “a ball bowled” as the transaction is right decision.
<!--more-->

You might be thinking “of course! That is obvious” but that doesn’t give us any “way” to learn more about “transaction”. Well! I am sure some of you must be more intelligent than me but my target audience are people like me. 
In this example we have given the “a ball bowled” as a transaction directly. We did not give a chance to analyze ourselves what could be the best choice for a transaction. 

Now we have two questions? 
	1.	Why “a ball bowled” is an obvious choice for a transaction in a cricket match.
	2.	What is such an obvious choice for a transaction in Ethereum world.

To understand this, let’s move away from both Cricket and blockchain. This will give us freedom to give a more generic name to this basic element which we were calling as either “a ball bowled” or a “transaction”. 

Since this “basic element” is what driving a world, 
Since this “basic element” is what changing the state of the world,
Let’s call it as “Action”.

If Ian just knowing about Cricket, I would think below all as actions.
Batsman hitting the ball
Catch by a fielder
Getting out
Hitting a boundary 
Toss

But if have to choose one basic “Action”, it is “the ball bowled” that triggers all other actions.

Now Let’s try to understand the basic “Action” of Ethereum. For this we have to borrow help from Ethereum Yellow paper.

It says Bitcoin is “This system can be said to be a very specialised version of a cryptographically secure, transaction-based state machine.”

And “Ethereum is a project which attempts to build the generalised technology;“

one key goal is to facilitate transactions between consenting individuals who would otherwise have no means to trust one another.


From the above three lines, what I infer is the below.

1. Ethereum is a Generalized, Cryptographically secure, transaction-based state machine.
2. It facilitates give and take between consenting individuals.

And my understanding of the basic “Action” on Ethereum is a “value interchange” between two consenting entities by means of give or take.

Now, we can come back to the naming convention of “Transaction” as we are talking about Ethereum world and the it logically matches with the understanding	of the basic action.

Transaction - a “value interchange” between two consenting entities by means of give or take.

Now let’s see what all possible ways this transaction can take place.

Assume there are two entities A and B

	▪	A gives “value” to B
	▪	B gives “value” to A

Thats it. These are the only 2 transactions in their pure form that can be done on Ethereum.

Well! Only 2?. Can’t we do any other kind transactions… I heard that we can do much more on Ethereum…Wait! What do you mean by “pure form”. 

Yes..You read it right. Infact the two I mentioned above are not two but just one. They both are same kind of transactions. The basic transaction is 
>                “One entity sends “value” to another entity”

Remember we were trying to understand the basic “Action” of Ethereum world. You just read that above.

> The basic Action in Ethereum is called a “Transaction” and it means “One entity sends “value” to another entity”. 

This is what Ethereum stores in its block. A Transaction which has the details of “which entity” sending “what Value” to “which another entity”

This is the state change in Ethereum world. 



