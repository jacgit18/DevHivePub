---
tags:
  - CodingProblem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses finding conditional logic.
Status: Done
Started: 
EditDate: 2024-02-29
Relates: 
Peer Reviewed: 0
dg-publish:
---
To identify conditional logic in a coding challenge problem statement, you can:

1. **Search for Keywords:** Look for words like "if," "else," "switch," or "when" as they often indicate the presence of conditional statements.

2. **Scan for Decision Points:** Identify decision points where the program needs to take different paths based on certain conditions.

3. **Examine Constraints:** Check for constraints or requirements that involve specific conditions, as they might hint at conditional logic.

4. **Analyze Input-Output Scenarios:** Understand how the program should behave under different input scenarios; this can reveal conditional statements.

5. **Check for Loops:** Sometimes, loops with conditions can be mistaken for conditional logic, so ensure you differentiate between iterative and conditional structures.

6. **Look for Case-Specific Instructions:** If the problem statement asks for specific actions under certain conditions, there might be conditional logic involved.

7. **Explore Error Conditions:** Investigate error handling or exceptional cases, as they often involve conditional statements.

8. **Examine Variable Usage:** Analyze how variables are used and modified based on specific conditions.

By systematically examining these aspects, you can effectively identify and understand the conditional logic embedded in a coding challenge problem statement.

## Problem Example 
You are given a list of songs where the `ith` song has a duration of `time[i]` seconds.

Return _the number of pairs of songs for which their total duration in seconds is divisible by_ `60`. Formally, we want the number of indices `i`, `j` such that `i < j` with `(time[i] + time[j]) % 60 == 0`.

**Example 1:**

**Input:** time = [30,20,150,100,40]
**Output:** 3
**Explanation:** Three pairs have a total duration divisible by 60:
(time[0] = 30, time[2] = 150): total duration 180
(time[1] = 20, time[3] = 100): total duration 120
(time[1] = 20, time[4] = 40): total duration 60

**Example 2:**

**Input:** time = [60,60,60]
**Output:** 3
**Explanation:** All three pairs have a total duration of 120, which is divisible by 60.

**Constraints:**

- `1 <= time.length <= 6 * 104`
- `1 <= time[i] <= 500`

## Application of Methodology 
Let's apply the methodologies to identify the conditional logic in the given problem statement:

1. **Search for Keywords:** Look for phrases like "total duration divisible by 60" and "(time[i] + time[j]) % 60 == 0." These indicate the presence of conditional logic related to divisibility by 60.

2. **Scan for Decision Points:** Identify the decision point involving the condition `(time[i] + time[j]) % 60 == 0` where the program decides if the total duration is divisible by 60.

3. **Examine Constraints:** The constraints indicate the range of values for `time[i]` and set the boundaries for the problem.

4. **Analyze Input-Output Scenarios:** The output depends on pairs of songs where the total duration is divisible by 60, highlighting the conditional nature of the problem.

Now, let's list the conditional logic:

- Conditional Statement: `(time[i] + time[j]) % 60 == 0`
- Decision Point: Checking if the sum of durations is divisible by 60.
  
Therefore, the conditional logic is based on checking whether the total duration of pairs of songs is divisible by 60.