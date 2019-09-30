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



Arguments are valid as long as it ** absolutely impossible ** for all the premises to be true while the conclusion is false.
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