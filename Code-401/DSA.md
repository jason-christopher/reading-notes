# Data Structure and Algorithms

## Data Structures

***Data Structures*** are a specialized means of organizing and storing data in computers in such a way that we can perform operations on the stored data more efficiently.

8 Basic Data Structures are:  

1. **Arrays** - a structure of fixed-size, which can hold items of the same data type.
   * Array operations:
      * Traverse: Go through the elements and print them.
      * Search: Search for an element in the array. You can search the element by its value or its index
      * Update: Update the value of an existing element at a given index

   ![Array](https://miro.medium.com/max/1400/1*pYIKtQYbX8vgCWrwe1YOyg.webp)

2. **Linked List** - a sequential structure that consists of a sequence of items in linear order which are linked to each other.
   * Linked list operations:
      * Search: Find the first element with the key k in the given linked list by a simple linear search and returns a pointer to this element
      * Insert: Insert a key to the linked list. An insertion can be done in 3 different ways; insert at the beginning of the list, insert at the end of the list and insert in the middle of the list.
      * Delete: Removes an element x from a given linked list. You cannot delete a node by a single step. A deletion can be done in 3 different ways; delete from the beginning of the list, delete from the end of the list and delete from the middle of the list.

   ![Linked List](https://miro.medium.com/max/1400/1*4fuF6lHXOSmoVNcOV8aaJA.webp)

3. **Stack** - a LIFO (Last In First Out — the element placed at last can be accessed at first) structure which can be commonly found in many programming languages.
   * Stack operations:
      * Push: Insert an element on to the top of the stack.
      * Pop: Delete the topmost element and return it.
      * Peek: Return the top element of the stack without deleting it.
      * isEmpty: Check if the stack is empty.
      * isFull: Check if the stack is full.

   ![Stack](https://miro.medium.com/max/1400/1*QMifqahZm4DGQ91GkOhu4g.webp)

4. **Queue** - a FIFO (First In First Out — the element placed at first can be accessed at first) structure which can be commonly found in many programming languages.
   * Queue operations:
      * Enqueue: Insert an element to the end of the queue.
      * Dequeue: Delete the element from the beginning of the queue.

   ![Queue](https://miro.medium.com/max/1400/1*K4-7c0lyUcSGRPmv3_9uqw.webp)

5. **Hash Table** - a data structure that stores values which have keys associated with each of them and supports lookup efficiently if we know the key associated with the value.
   * `h(k) = k % m`
   * A special function named as the hash function (h) is used to overcome the problem in direct addressing. In direct accessing, a value with key `k` is stored in the slot `k`. Using the hash function, we calculate the index of the table (slot) to which each value goes. The value calculated using the hash function for a given key is called the hash value which indicates the index of the table to which the value is mapped.
     * h: Hash function
     * k: Key of which the hash value should be determined
     * m: Size of the hash table (number of slots available). A prime value that is not close to an exact power of 2 is a good choice for m.

   ![Hash Table](https://miro.medium.com/max/1400/1*xOmBfzMxLLldy1ll4w7esg.webp)

6. **Tree** - a hierarchical structure where data is organized hierarchically and are linked together. This structure is different from a linked list whereas, in a linked list, items are linked in a linear order.
   * Binary Search Tree (BST) - a binary tree where data is organized in a hierarchical structure. This data structure stores values in sorted order.
   * Every node in a binary search tree comprises the following attributes:
      * key: The value stored in the node.
      * left: The pointer to the left child.
      * right: The pointer to the right child.
      * p: The pointer to the parent node.

   ![Tree](https://miro.medium.com/max/1400/1*TMn800emvMuqwY3AZpfwCg.webp)

7. **Heap** - a special case of a binary tree where the parent nodes are compared to their children with their values and are arranged accordingly.
   * Heaps can be of 2 types:
      * Min Heap — the key of the parent is less than or equal to those of its children. This is called the min-heap property. The root will contain the minimum value of the heap.
      * Max Heap — the key of the parent is greater than or equal to those of its children. This is called the max-heap property. The root will contain the maximum value of the heap.

   ![Heap](https://miro.medium.com/max/1400/1*BEq4aj8K7u4LbIaIEtHNmQ.webp)

8. **Graph** - consists of a finite set of vertices or nodes and a set of edges connecting these vertices.
   * The order of a graph is the number of vertices in the graph. The size of a graph is the number of edges in the graph.
   * Two nodes are said to be adjacent if they are connected to each other by the same edge.
   * **Directed Graphs** - a graph G is said to be a directed graph if all its edges have a direction indicating what is the start vertex and what is the end vertex.
   * **Undirected Graphs** - a graph G is said to be an undirected graph if all its edges have no direction. It can go in both ways between the two vertices.

   ![Graph](https://miro.medium.com/max/1400/1*bgRmFfnYXHYXSv1pbNea0A.webp)

## Big O

* O(1) - constant time
* O(N) - time increases linearly (like a for loop that iterates through each item in an array)
* O(N^2) - time increases exponentially (like a for loop nested in another for loop that iterates through each item in an array multiple times)

## Questions

1. What is 1 of the more important things you should consider when deciding which data structure is best suited to solve a particular problem?
   * The type of data being used
   * How is the data being stored
   * How much stored data will there be
2. How can we ensure that we’ll avoid an infinite recursive call stack?
   * A Base Case to exit the loop

Sources:
<https://towardsdatascience.com/8-common-data-structures-every-programmer-must-know-171acf6a1a42>
<https://triplebyte.com/blog/why-you-should-learn-big-o-and-stop-hacking-your-way-through-algorithms>
<https://triplebyte.com/blog/why-you-should-learn-big-o-and-stop-hacking-your-way-through-algorithms>
