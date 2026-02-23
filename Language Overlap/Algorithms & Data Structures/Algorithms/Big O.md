---
tags:
  - CodebaseDecision
  - timeComplexity
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses runtime complexity.
Status: Refinement
Started: 
EditDate: 2024-02-27
Relates: 
Peer Reviewed: 0
dg-publish:
---

![[BigO.gif]]

In the realm of algorithm analysis, it's essential to understand the various factors that affect an algorithm's runtime. 

Runtime can vary significantly across different cases, including **Worst**, **Average**, and **Best** scenarios, particularly when it comes to sorting algorithms.

![[Runtime Big O.png]]
<mark style="background: #FFB86CA6;">Scale Ascending from 🔼 EXCELLENT to WORST TIME 
lower EXCELLENT runtime + higher WORST runtime = higher WORST runtime</mark>

Let's delve into how to calculate the runtime of an algorithm, especially when you're dealing with complex algorithms composed of multiple parts with different runtimes. The key principle is that the worst-case runtime dominates and determines the overall complexity.

For instance:
- If you have part of an algorithm that is O(n)  and another part with O(n log(n)), the overall complexity is O(n log(n)), as it trends 🔼 towards the worst-case runtime.

In Big O notation, the dominant term is the one that matters most so for example:
`O(n) + O(n log(n)) = O(n log(n))` 

In this example, O(n log(n)) dominates O(n), so the hypercritical algorithm go ends being the worst runtime out of the two.

If you console log the first two index of an array in your function it is considered two operations so it will be <mark style="background: #FFF3A3A6;">O(2)</mark> but it will still be <mark style="background: #FFF3A3A6;">CONSTANT TIME O(1)</mark> the two is just a number we will default to O(1) because operation tends to increase but as long as it is <mark style="background: #FFF3A3A6;">CONSTANT TIME</mark> we just say <mark style="background: #FFF3A3A6;">O(1)</mark>  because the time it takes to perform an operation doesn't depend on the size of the input. So, whether you're logging the first two elements or performing other operations on them, as long as the number of operations remains the same and doesn't scale with the size of the input, it's considered constant time, or O(1).

`O(1) + O(1) +O(1) + O(1)` = O(1)` 

In big O notation, O(1) is used to describe operations that have a fixed or constant time complexity, and this remains true even if there are multiple constant-time operations performed.


**Understanding Big O Notation**

Big O notation is a way to describe how the efficiency of an algorithm changes with input size. It helps us understand the rate of growth or decline of a function as it approaches a limit. Here's a quick overview of some common notations:

- **O(*Landau*)**: Represents an upper bound or **worst-case** scenario. For instance, O(n) denotes linear time complexity. ^93b0ef
- **Ω(*Omega*)**: Represents a lower bound or **best-case** scenario. Ω(n) means that the algorithm's runtime won't be faster than linear. ^64043d
- **Θ(*Theta*)**: Denotes an **average-case** scenario between the worst and best cases. ^68b727

You can find more information on time complexity analysis notations [here](https://cs.stackexchange.com/questions/57/how-does-one-know-which-notation-of-time-complexity-analysis-to-use).

## Factors Affecting Runtime

The runtime of an algorithm can be influenced by several factors, such as:
- Operations (+, -, \*, /)
- Comparisons (<, >,\==)
- Looping (for, while)
- External function calls
- Recursive function calls

## Categories of Runtime

In the world of algorithm analysis, we categorize runtimes into different classes based on their growth rates. Let's explore some of these categories:

### Constant Time O(1)/Excellent: 
- Represents algorithms with a fixed number of operations, regardless of input size. This is ***Excellent runtime***, as you don't need to worry about input size. Examples include **merge**, **quick**, and **heap** sort algorithms.

	- A classic example of constant time is basic arithmetic, like **5 + 5**. No matter the numbers involved, the time it takes to perform this addition operation remains constant and does not depend on the numbers themselves.
	- Another example is when we loop through a print statement. Even if you print one item or a million items, the time it takes to execute the print statement remains constant, making it an **O(1)** operation.
	- Now, consider a function that takes an array of boxes as input. If this function performs a single action on each element, such as inspecting or modifying it, the time it takes to process each element is constant. Thus, as the number of operations scales with the size of the array, the overall time complexity remains **O(1)**. This is desirable because it means we don't have to worry about the input size affecting the efficiency of our algorithm.
	- it's worth noting that sometimes, even if a function appears to involve multiple operations, as long as those operations are not dependent on the input size, we still categorize it as **O(1)**, for instance, when you "console.log" the first two indices of an array in your function. Although it's two operations, it remains a constant time operation because the number of operations does not grow with the size of the input.

The runtime complexity `O(a * b)` represents what is called `"linear with respect to two variables"` or "product complexity." It means that the runtime of an algorithm or code segment grows proportionally with the product of the sizes of two input variables, a and b. The runtime is directly related to the sizes of both collections or data structures a and b. If you were to double the size of both a and b, the runtime would approximately double as well. This is why it's called linear with respect to two variables, as the runtime increases linearly with the product of the input sizes.
### Logarithmic Time O(log n): 
- Commonly found in binary search or divide and conquer search, where the search space is halved with each iteration. This is considered a ***Good runtime***, as it's efficient for large datasets. You can think of this as going through a dictionary book that is a large sorted data set trying to find a word under S and reducing the time by going to S. 

```javascript
function printPowersOfTwo(n) {
    for (let i = 1; i <= n; i = i * 2) {
        console.log(i);
    }
}

