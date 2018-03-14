---
title: A first survey On smart contracts popularity
author: Santiago Bragagnolo
layout: post
---

# Introduction

When we are doing research, some times we need to choose representative cases to analyze, to be sure that we get the more representative information. 
Depending on the kind of study we do we may need to define rankings over different criterias. 
In this post we talk about popularity related criterias.
How do we know if a contract is popular or not? How do we know what is people using now-a-days in this platform? 
Let's first define what are our metrics.


## Popularity metrics

	
| Metric        	 | Description   | 
| ------------- 	 |:-------------:| 
| Tx Count	         | Amount of transactions including a contract | 
| UT			 | Up time (days) | 
| Deploys		 | Amount of deploys of the same contract | 



## Why these criterias are interesting? 

We can have an over all picture, probably some of these criterias are more obvious than others but, regardless the triviality or complexity we will give a short explanation for each of them.

###Tx Count
This is the amount of transactions over all. This is an obvious first variable to analyze the popularity of a contract, since means how envolved is the ecosystem with this contract. 
The most transactions it has, the most popular it is (or it was). 
###UT
The up time (days) is the amount of days of this contract up (functional) of activity is also important as a way to distribute this large amount of transactions. It allow us to calculate an estimated of transactions per day based on our previous variable. 
It also speaks about maturity of the contract, and support from the ecosystem. The longuer it lasts, the most consolidated it is into the daily life. 
	
###Deploys
The amount of versions speaks about the addition of new functionalities, it speaks about the owner of hte contract trying to enhance his service, by enhancing quality, security or adding new features.
	


## Results
As result of this post, we will provide the results provided by the cited paper. In next posts related with this topic we will provide some of our results (yet cooking).

| # | Contract Name     | Tx count | UT       | Deploys |
|-- |:-----------------:|:--------:|:--------:|:-------:|
| 1 | EtherDelta        | 7203426  | 355      |       4 |
| 2 | Bitcoinereum      | 1948167  | 112      |       1 |
| 3 | KittyCore         | 2647898  | 63       |       1 |
| 4 | ReplaySafeSplit   | 1301418  | 554      |       1 |
| 5 | Registrar         | 1239876  | 271      |       2 |
| 6 | DSToken           | 1166631  | 217      |       1 |
| 7 | Controller        | 937626   | 168      |       2 |
| 8 | OMGToken          | 875921   | 209      |       1 |
| 9 | TronToken         | 920130   | 155      |       1 |
|10 | MCAP              | 635145   | 251      |       1 |
|11 | GolemNetworkToken | 454268   | 366      |       1 |
|12 | SaleClockAuction  | 981683   | 63       |       1 |
|13 | ReplaySafeSplit   | 447007   | 511      |       1 |
|14 | EOSSale           | 426275   | 218      |       1 |
|15 | SNT               | 400735   | 225      |       1 |
|16 | HumanStandardToken| 346242   | 205      |       1 |
|17 | PayToken          | 321557   | 228      |       1 |
|18 | Etheroll          | 325978   | 186      |       4 |
|19 | ReplaySafeSplit   | 273462   | 559      |       1 |
|20 | BAToken           | 244000   | 246      |       1 |


### Popularity indexes

In further posts we will talk more about popularity indexes. For this early post we propose already one naive popularity index:

Pi(c) = \frac{TxCount + versions}{UT}
      

As you can see, this index does not ponderate the flows of amounts of transacionts. So, even when is good enough for showing a general idea of the popularity in the history of the contract, it does not really ponderate the current popularity. 


| # | Contract Name     | Pi       |
|-- |:-----------------:|:-------: |
| 1 | EtherDelta        | 20291.34 |
| 2 | Bitcoinereum      | 17394.35 |
| 3 | KittyCore         | 42030.12 |
| 4 | ReplaySafeSplit   |  2349.13 |
| 5 | Registrar         |  4575.19 |
| 6 | DSToken           |  5376.18 |
| 7 | Controller        |  5581.11 |
| 8 | OMGToken          |  4191.01 |
| 9 | TronToken         |  5936.32 |
|10 | MCAP              |  2530.46 |
|11 | GolemNetworkToken |  1241.17 |
|12 | SaleClockAuction  | 15582.27 |
|13 | ReplaySafeSplit   |   874.77 |
|14 | EOSSale           |  1955.39 |
|15 | SNT               |  1571.51 |
|16 | HumanStandardToken|  1688.99 |
|17 | PayToken          |  1410.34 |
|18 | Etheroll          |  1752.57 |
|19 | ReplaySafeSplit   |   489.20 |
|20 | BAToken           |   991.87 |

## Early conclusions

   It still early to generalize a good way to detect special properties such as popularity. But we have to start by somewhere. 
   I think that this criterias are good even when they still not completely representative due to the lack of time correlation of the variables (Something maybe was really popular on the past and is not popular anymore). We still having much road to walk to understand properly what can we call popularity, but I am quite sure that it should be this way. 
   In further posts we will talk more about indexes and new properties to analyze and rank this information.



