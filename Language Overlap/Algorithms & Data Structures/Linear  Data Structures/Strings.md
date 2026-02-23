---
tags:
  - primitiveType
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses strings.
Status: Refinement
Started: 
EditDate: 2024-02-29
Relates: 
Peer Reviewed: 0
dg-publish:
---
Strings, despite being one of the first data structures introduced to programmers, shouldn't be underestimated as "easy" in interview scenarios due to their versatility. Unlike data structures like trees or graphs that have specific algorithms like DFS/BFS or backtracking respectively, strings can incorporate a range of technical topics frequently asked in interviews. Strings are a linear data structure, and because of that all common algorithms related to linear data structures could potentially be involved in a string question. This means techniques like [two pointers](https://interviewing.io/two-pointers-interview-questions), [sliding windows](https://interviewing.io/sliding-window-interview-questions), [recursion](https://interviewing.io/recursion-interview-questions), backtracking, and [dynamic programming](https://interviewing.io/dynamic-programming-interview-questions) (to name just a few) can be used in a string question. Therefore, avoiding string practice due to perceived ease could lead to challenges in handling complex string problems in interviews.


### Messing Up String Conversions

One of the more annoying things we can have to do, which nevertheless comes up fairly often, is various forms of string math. This includes converting characters to their index in the alphabet and converting characters to their numeric value. General familiarity with how to do these things in your interviewing language is critical. It's obscure enough to not remember on the spot, but simple enough that it looks bad if you don't know how to do it.

### Making Assumptions About String Contents

It's easy to think of strings as just letters in the alphabet, but this will lead to one of the most common interview errors with string questions – making an incorrect assumption about the string contents. Useful clarifying questions to ask whenever strings are involved in a problem can be questions like.

- Are we guaranteed that there will just be alphabetical characters? Alphanumeric?
- Do we need to worry about punctuation?
- Do I need to handle special characters/symbols?
- Can the string ever be empty or null?
- Is the string always lower/uppercase? Can we receive a mixed case string?
- Do we need to worry about the string encoding at all? UTF-8, ASCII, etc?
- Does the string fit into memory?

Here's a good example of a string question where [all of these questions matter](https://leetcode.com/problems/ransom-note/) in achieving the correct output to pass all tests. Don't make assumptions about what is in the string, asking these types of questions helps demonstrate your seniority and familiarity with common gotchas.

### Hidden Complexity

One danger you should be aware of is how languages will abstract away the heavy lifting when it comes to strings. This can make us wrongly assume that "simple" operations are cheap. For example, we can very easily get a substring of a string in Python using the Python slicing syntax: s[1:5]. Writing it this way we may assume that this is a constant-time operation. However, in most cases, operations like this are still going to copy the substring (remember strings are immutable), meaning that it is going to take us linear time.

## Advanced String Topics

### The Multiple Pointers Technique

Same as with arrays, it is common to use multiple pointers to traverse a string. This allows us to accomplish various interesting tasks with substrings and comparing characters. Here are some problems to consider:

- [Reverse words in a string](https://interviewing.io/questions/reverse-words-in-a-string)
- [String compression](https://leetcode.com/problems/string-compression/)

### The Sliding Window Technique

[**Sliding windows**](https://interviewing.io/sliding-window-interview-questions) are common with any linear data structure. That includes things like arrays, linked lists, and, of course, strings. They are a great tool for finding the longest substring matching an arbitrary property. For practice take a look at the following.

- [Longest substring without repeating characters](https://interviewing.io/questions/longest-substring-without-repeating-characters)
- [Longest substring with at least k repeating characters](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/)
- [Find all anagrams in a string](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

### Advanced String Algorithms

These advanced algorithms are fairly niche and only likely to be asked at FAANG companies, and even then these algorithms show up a small fraction of the time. If you want to go deep on strings, there are three advanced algorithms worth having on hand. All of these algorithms are used for searching for a substring within a string and variations of them exist in a handful of problems online. The core algorithms to learn are:

- [KMP](https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm)
- [Boyer Moore](https://en.wikipedia.org/wiki/Boyer%E2%80%93Moore_string-search_algorithm)
- [Rabin-Karp](https://en.wikipedia.org/wiki/Rabin%E2%80%93Karp_algorithm)

### [[Regular expression]]

While it is unlikely that you will get a problem which can be solved directly with regular expressions, you should have a good idea of how regular expressions work. Leetcode questions with regular expression answers [do exist](https://leetcode.com/problems/solve-the-equation/description/), but are uncommon. If you're thinking of using regular expressions in your solution, you're probably over-complicating it. With that stated, it is still important to have familiarity with them. Consider playing with a site like [regex101.com](http://regex101.com/) to develop a better sense of regular expressions. Additionally, spend some time thinking through how to document a regular expression. Demonstrating not just an understanding of regular expressions but how to make them maintainable shows a certain coding maturity.