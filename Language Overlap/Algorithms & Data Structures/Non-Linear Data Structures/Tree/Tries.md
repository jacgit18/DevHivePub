---
tags:
  - dataStructure
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Trie.gif]]

A **Trie**, pronounced as 'try' and also known as a prefix tree, is a specialized type of search tree used for efficient word storage and retrieval. In a Trie, data is organized in a stepwise fashion, where each step corresponds to a node in the Trie. This data structure is commonly employed for quick word lookups, such as in auto-complete features.

In a language Trie, each node represents a single letter of a word. To spell a word, you traverse the Trie by following branches, one letter at a time. As you progress, nodes diverge to represent different word paths or mark the end of a word. Each node contains two essential components: a letter (the data) and a boolean that signifies whether the node is the final character of a word.

Consider the example image to better understand how words can be formed. Always start at the root node at the top and work your way down. The Trie illustrated here contains words like "ball," "bat," "doll," "do," "dork," "dorm," "send," and "sense." It's important to note that a Trie can be constrained to limit how and where data is stored within it, but this is a more advanced concept beyond the scope of this explanation.

Tries are highly versatile for storing letters of the alphabet and characters. By skillfully traversing the Trie, you can construct words in various ways. Tries are sometimes referred to as prefix trees, particularly in the realm of discrete mathematics.

The Trie starts with a root node, which is usually empty, often represented by a blank value like an empty string or null. The root node has an array of references that start as null, and these references can be gradually populated with references to other nodes.

Let's say we're creating a Trie to store words that start with the letter 'd.' The root node would contain an array with a reference to a node representing the character 'd,' signifying the beginning of words starting with 'd.' The 'd' node would, in turn, have its own array containing references to characters in the alphabet, which represent the first two characters of words in the English dictionary starting with 'd' (e.g., "da" or "de").

This pattern continues for each subsequent letter until you reach a designated flag that signifies the end of a word.

Tries have practical applications and can be found in tools like Grammarly, Pro-Rite Aid, and autocorrect systems.

In summary, a Trie can be visualized as an array with a tree structure inside it, providing an efficient way to store and search for words and data.