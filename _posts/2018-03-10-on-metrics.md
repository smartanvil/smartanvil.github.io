---
title: A First survey on smart contract metrics
author: Santiago Bragagnolo
layout: post
---

	It is not news that the crypto-technologies are spreading faster than a flu. And that they are here to stay a bit longer that just-an-other-hype.
	The speed is not only the important key, but the immaturity of the technologies, and the amount of information mixed with the typical speculation of a for-profit platform.
	

	It's important, specially now, that the technology is taking form, to keep calm, and systematize. Try to cut this new reality in new pieces, and try to measure to have some better understanding of the reality.

	For achieving this propose there are many people around the world working on research and formalizations on different subjects. 


	In this post we will do a quick survey on metrics. The old object-oriented-systems metrics, applied into Smart Contracts (SC) source code.
	This is a natural first step to do before starting to do blockchain specific metrics: to understand how far we are from what we know. 
	To use the known metrics for this new world, and understand if they behave as expected or not.

	For doing this we choosed, for guiding us the paper [Smart Contracs Software Metrics: a First Study] https://www.researchgate.net/publication/322978386_Smart_Contracts_Software_Metrics_a_First_Study. 

	Let's start by define the metrics commonly analyzed, before presenting some existing results. 

## Structural metrics

	
| Metric        	 	| Description   | 
| ------------- 	 	|:-------------:| 
| Total Lines (TL)      	 | Amount of lines in a source code file | 
| Blanks 			 | Amount of blanks lines in a source code file     | 
| Comments			 | Amount of comments defined in a source code file   | 
| ABI				 | Length of the ABI  | 
| Bytecode			 | Length of the Bytecode  | 
| Contracts			 | Amount of contracts defined in a source code file   |
| Functions			 | Amount of functions defined in a source code file   | 
| Payable Functions	         | Amount of functions defined in a source code that are payed |
| Events			 | Amount of events defined in a source code file   | 
| Modifiers			 | Amount of modifier defined in a source code file   | 
| Addresses			 | Amount of addresses defined in a source code file   | 
| Dynamic structures	 	| Amount of mappings, arrays, strings defined in a source code file   | 
| Cyclomatic Complexity 	 | McCabe cyclomatic complexity  | 




## Why these criterias are interesting? 

    This criterias are not really interesting from a developer point of view. The amount of lines or functions or the kind of variables may be good for one problem or bad for an other problem. But they allow us to do a general statistical analysis (based on data mining techniques) and with it, some predictions and assumptions about our results.
    
    Regardless the appearent triviality of many of these metrics, we will give a deeper explanation of each of them. 

* Total lines
	The total lines are count of each line in the file. Including pragmas, libraries, and  even empty lines. 
	This is probable the most lame of the metrics, but then again it helps a lot to categorize a contract. 
	If you come from other software backgrounds, ask your self, is the same a source code of 10 to 20 lines to a source code of 200 to 100 ? Surely not.	
	It is the same a code that has blanks in between functions than other that does not have any blank? Maybe for the compiler. Surely not for me. 

* Blanks
The blanks are the empty blank lines. This lines are counted because they whisper about two things: 
 - Code quality 
  Sometimes blanks are related with nice distribution of definitions, sometimes those are related with an intent of clearify a messy code. 
 - Absence of meaning
  The part of the total lines that are not contributing to the semantic of the contract. Total of lines - blanks = Contributing lines. 
* Comments	
 The comments are also a really light metric. We never know what kind of comment we find, if a usage design comment, an explanation for a dark code or a piece of commented code. 
 But then again this contributes to the construction of a category and profile of a contract.

* ABI
	The ABI (Abstract binary interface) variable stores the lenght of a contract.
	It speaks normally about the complexity of the interaction with a contract. 

* Bytecode
	The bytecode variable stores the lenght of a contract bytecode. 
	This variable speaks about the real comlexity of the contract. 
	And the size of what we can call effective code, since all the hints and modifications are flattened during the compilation.

