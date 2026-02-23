---
tags:
  - CodingProblem
author:
  - jacgit18
Purpose: This a rough thought process breaking down a problem.
Status: Draft
Started: 
EditDate: 2024-02-29
Relates: 
Peer Reviewed: 0
dg-publish:
---
<div style="background-color: orange; padding: 10px; border: 1px solid #ccc; color: black;"> 

<center style="font-weight: bold; ">
TRUE &lt;<mark style="background: #FFF3A3A6;">READ</mark>&gt; FALSE
</center>
 
<p>
Pure Boolean check with UPDATES or no UPDATES needed in terms of what the question is asking but UPDATES can be included depending on the approach you come up with or if the question requires it. Also READ is doing some type of access so be aware of that when creating conditional logic because you optimize your READ  
</p> 


<center style="font-weight: bold; ">
<mark style="background: #BBFABBA6;">CREATE &lt;</mark><mark style="background: #ABF7F7A6;">UPDATE</mark><mark style="background: #FF5582A6;">&gt; DELETE</mark>
</center>
 
<p>
Typically involves READ/UPDATE functionality  which can be also considered as CREATE/DELETE when it comes to UPDATE process and depending on the question and your approach can include CREATE and/or DELETE  
</p> 

</div>

<div style="background-color: grey; padding: 10px; border: 1px solid #ccc; color: black;"> 

<p>
<mark style="background: #FFF3A3A6;">A heuristic technique, or a heuristic, is any approach to problem solving or self-discovery that employs a practical method that is not guaranteed to be optimal, perfect, or rational, but is nevertheless sufficient for reaching an immediate, short-term goal or approximation. </mark>
</p> 

<p>
<mark style="background: #BBFABBA6; font-weight: bold;">Prioritize VISUAL THINKING OVERALL and Talk through you thought have conversation while taking notes </mark>
</p> 

<p>
Talk about code Modularity instead of implementing focus on just creating a working solution and you can refactor or talk about refactoring after     
</p> 

<p>
When thinking about Modularity think about which section of the code can be reused for other things  
</p> 
</div>

> [!important]
> Gen Options available
> 
>- Don't interrupting your interviewer when they are talking. Usually, if they speak, they are trying to give you hints or steer you in the right direction. 
>- Be thoughtful with your questions, don't ask too many especially since you have limited time.
>- Ask the interviewer to restate the question or repeat the question back at the interviewer this gives you time to think  
>- If interviewer tells you to move on you can tell them wait I want to spend a little more time to think about things especially if you know or on something  
>- You can ask to look at documentation like regex or general documentation for syntax since some methods take more parameters than you think 
>- Never make assumptions about the input. Ask for help when unsure but try to communicate the steps in your process or the specific issue 
>- If an interview will give you a harder question after you answer a question that's good they trying to see how high level are you




#### <mark style="background: #BBFABBA6;">
⬇  Identify CRUD in the problem getting a better understanding of what is being asked before thinking about I/O 5 min or less: </mark>

***Similar step in system design but after breaking down problem establish design scope***

## Focus on these interrogative pronouns  

### Try and compress 

- ##### What(broadest question of them all) refer to things - identify the different scenarios/edge-Cases and dependencies   
	- Use **what if questions** for edge cases and using the edge case to figure out what the question is asking. you can rephrase it saying `"can I assume this or that …"` 
	- The focus of these question should be on the edge case  


- ##### Why - identify the root overall or at specific scopes 
	- Can be asked in different ways `"Is there any reason this wouldn't have... "`


- ##### How - identify the steps  
	- This is used after you collect information as define steps you will order them appropriately 


> [!important]  
> Start broad with ***WHAT*** wide open ended questions then when you trying to determine something specific start closing your scope and ask more specific close ended ***WHAT*** questions 
> 
>  Also ***WHAT*** is the  base control flow in the question 

## <mark style="background: #CACFD9A6;">What are initial things to … </mark>

### <mark style="background: #BBFABBA6;">  Created/Store or be added into something </mark>

