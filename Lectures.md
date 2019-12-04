# Logic Lectures
***
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


***
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

*conditional vs bi-conditional? if jill has a job, she commutes. vs jill only commutes if she has a job*  

1. Jill **and** Bill **both** have jobs  
2. **If** Jill has a job, **then** she commutes  

C. **Either** Jill commutes **or** she does**n't** have a car  


##### Atomic Parts (smallest complete sentences inbetween logic separations):  
* p: Jill has a job
* q: Bill has a job  

* p:Jill has a job
* r: Jill commutes  

* r: Jill commutes
* s: Jill owns a car

##### Replace with symbols
(p /\ q)    ==    p && q
(p --> r)   ==    if(p) { r }
(r \/ ¬ s)  ==    r || !s  

### Discussion 10/3
Ways to show validity:
* Direct: show how every case works
* Reductio ad absurdum: Assume conclusion is false to show how the argument falls apart
* Derivation  

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

***
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
**7_6_1__5__4_3___2__1**  

Base:p q r  
1: ¬p, ¬p *the first acts on a single atomic sentence*  
2: (r v ¬p)  
3: ¬(r v ¬p)  
4: (q->¬(r v ¬p))  
5: (¬p^(q->¬(r v ¬p)))  
6: ¬(¬p^(q->¬(r v ¬p)))  
7: ¬¬(¬p^(q->¬(r v ¬p)))  
***
### 10/9
Basic Truth Tables  
*page 89*  
<table>
<tr><td><b>¬A</td><td><b>A ^ B</td><td><b>A v B</td><td><b>A -> B</td><td><b>A <-> B</td> </tr>
<tr><td><b>F</b> T</td><td>T <b>T</b> T</td><td>T <b>T</b> T</td><td>T <b>T</b> T</td><td>T <b>T</b> T</td> </tr>
<tr><td><b>T</b> F</td><td>T <b>F</b> F</td><td>T <b>T</b> F</td><td>T <b>F</b> F</td><td>T <b>F</b> F</td> </tr>
<tr><td></td><td>F <b>F</b> T</td><td>F <b>T</b> T</td><td>F <b>T</b> T</td><td>F <b>F</b> T</td> </tr>
<tr><td></td><td>F <b>F</b> F</td><td>F <b>F</b> F</td><td>F <b>T</b> F</td><td>F <b>T</b> F</td> </tr>
</table>

**bold is output**  
Example:  
*p64*  
Work by scope degrees  
Base: ¬(p -> (q ^ p)) or (¬(p -> q) ^ p)  
<table>
<tr><td>pq</td><td>¬(p -> (q ^ p))</td><td></td><td></td><td></td></tr>
<tr><td>T T</td><td>¬(T ->(T ^ T))</td><td>¬(T ->T)</td><td>¬T</td><td>F</td></tr>
<tr><td>T F</td><td>¬(T ->(F ^ T))</td><td>¬(T ->F)</td><td>¬F</td><td>T</td></tr>
<tr><td>F T</td><td>¬(F ->(T ^ F))</td><td>¬(F ->F)</td><td>¬T</td><td>F</td></tr>
<tr><td>F F</td><td>¬(F ->(F ^ F))</td><td>¬(F ->F)</td><td>¬T</td><td>F</td></tr>
</table>

| p q r | ((¬(p ^ q) v (q -> ¬r)) -> p) | 											 |							  |          |   |
|-------|-------------------------------|------------------------|----------------|----------|---|
| T T T | ((¬(T ^ T) v (T -> ¬T)) -> T) | ((¬T v (T -> F)) -> T) | ((F v F) -> T) | (F -> T) | T |
| T T F | ((¬(T ^ T) v (T -> ¬F)) -> T) | ((¬T v (T -> T)) -> T) | ((F v T) -> T) | (T -> T) | T |
| T F T | ((¬(T ^ F) v (F -> ¬T)) -> T) | ((¬F v (F -> F)) -> T) | ((T v T) -> T) | (T -> T) | T |
| T F F | ((¬(T ^ F) v (F -> ¬F)) -> T) | ((¬F v (F -> T)) -> T) | ((T v T) -> T) | (T -> T) | T |
| F T T | ((¬(F ^ T) v (T -> ¬T)) -> F) | ((¬F v (T -> F)) -> F) | ((T v F) -> F) | (T -> F) | F |
| F T F | ((¬(p ^ q) v (q -> ¬r)) -> p) | ((¬F v (T -> T)) -> F) | ((T v T) -> F) | (T -> F) | F |
| F F T | ((¬(p ^ q) v (q -> ¬r)) -> p) | ((¬F v (F -> F)) -> F) | ((T v T) -> F) | (T -> F) | F |
| F F F | ((¬(p ^ q) v (q -> ¬r)) -> p) | ((¬F v (F -> T)) -> F) | ((T v T) -> F) | (T -> F) | F |

