# Logic Lecture

### 9/30
#### Review syl for testing schedule

Arguments are built from premises (the earlier members) and a conclusion (last member)  
*Collection* of premises and a conclusion, just as a collection is defined in java
<p1, p2, pN, C,>  
*p = premises*  

Arg1
1. Jill and Bill both have jobs  
2. If Jill has a job, then she commutes  

C. Either Jill commutes or she doesn't have a car  

Arg2
1. Jill and Bill have jobs.  

C. Jill commutes.  



Arguments are valid as long as it **absolutely impossible** for all the premises to be true while the conclusion is false.
Countermodel: A possibilty where all the premises are true and the conclusion is false.
*if all premises are false and the conclusion is true, one cannot determine validity*  


Arg1:  

*jillJob=true;*  
*billJob=true;*  
*if(jillJob)*  
	*jillCommutes=true;*  
  
*return jillCommutes || !jillCar*   

**Arg1 is valid**
*the terms on either side of the or are disjuncts*
*inside the 'if' is the anticedent, the result is the consequent*  

"A truth funtion operator takes booleans as inputs and delivers a boolean as an output."  

*!* : Negation: truth value flipper; *not*  
"Jill doesn't own a car"  
turns into  
"It is not the case that Jill owns a car"  
*== !(jillCar)*  



### 10/2
#### Reviewing how to submit problems sets
* Submit to TA

#### premises + conclusion = argument  
Page 18:

| type           | English form   | symbol    | CS equivalent | Example(25) |
|----------------|----------------|-----------|---------------|-------------|
| negation       | not            | ¬         | !             | not         |
| conjunction    | and            | ^         | &&            | but, and    |
| disjunction    | or             | v         | ||            | or          |
| conditional    | if, then       | -->       | if            | if          |
| bi-conditional | if and only if | <->       | if            | 

*conditional vs bi-conditional? if jill has a job, she commutes. **vs** jill only commutes if she has a job*  

1. Jill **and** Bill **both** have jobs  
2. **If** Jill has a job, **then** she commutes  

C. **Either** Jill commutes **or** she does**n't** have a car  


##### Atomic Parts (smallest complete sentences inbetween logic separations):  
*p: Jill has a job
*q: Bill has a job  

*p:Jill has a job
*r: Jill commutes  

*r: Jill commutes
*s: Jill owns a car

##### Replace with symbols
(p /\ q)    ==    p && q
(p --> r)   ==    if(p) { r }
(r \/ ¬ s)  ==    r || !s  

### Discussion 10/3
Ways to show validity:
*Direct: show how every case works
*Reductio ad absurdum: Assume conclusion is false to show how the argument falls apart
*Derivation  

Contrary: Both cant be true at once
Contradictory: Only one is true  

Page 27:
<blockquote>
You are already familiar with the idea of parentheses and “order of operation”
from basic arithmetic. Consider the arithmetical expression ‘2+3*5’,
ignoring conventions governing the order of operations. What is its value? 25
or 17? It is (absent the disambiguating conventions we asked you to set aside)
undefined, as there are in fact two distinct functions that the term can be taken
to express, as follows: ‘(2+3)*5’ and ‘2+(3*5)’. The first is primarily a multiplication
function (with an addition function used to determine its first argument)
and the second primarily an addition function (with a multiplication function
used to determine its second argument). A true sentence results from adding
‘=25’ to the first and a false sentence results from adding the same to the second.
But adding ‘=25’ to the original, ambiguous expression results in neither
a true nor false sentence. 
</blockquote>  

To find main operator:
(¬(p^q)^r))  
**The 2nd ^**  
work from inside out and the last 2 place truth functional operator is the **main operator**  


### 10/7

Page 25:
<blockquote>
Translating Material Conditionals  
A only if B => A -> B  
A if B => B -> A  
A when B => B -> A  
A provided B => B -> A  
A unless B; Unless B, A => ¬B -> A    
  
</blockquote>    
	
Ex)  
**George is happy, unless he goes to work, in which case he doesn't get dessert.**  
p=George is happy  
q=George goes to work  
r=George gets dessert  
p unless q in which case not r  
if not q then p and not r  
**((¬q->p)^¬r)**, could also be **((¬q->p)^(q->¬r))**  
  
Testing for grammaticality: pg 35  
*find other reason on page 35 for why not grammitcally correct*  


##### Scopes
¬(p^q), (¬p^q)  
Base: p q  
1:  (p^q)       ¬p  
2: ¬(p^q)      (¬p^q)    

**¬¬(¬p^(q->¬(r v ¬p)))**  
**76 1 5  4 3   2  1**  
  
Base:p q r  
1: ¬p, ¬p  
2: (r v ¬p)  
3: ¬(r v ¬p)  
4: (q->¬(r v ¬p))  
5: (¬p^(q->¬(r v ¬p)))  
6: ¬(¬p^(q->¬(r v ¬p)))  
7: ¬¬(¬p^(q->¬(r v ¬p)))  