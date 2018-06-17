
---
title: A first survey On smart contract static analysis 
author: Santiago Bragagnolo
layout: post
---

## Introduction 
	
Following the line of understanding our code and understanding what may be an issue in the future (as in the metrics posts) we continue by trying to understand a bit more on the potential issues that a smart contract may have. 
There is a lot told about the most epic failures on contract development, but epic failures are the result of a sumatory of small problems. 
In this subject there are some just starting researches such as [SmartCheck: Static analysis of Ethereum Smart Contracts] (cite), [Smart Contracts Vulnerabilities: A call for Blockchain Software Engineering ] and [Towards analyizing the Complexity Landscape of Solidity Based Ethereum Smart Contracts ]. 
And as they do, we care more about the contract development complexity than about the underlying security. 

We do also summarize into this post some of the detectable security issues defined in the post [cite post].

In what it comes to issues on contract code we recognice the following contract-centered categories.
	
 - Functional
 - Non Functional
 - Etiquette
 - Security

The issues that we will procceed to propose, are problems that are possible to detect by doing static source code analysis. 


## Functional
In this section we address the pieces of code that may not behave as expected in a highlevel virtual machine language, and that may impact over the behaviour of our contracts.
	
	
Native types
------------

Solidity provides native types in the quest of ensuring that the user can choose the size that fits better the needs. 

But, this comes with some maybe unexpected old problems:
 - Overflow 
 - Underflow 

The usage of arithmetical and functional operations may lead to unsafe assignments. This kind of error is quite complex to recognice and it may deal to disasters, such as unexpected values, and therefore, unexpected behaviours.



Incomplete numerical representation
-----------------------------------
 EVM does not provides yet decimal nor floating point numerical representations.
 This means that any function meant to map any value to decimal nubers, based in native types, will be forced to round
 up / down the results into integer representations. 

 The most canonical example of this problem is the division. Any division in between two integer, in our current EVM implementation, will round down the results up to the closer integer representation.
 No need to explain how bad would be to not have this in mind when developing a smart contract. 


Unsafe type inference
----------------------
 Solidity provides, as many other languages, the keyword 'var', used for defining types of variables in terms of the assigned expression. 
 Extracted from  [SmartCheck: Static analysis of Ethereum Smart Contracts] (cite), the following example illustrate pretty well our problem:

	for(var i = 0 ; i < \array.length ; i++)
  

 Meanwhile the compiler would match the type of the variable I with it assigned expression, (0; therefore uint8), array.length may hold a number several orders bigger. 
If this happen, this type inference will lead us to an overflow, and maybe to an infinite loop. 


Using scope 
-----------
  Solidity provides a nice functionality to extend native and non-native types, in the fashion of scoped traits [cite].
  The clause <<for 'TypeName' using 'Library'>>. To understand the types and the scope of them is pretty important to ensure the expected behaviour. 
  


## Non functional
In this section we address the pieces of code related to the spent of resources such as execution and storage. 

Money talks
-----------
With the idea of gas, and execution fee, we have to keep track of the code we type pretty much. From the structures used to the solution strategies. 

  - Byte array. Prefer the use of the type 'bytes' instead of 'byte[]'. It has a smaller footprint. 
  - Loops. Loops are one of the most important reasons for ethereum to use the GAS system.
    * Ensure low complexity inside loops
    * Ensure to control the breaking condition
    * Ensure to not use external calls into
    * Ensure the usage of break in searches
[CHECK]
  - Recursive calls. The other reason for the GAS system are the recursive calls. 
    * Ensure to know your recursive calls
    * Ensure the base case
	
Those little annoying details
-----------------------------
  - The compiler version pragma uses fixed and unfixed version:	^ 0.4.1 vs 0.4.1
    * Ensure to know your pragma.
[CHECK]
    * On unfixed versions, ensure that your code is easy to compile.
    * On fixed versions, ensure that your version is maintained.
  - The modifiers. 
    * Ensure to know them all. 
  

## Etiquette
	In this section we address the nomenclatures and other etiquette definitions 
  Solidity as many other languages has it's style guide. The style of your code is like the code of a party. A code with wrong style looks as embarrasing as your suit at the your mother law's spring hippie party.

   - Variable naming
   - Functions naming
   - Events naming 
   - Types naming
  
## Security
 In this section we cite some structures that lead to possible vulnerabilities. For understanding in deep these vulnerabilities, we suggest you to check our post on vulnerabilities [link to post].
 The pieces of code that we address in this section, eventho there are correct, they may be used for exploiting the contract's logic.
 
   
   - Avoid to branch (if|for|while|do while) your code on equality (==) over uncontrolled, divergent variables. 
      Equality is a really specific case. It would be easy to push this contract into a denyial of service. 

   - Avoid to branch (if|for|while|do while) your code on external calls, specially on unknown parties.
      Taking decisions of behaviour over third parties makes your code potentially unpredictable and, again, easy to push into a denyial of service. 

   - Mind the reentrancy on the access to contract state variables.
      Specially those that are used as barriers. Reentrancy is not always obvious in ethereum. Recursive calls can happen from fallback functions, and lead to many vulnerable states. 

   - Check the addresses on transfer - the ether transferred to unexistant accounts cannot be recovered - 
      Eventhou an address is valid, it does not means that the address is bounded to any existing account. Ensure that the transfers are done to existing accounts. 

   - Avoid to use dynamic Libraries from untrusted / unknown parties. 
      Since libraries's functions are called with delegatecall, the wallet used by this functions is the calling wallet.
   
   - Ensure your setters to ensure calling users. 