### Discussion
##### Logical Status:
* Contingent; true in some and false in some interpretations  
* Logically true; all rows are true  
* Logically false; all rows are false == contradiction  

*any sentence of PL is only one of these status*  

##### Consistency:
There exists and interpretation where all sentences (Γ)(gamma) are true (not including atomic definitions)
***

### 10/14 : Quiz
*HWs due on Saturdays, not Mondays*  
##### Joint truth tables
*Squiggly I means interpretation*
* Going over Logical Status again

Shortcuts for symbols:
* Gamma Γ alt+226
* Negation ¬ alt+170
* Biconditional ↔ alt+29
* Conditional → alt+26

***
### 10/16
**Validity == logical consequence**  
##### Single sentence
* Contingent
* Logical Truth
* Logical Falsity  

##### Set of sentences
* Consistency/Inconsistency
* Logical equivalence  

##### Arguments
* Logical consequence  

Γ (gamma) (set of sentences) is consistent if there is a possibility where all arguments are true  
Γ is Inconsistent if for every interpretation there is at least one sentence that is false
* ex) ( p v q ) , ¬ ( p v q )  

##### Logical Equivalence
Every sentence's truth value per interpretation is the same  
ex) p, ¬¬p  

##### Logical Consequence
*A* is the logical consequence of set Γ, such that Γ |= *A*, just in case it is absolutely impossible for all of the sentences in Γ to be true together while *A* is false  
*A* shows that validity exists  
##### Countermodel
Call in interpretation that makes all of the sentences in Γ true while making *A* false a countermodel to the claim that Γ |= *A*  
* *|= is the symbol for logical Consequence, |= with a not equals for Logical Inconsequence*  
* Premises are consistent but the conclusion is false
* Existence of a countermodel voids logical consequence
* Non-Existence of a countermodel proves logical consequence

##### Formatting
Separate premises and conclusion in truth table with double vertical lines  
Separate premises with single vertical line  
Label scope degrees, rows  
Cross out used columns with vertical line
##### Example
Is the claim (p v ¬q), ¬q |= ¬p true?  
*Draw truth table*  
##### Ex 2
1. Someone acts of their own free will only if they could have done otherwise, unless every event has a cause.
2. Every event has a cause if and only if no one could have done otherwise.  
3. |= No one acts of their own free will if no one could have done otherwise.

###### Translation manual  
p= Someone acts of her/his own free will  
q= they could have done otherwise  
r= every event has a cause

###### Translation
1. ¬r → (p → q)
2. (r ↔ ¬q)
3. |= (¬q → ¬p)


### 10/21
*Review Logical Status*  

### 10/28
##### Contrapositive:  
* (A→B)==(¬B→¬A)  
* Equivalent to original conditional

##### Converse  
* (A→B)==(B→A)  

##### Sufficient vs Necessary condition  
* Sufficient: A's condition is enough for B's truth inn (A→B)
* Necessary: The consequent B in the sentence (A→B) is a Necessary condition for the truth if the antecedent A. Intuitively, B's being true is required for A's being true  

##### A square of opposites:
<table>
	<tr>
		<td> must be true </td>
		<td> must be false </td>
	</tr>
	<tr>
		<td> could be true </td>
		<td> could be false </td>
	</tr>
</table>
ex) "must be true" == ¬ "could be false", "could be true" == ¬ "must be false"
<table>
	<tr>
		<td> Everyone is sitting </td>
		<td> No one is sitting </td>
	</tr>
	<tr>
		<td> Someone is sitting </td>
		<td> Someone is not sitting </td>
	</tr>
</table>

### 10/30
Going over the midterm and some ordering and grouping logic game examples

### 10/31 Halloween
##### Discussion  
Contrapositive is equivalent to original, converse and inverse are not.  
Converse == contrapositive of inverse  

