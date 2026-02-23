---
tags:
  - linear
  - dataStructure
author:
  - jacgit18
Purpose: This documentation discusses Singly Linked List.
Status: Refinement
Started: 
EditDate: 2024-02-29
Relates: "[[Type of Linked List]]"
Peer Reviewed: 0
dg-publish:
---
A linked list consists of nodes, with each node containing data and a pointer that links to the next node, creating a chain. The first node in the list is known as the head, and the last node, which points to null, is known as the tail.

![[SingleyLinkedLists.png]]

You can create a Linked List like this:

```Java
LinkedList<String> cars = new LinkedList<String>();
```

```typescript
const cars = new LinkedList<string>();
```


The linked list is often described recursively in terms of nodes, which are scattered throughout memory.

Advantages of linked lists include efficient addition and deletion of nodes by changing where the next pointer points. Linked lists also tend to use memory efficiently when compared to arrays.

Linked lists are useful for adding items without copying to memory, similar to hash tables. However, traversing a linked list can be slower compared to arrays, even though both are technically O(n).

Insertions in the middle of a linked list are more efficient than in an array, and deleting nodes is also straightforward.

One advantage over hash tables is that linked lists maintain order, as each node points to the next node, allowing for sorted data.

Here are the time complexities for common operations on linked lists:

- Prepend: O(1)
- Append: O(1)
- Lookup: O(n)
- Insert: O(n)
- Delete: O(n)

A disadvantage of linked lists is that they are not efficient for retrieving nodes by index or searching since each node only knows the next node in the sequence. You can only traverse from head to tail, not the other way around, and random access is not possible.

Linked lists are linear data structures that can be accessed sequentially.

Applications of linked lists include creating and navigating video or music playlists, representing sparse matrices, and navigating through web pages.

Despite their differences in implementation, all types of linked lists maintain a linear sequence of data elements and are considered linear data structures.

For iterating through linked lists, consider using the "runner" technique, where you use two pointers simultaneously—one ahead of the other. This technique is helpful in many linked list problems.

To determine if a linked list is cyclic, use a faster and slower pointer. If the fast pointer catches up with or passes the slower one, the list is cyclic. If it encounters a null pointer, the list is acyclic.



```javascript
function printFoward(node) {  

let current = node;  

while(current!== null){  

 console.log(current.value)  

 current = current.next  // equvivalent to i++ in a loop  

}  

}  

function printFowardRec(node){  

let current = node;  

if(current!== null){  

   console.log(current.value)  

   current = printFowardRec(current.next)    
 }  
}  
```

```javascript
function reverseListIter(head) {  

if (!head) return null;  

let current = head;  

let previous = null;  

while (current !== null) {  

let next = current.next;  

current.next = previous;   
previous = current;   
current = next;   

}  

return previous;  

};  


function reverseListRec(head, prev = null) {  

if (!head) return prev;  

let current = head;  
let next = current.next;   

current.next = prev;       
prev = current;         

return reverseListRec(next, prev)  

};  
```