### <mark style="background: #FFF3A3A6;">Read(Access) or Search which is like access but with a filter that includes iteration to find something specific </mark>

### <mark style="background: #ABF7F7A6;">Update on iteration  </mark>

### <mark style="background: #FF5582A6;">Delete</mark>


### <mark style="background: #BBFABBA6;">⬇ Identify I/O Type examining common properties and variations focusing more on Input 5 min or less </mark>




>[!important] 
> <h2>Properties of Data: </h2>
>
>***Number***(has ascii values) numbers can apply to a lot of diff parms below. Don’t forget [[Algorithm Most Common Built in Functions#Common Math| Math Func ]]
>
> - String(***can iter in array like 2d array for letters ***)
> 	- if string of various characters think ascii a little don't default to it  
> 	- If limited to a specific set of characters, what happens when some are not in the range 
> 	- Alphabeting order  
> 	- **Empty string or spaces in string **
> 	- **Unique or Specific Characters **
> 	- **Unicode string (special characters) **
> - Array of [[Primitive Types]]
> 	- if array of nums check  particular range or DS length, order, type of nums like `Natural num(pos and 0)`, `Integers(Natural and neg)`,  `Rational num(decimal, fraction)`,` Min/Max` , `symmetry of relation(even/odd)`, decimal floor/ceiling, or decimal place 
> 	- Think about what places to iterate from like the beginning, middle or end point
> 	- When dealing with large ranges think about breaking things down to lower sub ranges to reduce iteration 
> 	- if array of strings think built in string/array functions else array of characters you can think more about algo patterns then string methods ask about empty space string length range of characters or special characters 
> - Object
> 	- Advanced Objects/Array Data Structures like Linked List, Tree, Graph, Heap, Sets, etc …. 

### <mark style="background: #BBFABBA6;">⬇ IDENTIFY EDGE and TEST CASES with Control Flow(Break, Continue, SwitchCase) in mind in 10 min or less: </mark>

Test cases In-compass unit test based on a function and what its overall defined logic  is returning 

### Try and compress 



<div style="background-color: grey; padding: 10px; border: 1px solid #ccc; color: black;"> 

<mark style="background: #BBFABBA6; font-weight: bold;">Prioritize VISUAL THINKING OVERALL and Talk through you thought have conversation while taking notes </mark>
 
<p>
Look for obvious checks at pre then post then in the middle and then utilize truth table comparing conditions using the results from table determining which conditions get separated 
</p> 

<p>
If test cases size exceeds two conditions or you use else if think about breaking out into helper function 
</p> 

<p>
Check attributes if num of param greater than one what is being compared if parms are of two array or different Data Structures lean more towards brute force approach especially if problem is complex and specific do `iterative` coding style else you can go a `declarative` 
</p> 

<p>
Think about pre or post computing input/params. Is there a way that you can reorganize the data (`sorting algo`, etc.) or compute some values upfront that will help save time in the long run? and Don't hyper focus on the output too much basically check if input is in a particular order like sorted, partially sorted, and unsorted and see if you can sort as a optimization changing how you traverse(some or every element) beginning/end of data structure or which algo pattern is used or can be ruled out as you render down problem 
</p> 

<p>


You can simplify or tweak some constraint or input, such as the data type. Then, we solve this new simplified version of the problem. Finally, once we have an algorithm for the simplified problem, we try to adapt it for the more complex version.  
</p> 

</div>



         Pre-Condition: at beginning of something 

         General-Conditions: usually inside loop 

         Termination-Conditions: outside of loop or even inside or beginning  

         Post-Conditions: after loop 


Think about how would you test define utilization and over-utilization basically how something should be used and shouldn't be used and how code can be scaled  

identify  use cases, situations, and scenario, bounds and constraints, stresses and failures conditions, and set limitations  


Properties of Edgecase: 



Alt EdgeCase and similarities: 




## Simple Test case: Rules: 
>[!important]
>- new customer -> 15% off 
>- repeat customer -> 10% off 
>- coupon customer -> 30% off 
> 	***num of test case = num of rules = 2^num of conditions = 2^3 = 8 rules*** 
*N = not likely*
**P = probably**
***Identify commonalities between test case***
***Follow Discrete math De-Morgan's Law***

|             Truth  Table                                                                                |            
|-------------|---------|---------|---------|---------|------------|------------|------------|------------|
| new cus     |   T     |   T     |   T     |   T     |    F       |    F       |    F       |    F       |     
| repeat cus  |   T     |   T     |   F     |   F     |    T       |    T       |    F       |    F       |    
| coupon cus  |   T     |   F     |   T     |   F     |    T       |    F       |    T       |    F       |         
| result      |   N     |   N     |   P     |   P     |    P       |    P       |    N       |    N       |    



## Decision table   

Look at all the cases you have and create a long list trying to understand how they overlap and which conditions will be true or false most of the time (which is known as Short circuit Evaluation) especially if combining two or more  condition checks together 

think about different rules and combinations from the input to the output  

decision are the input and actions are the output  

### <mark style="background: #BBFABBA6;">
⬇ LIST potential data structure, built in functions, and pre or post processing is needed under 5 min or less: </mark>



### <mark style="background: #BBFABBA6;">
⬇ Define Naïve-Approach/Pseudocode on whiteboard under 20 min or less: </mark>

Define CRUD of approach identifying and ruling out pathways/pattern   

***Reordered and organize Steps*** while thinking about modular functional pieces that can include things like Boolean functions that check something. ***Render that down into BIG ABSTRACT steps that can be rendered down to sub steps ***

Explain trade-offs, poke holes in logic,  and how the code/approach can be improved if given more time typically at end of working or semi solution. 

Between questions and writing code ask if you can get a minute to think in silence by saying ok interesting can I have a little time to think just limit time keep it like 45-sec shift to another mental tab 

You don't need to code everything if you can mention there might be a cleaner or better way to make it more readable or optimal by refactoring certain parts you could just describe that  



#### Talk about the overall `runtime` and [[Spacetime Complexity | Spacetime]] complexity of your code at different steps or at end 

O(1) + O(n) = O(n) worst runtime takes president when adding up runtime 



> Excellent                                                         Worst



| *Complexity* | Constant | Logarithmic | Linear | Linearithmic | Quadratic | Exponential | Cubic | Fact |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| ***Notation*** | O(1) | O(log n) | O(n) | O(n log (n)) | O(n^2) | O(2^n) | O(n^3) | O(n!) |
|  |  | binaySearch |  | sort/search | nestedLoop | recur | tripLoop |  |
|  |  | DivNConquer |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |
 
***In System design you would propose high-level design within 10 to 15 min then talk more depth about the system for 10 to 25 minutes or so and wrap up in 3 to 5 minutes  ***



### <mark style="background: #BBFABBA6;">⬇ Code if stuck check past steps and Identify Runtime and potential BUD or Optimizations 15 min or less </mark>

When optimizing identify BUD and think about BIG O Processes like Access, Search, Insertion, and Deletion 

And the data Structures associated with them  basically doing a Data Structure Brainstorm also think about past problems that may be similar  

- If stuck, think about related problems you have seen before and how they were solved. 

- If you have to explain a lot of stuff and steps about your code you should probably change your approach. Also If you can't think of naïve approach do a BruteForce or If you have a naïve maybe talk through a BruteForce initially. 


- Solve a simpler version of the problem. Remove or simplify one of the requirements of the problem. Once you have a solution, see if you can adapt that approach for the original question. 

- Solve problem "incorrectly" and then think about why the algorithm fails. Can you fix those issues?   

- Look for any unused info.  


- Start with an inefficient solution. Even if it feels stupidly inefficient, it’s often helpful to start with something that’ll return the right answer. From there, you just have to optimize your solution. Explain to your interviewer that this is only your first idea, and that you suspect there are faster solutions.  