* Contracts
	This is the first structural variable. 
	This variable measures the amount of contracts in a source file. It may talk about complexity of the problem, it may talk about over design and-or verbosity. 

* Functions 
	Or methods, depending on what is your background. This is the amount of callable (private or public) entities defined inside this file. 
	Regardless the amount of contracts.
	This variable talks about verbosity or about lack of design, since the amount of functions is realted with the feature delegation of the system. 
* Payable 	
	Amount of fuctions that are mean to be payed for the execution of the specific functionality.
	This variable talks about a pretty specific kind of function. 
	

* Events 
	Amount of events defined in a contract. 
	The events are mean to announce important changes to the users. This brings to light then about the synchronization capacity of our contract. 
	And also about the interest of the users.  

* Modifiers
	Amount of modifiers defined in the source code.
	The modifiers are related to the reusage of small portions of code. Normally verifications.
	The modifiers variable may talk about complexity, security and trustability of a contract. 

* Addresses
	The address variable counts the amount of different addresses explicity used in the contract.
	This variable speacks surely about security, and flexibility, since the addresses are usually assigned only once. 
	This kind of data is usually used for verifying. Specially users, as the owner of the contract. 

* Dynamic structures
	This is the first inner containing structure variable. The amount of dynamic structures speaks about the tendency of growing of a contract. 
	And with growing the chance of changing it behaviour. 

* Cyclomatic Complexity
	McCabe's Cyclomatic Complexity speaks about the complexity of an execution path, regarding to it flow graph properties (as branching and reentrance) . 
	In human language, it ponderates the cost of executing. For calculating metrics we sumarize all the public functions complexity.

## Some results
	The paper  [Smart Contracs Software Metrics: a First Study] https://www.researchgate.net/publication/322978386_Smart_Contracts_Software_Metrics_a_First_Study.  comes up with some really helpful results that we put following

|Metric     |Mean |Median| Std |Max |Min| 
|:---:      |:---: |:---:|:---: |:---:|:---:|
|Total Lines | 316.5|201  | 326.9| 4241| 2 |
|Blanks 	    | 55.0 | 32  | 61.4 | 692 | 0 |
|Comments    | 77.6 | 42  | 106.5| 1285|  0| 
|ABI 	    | 3411.4 |2864| 2218.5| 19207| 0| 
|Bytecode |9617.9| 8273| 6944.3 |50607 |15 |
|Contract |9.2| 7 | 8.8| 93 |1|
|Function |25.9| 18| 24.2 |232| 0|
|Payable Functions |1.2| 0 |2 |15| 0 |
|Events |4.6| 3| 4.4 |42| 0|
|Dynamic structures| 2.5| 2 |2.3 |31 |0|
|Modifier| 2.3 |1 |3.2| 26 |0 |
|Address |24.8 |22 |19.7| 176| 0 |
|Cyclomatic Complexity |12.7 |5 |21.4| 537| 1| 

Extracted from the paper: 
Many minima values reult set to zero, since there are a few contracts withalmost no code.  The results on central tendency measures in Tab.  1 showthat the mean is constantly larger than the median, (almost always of abouttwo third) which is a feature typical of right skewed distributions. One simplereason explaining this fact is the lower bound posed to all the metrics by thefact that they are defined null or positive, while, in principle, large valus arenot bounded.  A little exception is represented by the Bytecode metric whichfeatures values for mean and median very close to each other, suggesting a distribution shape which may be not really skewed.  Standard deviations areall comparable with the mean, meaning a large dispersion of values aroundthe last, but there are not cases where it is much large than the mean or the media 

	

## Early conclusions 

   This numbers still pretty dead. As it is concluded in  [Smart Contracs Software Metrics: a First Study] https://www.researchgate.net/publication/322978386_Smart_Contracts_Software_Metrics_a_First_Study, even when there are some models that allow us to apply same properties to this domain, we are not yet able to have good predictions and understanding with such small amount of examples. But we can see surely that even when some of this numbers talk with the same voices of the Object Oriented system results, we still having huge gaps and pretty scattered numbers to analyze.  












