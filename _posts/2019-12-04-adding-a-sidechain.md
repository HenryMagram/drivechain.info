---
title: Creating a Sidechain
show_author: true
comments: true
date: 2019-12-04 5:00:00
---


Its been over a year since [the last Drivechain Usage Tour](http://www.drivechain.info/blog/usage-tour/). Since then, we've added many features.

The big one is the ability to add a new sidechain, without changing any lines of code.




## Creating A Sidechain

Most people won't want to make a new sidechain, any more than they would want to make a new Altcoin. I expect only about a dozen or so sidechains to ever exist (most Altcoin ideas are just so bad, that they aren't even worth copying).

Nonetheless, people deserve to understand how it happens.

Conceptually, DriveNet has 256 blank 'drivechain slots', each waiting to be assigned to a specific new real-world peice of sidechain software.

We will assign slot #1 to "Testchain", which is [our sidechain template](https://github.com/drivechain-project/sidechains).

Starting with [our latest release of the software](https://drive.google.com/drive/folders/1o83i1N4yPbbKT5hVv_IspNVwHV2jUUoT), here are the steps:

![image](/media/post2/11-drivenet.png)

### 1. Propose Sidechain

The "Sidechains" tab has a little gear button, leading to an important menu where sidechains can be proposed:

![image](/media/post2/12a-propose-sidechain.png)

### 2. The Parameters

The parameters include "address bytes" -- this is how the network identifies sidechain-deposits. These bytes are arbitrary, but must be unique. (Also, the sidechain software needs to use these bytes, to identify deposits sent to it.)

The lower two fields intend to prevent disputes over the "definition" of the sidechain (as is disputed today, wrt BTC, BCH, and BSV each claim to be "the real Bitcoin"). They mark a given software release as authoritative.

( Note: That sidechain can still release new versions of its software -- if those new versions are soft forks, their withdrawals should exactly mirror those of the authoritative flagged release. )

![image](/media/post2/12b-parameters.png)

3. From there, the proposal must achieve a sufficient number of ACKs. Miners can give one ACK per block:

![image](/media/post2/12c-acking-sidechain.png)

4. After sufficient ACKs (eventually, the requirement will be 95% of the past 2016 blocks -- currently it is much lower for easier testing), the sidechain is activated:

![image](/media/post2/12d-sidechain-activated.png)



## 2. Starting up The Sidechain

To start up 'Sidechain One', go into the sidechain folder ("/testchain-3.00.00/"), enter the /bin/ directory, open a terminal, and run './testchain-qt':

![image](/media/post2/13-run-sidechain.png)

Like Lightning nodes, every Drivechain-sidechain require a connection to some Bitcoin Full node. In our case, that full node is DriveNet (the software on the left).

Establishing the connection is easy:

![image](/media/post2/14-rpc-access.png)

![image](/media/post2/15-close-both.png)

Most users will not Blind-Merged-Mine, so they can ignore those warnings.

Now you should be good to go!!

![image](/media/post2/12e-two-softwares.png)