##### Necessary vs sufficient
Water is necessary but not sufficient for life  

### 11/04
##### Indirect Proofs to Prove the NONEXISTENCE of a certain Kind of Interpretation
*See indirect proofs notes, posted later*  
##### Reductio ad absurdum
* Assume a claim is truth, show that the assumption leads to a contradiction  

Ex)  
* Show p ^ q |= p v q  

**Stage 1**  
Assume CM
1. p ^ q is true in I
2. p v q is false in I  
**Stage 2**  
By 1 + T^,
3. p is true in I and
4. q is true in I  

By 2 + Fv,
5. p is false in I and
6. q is false in I  
**Stage 3**  
By 3, p is true, but by 5, p is false, so out initial assumption is false  


***See Cheatsheet for proper notes, wait for Discussion***  
### 11/06
Show that p and ¬¬p are equivalent  
Show no interpretation where p is true ands ¬¬p is false  
And no interpretation where ¬¬p is true and p is false  
Assume Countermodel existence  
**Stage 1[reductio assumption]**  
1. p is true in I
2. ¬¬p is false in I
**Stage 2[unpacking truth complexity]**  
By 2 + ¬F,  
3. ¬p is true in I

By 3 + ¬T,  
4. ¬p is false in I
**Stage 3[draw out contradiction]**  
By 1, p is true. By 4, p is false. **Contradiction**  
So, there is no such interpretation  

***Prove other way as well***  
**Stage 1**  
1. ¬¬p is true in I
2. p is false in I
**Stage 2**  
By 1 + ¬T  
3. ¬p is false in I

By 3 + ¬T  
4. p is true in I
**Stage 3**  
By 2, p is false. By 4, p is true.  
So, there is no such interpretation  

***
Show { ( ( p -> p ) -> q ) , ( p -> ( p -> q ) ) } are equivalent  
##### Stage 1

1. ( ( p -> p ) -> q ) is true in I
2. ( p -> ( p -> q ) ) is false in I

##### Stage 2
By 1 + ->T, EITHER  
3. (p -> p) is false in I  
(CONTINUE LATER. NOT DONE)

### 11/27
##### Post Midterm, into ¬I lecture for derivations; See paper notes for derivation notes
<br>
<b>¬Intro</b>
<br>
p, ¬p |- ¬r<br>
| 1. p<br>
| 2. ¬p<br>
|--<br>
| 3.| r<br>
| |--<br>
| 4. ¬r     ¬Intro: 3, (1,2)  // Show an existing contradiction<br>
<br>
{ ¬q, (p -> q) |- ¬p }<br>
<b><i>Modus Tollens</b></i> <br>
// p. 113<br>
<br>
| 1. ¬q      Hyp<br>
| 2. (p -> q)    Hyp<br>
|--<br>
|  |3. p    Hyp<br>
|  |--<br>
|  |4. q    ->E 2,3<br>
| 5. ¬p    ¬Intro 3, (1,4)

### 12/2
##### Review on ¬I
##### Going over PS9
Law of excluded middle  
|- p v ¬p
<br><br>
| //no premises  
|-  
| | ¬(p v ¬p)  
| |-  
| | | p  
| | |-  
| | | p v ¬p  
| | ¬p  
| | p v ¬p  
| ¬¬(p v ¬p)
| p v ¬p  
// *see pic*  
<br><br>
##### v Elim
| i. p v q **hyp**  
|-|-  
| | j. p **hyp**  
| |-  
| | k. q v p **v Intro *j***  
|  
| | l. q **hyp**  
| |-  
| | m. q v p **v Intro *l***  
| n. q v p **v Elim: i, (j, k), (l, m)**

### 12/4
##### Going over the second Midterm
###### For 28, base derivation on <i> The Law of excluded Middle</i>
p v (q v r) |- (p v q) v r  
| p v (q v r)  
|-
| | p  
| |-  
| | p v q <b>v I:2</b>  
| | (p v q) v r <b>v I:3</b>  
|  
| | q v r  
| |-  
| | | q  
| | |-  
| | | p v q  
| | | (p v q) v r <b>v I</b>  
| |  
| | | r  
| | |-  
| | | (p v q) v r <b>v I</b>  
| | (p v q) v r  
|  
| (p v q) v r <b>v E: 1, (,), (,)</b>  

###### 19
p v q, ¬q v r |- p v r  
***see pic, contradiction***
