# Linked Lists

## What is a Linked List?

* A Linked List is a sequence of `Nodes` that are connected/linked to each other. The most defining feature of a Linked List is that each `Node` references the next `Node` in the link.
* There are two types of Linked List: ***Singly*** and ***Doubly***.

## Terminology

* Linked List - A data structure that contains nodes that links/points to the next node in the list.
* Singly - Singly refers to the number of references the node has. A `Singly` linked list means that there is only one reference, and the reference points to the Next node in a linked list.
* Doubly - Doubly refers to there being two (double) references within the node. A `Doubly` linked list means that there is a reference to both the `Next` and `Previous` node.
* Node - Nodes are the individual items/links that live in a linked list. Each node contains the data for each link.
* Next - Each node contains a property called `Next`. This property contains the reference to the next node.
* Head - The `Head` is a reference of type `Node` to the first node in a linked list.
* Current - The `Current` is a reference of type `Node` to the node that is currently being looked at. When traversing, you create a new `Current` variable at the `Head` to guarantee you are starting from the beginning of the linked list.

## Traversal

* When traversing a linked list, you are not able to use a `foreach` or `for` loop. We depend on the `Next` value in each node to guide us where the next reference is pointing. The `Next` property is exceptionally important because it will lead us where the next node is and allow us to extract the data appropriately.
* The best way to approach a traversal is through the use of a `while()` loop. This allows us to continually check that the `Next` node in the list is not null. If we accidentally end up trying to traverse on a node that is `null`, a `NullReferenceException` gets thrown and our program will crash/end.
* When traversing through a linked list, the `Current` variable will tell us where exactly in the linked list we are and will allow us to move/traverse forward until we hit the end.

![Node](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LinkedList1.PNG)

Source: <https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/singly_linked_list.html>

## Memory Management

* The biggest differentiator between arrays and linked lists is the way that they use memory in our machines.
* Linked lists don’t need to take up a single block of memory; instead, the memory that they use can be scattered throughout.
* The fundamental difference between arrays and linked lists is that arrays are ***static data structures***, while linked lists are ***dynamic data structures***.
* A ***static data structure*** needs all of its resources to be allocated when the structure is created; this means that even if the structure was to grow or shrink in size and elements were to be added or removed, it still always needs a given size and amount of memory.
* A ***dynamic data structure*** can shrink and grow in memory. It doesn’t need a set amount of memory to be allocated in order to exist, and its size and shape can change, and the amount of memory it needs can change as well.

## Parts of a Linked List

* A linked list can be small or huge, but no matter the size, the parts that make it up are actually fairly simple. A linked list is made up of a series of ***nodes***, which are the elements of the list.
* The starting point of the list is a reference to the first node, which is referred to as the ***head***. Nearly all linked lists must have a head, because this is effectively the only entry point to the list and all of its elements, and without it, you wouldn’t know where to start! The end of the list isn’t a node, but rather a node that points to ***null***, or an empty value.
* A single node is also pretty simple. It has just two parts: ***data***, or the information that the node contains, and a reference to the ***next node***.

![Parts](https://miro.medium.com/max/1400/1*K0_eV07tJtKQSVGKfP18bw.webp)

## Key Takeaways

* A node only knows about what data it contains, and who its neighbor is and this is the very reason why a linked list doesn’t need a contiguous block of memory.
* There are two major points to consider when thinking about how an algorithm performs: how much time it requires at runtime given how much time and memory it needs.
* A linked list is usually efficient when it comes to adding and removing most elements, but can be very slow to search and find a single element.

Source: <https://medium.com/basecs/whats-a-linked-list-anyway-part-1-d8b7e6508b9d>  
Source: <https://medium.com/basecs/whats-a-linked-list-anyway-part-2-131d96f71996>