// Usage
printPowersOfTwo(16); // Replace 16 with any value of n you want to print powers of 2 up to
```

### Linear Time O(n):
- Occurs when the algorithm's runtime scales linearly with the input size. It's ***Fair runtime*** but can be less efficient for larger datasets. Examples include finding the maximum element in an unsorted array and duplicate element detection with a hash map generally any looping it just depends what your doing on each iteration like looping a console log string message would be O(1).

- **O(n + m)** working with two separate loops  which ends up by Linear time

### Linearithmic Time O(n log(n)):
- Typically associated with sorting and searching operations. Merge and quick sort algorithms fall into this category.

### Quadratic Time O(n^2): 
- This runtime is considered ***horrible runtime*** and arises when you compare every element in a collection to every other element. Nested for loops can result in this runtime, but non-nested loops follow O(n \* m) scaling.

- Quadratic time complexity is typically encountered when you need to compare every element in a collection to every other element, such as when searching for duplicate elements in an array or using a sorting algorithm like bubble sort.

### Exponential Time O(2^n): 
- Recursive algorithms that grow exponentially. This runtime is often associated with tree and graph problems.

### Cubic Time O(n^3): 
- Occurs with triple-nested loops or solving equations with three variables.

### Factorial Time O(n!)/Worst: 
- The slowest rate of growth or ***Worst runtime*** , where you add a loop for every element. This is particularly inefficient and should be avoided whenever possible.

- Factorials (!) are products of every whole number from 1 to n. In other words, take the number and multiply through n to 1.  

	- If n is 3, then 3! is 3 x 2 x 1 = 6. 

Find all permutations of a given set/string is an example of factorial time

## Calculating Big O and Rules

When calculating Big O notation, there are a few rules to keep in mind:

1. **Drop the Constants**: Since Big O notation focuses on the rate of growth, constants can be dropped. For instance, O(2n) simplifies to O(n). Constants only matter when dealing with quadratic (O(n^2)) or exponential (O(2^n)) time complexities.

2. **Drop the Non-Dominant Terms**: In an expression like O(N^2 + N), you can drop the non-dominant term. If the latter N term doesn't significantly affect the runtime, it can be ignored.

3. **In If-Else Blocks, Choose Maximum Complexity**: Big O analysis should focus on the worst-case scenario. Therefore, choose the block with the highest complexity for your calculations.

4. **Runtime of Loop Blocks**: The runtime of a loop block is equal to the runtime of the statements within the loop multiplied by the number of iterations.

So in the end the reality is that some algorithms best cast would be O(n) and there may not be any way of improving it more 
