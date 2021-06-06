+++
author = "Raja Kesari"
title = "World State"
date = "2021-05-27T10:48:01"
description = "World State in Ethereum"
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

Ethereum, or for that matter any blockchain does not store the data like normal databases. Blockchain stores the ‘State’ of the ethereum world. 
<!--more-->

So at what frequency, this state will be stored. I mean at what interval, the ‘state’ of the blockchain will be captured? The answer is “in blocks”. 

The blockchain captures the state after completion of few transactions that are enough to fill a block. The capturing happens once the block of transactions are ready and included in a block and attached to the existing chain of blocks at the end. 

Let’s try to understand the world state in a different way.

The world state can be captured in any model not just blockchain. For example, lets take a cricket match. 

The initial Cricket world state is 
	▪	0 runs
	▪	0 balls
	▪	0 wickets

Now the best frequency to capture the state is “after every ball bowled”. 
To make it similar to blockchain, we can capture it “in overs” where every over is a block consist of 6 transactions.every ball bowled is a transaction here.

Since the number of balls in an over is a constant , we can replace balls with overs in our “world” state.

We can call it as “match” state instead of world state to make it more meaningful but he concept is to capture the current state of the match’s world.


Initial “match” state:
	▪	0 runs
	▪	0 overs
	▪	0 wickets

After first over, the “match” state is:
	▪	4 runs
	▪	1 over
	▪	1 wicket

The block can consist of 6 records with each ball information like
- - - - - - - - - - - - - - - - - - - - 
Ball 1 - Runs:1;Wickets:0; any additional data like bowler:abc/ Batsman: xyz/Wide:false/No-Ball:false/speed of ball:120mph/Like this we can add any information you want to capture
- - - - - - - - - - - - - - - - - - - - 
Ball 2 - Runs:3;Wickets:0; any additional data like bowler:abc/ Batsman: xyz/Wide:false/No-Ball:false/speed of ball:130mph/Like this we can add any information you want to capture
- - - - - - - - - - - - - - - - - - - - 
Ball 3 - Runs:0;Wickets:0; any additional data like bowler:abc/ Batsman: xyz/Wide:false/No-Ball:false/speed of ball:110mph/Like this we can add any information you want to capture
- - - - - - - - - - - - - - - - - - - - 
Ball 4 - Runs:0;Wickets:0; any additional data like bowler:abc/ Batsman: xyz/Wide:false/No-Ball:false/speed of ball:140mph/Like this we can add any information you want to capture
- - - - - - - - - - - - - - - - - - - - 
Ball 5 - Runs:0;Wickets:1; any additional data like bowler:abc/ Batsman: xyz/Wide:false/No-Ball:false/speed of ball:100mph/Like this we can add any information you want to capture
- - - - - - - - - - - - - - - - - - - - 
Ball 6 - Runs:0;Wickets:0; any additional data like bowler:abc/ Batsman: xyz/Wide:false/No-Ball:false/speed of ball:120mph/Like this we can add any information you want to capture. 
- - - - - - - - - - - - - - - - - - - - 
This is very high level. You can include more details from the regular cricket statistics but the above mentioned variables will give a good enough state of the that particular match. 

The Score Card that you see in any cricket match is the Latest block. 

Now the question should be, with how minimally, how optimally we should choose the set of variables that comprise a transaction to make the “world state” minimal but enough to capture a particular world’s state. This will take us to another topic “Transaction”


