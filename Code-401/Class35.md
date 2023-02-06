# Graphs

* A graph is a non-linear data structure that can be looked at as a collection of ***vertices*** (or ***nodes***) potentially connected by line segments named ***edges***. Here is some common terminology used when working with Graphs:
  1. Vertex - A vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
  2. Edge - An edge is a connection between two nodes.
  3. Neighbor - The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
  4. Degree - The degree of a vertex is the number of edges connected to that vertex.

## Directed vs Undirected

### Undirected Graphs

* An ***Undirected Graph*** is a graph where each edge is undirected or bi-directional. This means that the undirected graph does not move in any direction.
* For example, in the graph below, Node C is connected to Node A, Node E and Node B. There are no “directions” given to point to specific vertices. The connection is bi-directional.

![Undirected Graph](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/UndirectedGraph.PNG)

* The undirected graph we are looking at has 6 vertices and 7 undirected edges.
* Vertices/Nodes = `{a,b,c,d,e,f}`
* Edges = `{(a,c),(a,d),(b,c),(b,f),(c,e),(d,e),(e,f)}`

### Directed Graphs (Digraph)

* A ***Directed Graph*** also called a ***Digraph*** is a graph where every edge is directed.
* Unlike an undirected graph, a ***Digraph*** has direction. Each node is directed at another node with a specific requirement of what node should be referenced next.
* Compare the visual below with the undirected graph above. Can you see the difference? The ***Digraph*** has arrows pointing to specific nodes.

![DirectedGraph](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/DirectedGraph.PNG)

* The directed graph above has six vertices and eight directed edges
* Vertices = `{a,b,c,d,e,f}`
* Edges = `{(a,c),(b,c),(b,f),(c,e),(d,a),(d,e)(e,c)(e,f)}`

## Complete vs Connected vs Disconnected

* There are many different types of graphs. This depends on how connected the graphs are to other node/vertices.
* The three different types are completed, connected, and disconnected.

### Complete Graphs

* A complete graph is when all nodes are connected to all other nodes.

![CompleteGraph](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/CompleteGraph.PNG)

* Take a close look at each of the vertices in the graph above. Do you notice that each vertex is actually connected to every other node on the graph? That is what makes it a complete graph.

### Connected

* A connected graph is graph that has all of ***vertices***/***nodes*** have at least one edge.

![ConnectedGraph](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/ConnectedGraph.PNG)

* In the visual above, this looks a lot more than what you are used to seeing. If you look closely at the different vertices of the graph, you will see that each node is connected to at least one other node or vertices. A Tree is a form of a connected graph. We will talk more about that in a bit.

### Disconnected

* A disconnected graph is a graph where some vertices may not have edges.

![DisconnectedGraph](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/DisconnectedGraph.PNG)

* In the above visual, the disconnected graph shows that some nodes may not always be connected to other nodes or vertices of the graph. It is complelty possible to have standalone nodes or edges (also known as islands) in a graph data structure.

## Acyclic vs Cyclic

### Acyclic Graph

* An acyclic graph is a directed graph without cycles. A cycle is when a node can be traversed through and potentially end up back at itself. Here is an example of 3 acyclic graphs:

![ThreeAcyclicGraphs](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/threeAcyclic.png)

* A directed acyclic graph is also called a DAG. This can also be represented as what we know as a tree.

### Cyclic Graphs

* A Cyclic graph is a graph that has cycles. A cycle is defined as a path of a positive length that starts and ends at the same vertex. Here is an example of a two different cyclic graph:

![Acyclic](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/cyclic.PNG)

## Graph Representation

### Adjacency Matrix

* An Adjacency matrix is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix
* Each Row and column represents each vertex of the data structure. The elements of both the column and the row must add up to 1 if there is an edge that connects the two, or zero if there isn’t a connection. This is what an adjacency matrix looks like:

![AdjMatrix](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/AdjMatrix.PNG)

* A few things to note from the above:
  1. Vertex A connects to both Vertex D and Vertex C. To show this, we place a 1 in the position of `(a,c)` and `(a,d)`.
  2. We follow this same pattern for the other vertex’s and where they are connected.
  3. If there is not an edge/connection between the vertex’s, we represent this by placing a 0 in the appropriate point of the matrix.
* A ***sparse*** graph is when there are very few connections. A ***dense*** graph is when there are many connections
* Within an adjacency matrix, an undirected graph will always be symmetric. This is not the case for a directed graph.

### Adjacency List

* An adjacency list is the most common way to represent graphs. An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected. Adjacency lists make it easy to view if one vertices connects to another. This is what an Adjacency List looks like:

![Adjacency List](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/AdjList.PNG)

* Vertex A has an edge to both Vertex C and Vertex D. As a result, we will place both Vertex C and Vertex D in the adjacency list. Just from observation, we can see that we will only place the vertices that are connected in the list. If there is no connection between the vertices, they are not listed.
* Thinking about how we will implement this in code? Well, let’s look at what the visual is telling us.
  1. We can visually see that we are working with a collection of some sort. The visual is depicting a Linked List, but you could easily make it an array of arrays if you’d like.
  2. Each index or node (depending on the data structure you choose to represent the adjacency list) will be a vertex within the graph.
  3. Every time you ***add an edge***, you will find the appropriate vertices in the data structure and add it to the appropriate location.

## Traversals

### Breadth First

* In a breadth first traversal, you are starting at a specific vertex/node. This node must be specified when calling the `BreadthFirst()` method. The breadth first traversal of a graph is like that of a tree, with the exception that graphs can have cycles. Traversing a graph that has cycles will result in an infinite loop….this is bad. To prevent such behavior, we need to have some way to keep track of whether a vertex has been “visited” before. Upon each visit, we’ll add the previously-unvisited vertex to a `visited` set, so we know not to visit it again as traversal continues.
* As a refresher of what breadth first actually means here it is: Breadth first traversal is when you visit all the nodes that are closest to the root as possible. From there you traverse outwards, level by level, until you have visited all the vertices/nodes. Here is what the algorithm breadth first traversal looks like:
  1. `Enqueue` the declared start node into the Queue.
  2. Create a loop that will run while the node still has nodes present.
  3. `Dequeue` the first node from the queue.
  4. If the `Dequeue`‘d node has unvisited child nodes, add the unvisited children to `visited` set and insert them into the queue.

![BreadthFirst](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/BreadthFirst.PNG)

* The visual above shows the levels in which the nodes will be added to the queue. You can see that since the root node is A, it will look the nodes that are only 1 away from the root. This is C,E, & B.
* Next it will look at the nodes that are 2 away from the root, this is F, G, & D. It will follow this pattern until it reaches the end of the graph and all nodes have been visited.
* Look at the code below to take a closer look at what is actually happening. This is the code for a breadth first traversal:

  ```python
  ALGORITHM BreadthFirst(vertex)
      DECLARE nodes <-- new List()
      DECLARE breadth <-- new Queue()
      DECLARE visited <-- new Set()

      breadth.Enqueue(vertex)
      visited.Add(vertex)

      while (breadth is not empty)
          DECLARE front <-- breadth.Dequeue()
          nodes.Add(front)

          for each child in front.Children
              if(child is not visited)
                  visited.Add(child)
                  breadth.Enqueue(child)

      return nodes;
  ```

* Here is a breakdown of what is going on:
  1. We have declared that our starting node (or root) is going to be Node A.
  2. The first thing we want to do is `Enqueue` the root.
  3. We also need to add the root to the `visited` set.
  4. Next, we enter a while loop. We want this loop to keep running until there are no more nodes in our queue.
  5. Once we are in the while loop, we want to `Dequeue` the front node and then check to see if it has any children.
  6. If there are children of the node we are currently looking at, we want to add them to visited set. This will help us know that we have already seen that node before, and won’t accidently push us into an infinite loop if the graph was cyclic. In addition to tracking each child node as visited, we want to place any of its children that have not yet been visited into the queue.
  7. The process will complete until the queue is empty.
  8. Once the while loop breaks, we can then return the list of nodes. This list will contain, in order, all the nodes that were traversed.
* A few things to note about breadth first traversals:
  1. If there are any disconnected nodes (such as islands) with the graph data structure, they will not be traversed.
  2. Breadth first only outputs the nodes that are connected in some relation to the root that you pass in.

### Depth First

* In a depth first traversal, our approach is a bit different than the approach used for breadth first. While the breadth first traversal uses a Queue to visit all children at a given level, the depth first traversal uses a Stack to visit all children of a given subtree. (This differs from our approach to tree traversal, where we visit nodes via recursive calls. Recursive calls use a call stack internally.) The algorithm for a depth first traversal is as follows:
  1. `Push` the root node into the Stack and mark as visited.
  2. Start a while loop that runs as long as the stack is not empty.
  3. `Pop` the top node off of the stack and check its neighbors.
  4. If a neighbor hasn’t been visited, push it onto the stack and mark as visited.
  5. Repeat until the stack is empty.

![DepthFirst](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/Depth1.PNG)

* We start by adding our root Node (Node A) to the Stack and marking it as visited.
* Following the algorithm we described above, we want to initiate our loop and begin `Popping` Nodes off the Stack.
* We pop off our root Node and check its neighbors, as neither have been visited. We then push both Node B and Node D onto the Stack and mark them as visited.
* At this points, depending on the order in which Nodes B and D have been added as neighbors, we assume that Node B is the top Node ready to `Pop` off and be evaluated.
* We pop off Node B and check its neighbors: Node C, which has not been visited so we add it to the top of the Stack and mark as visited.
* As our Stack is not empty, we continue to `Pop` nodes from the top of our stack.
* Now that we have visited all the neighbors of one sub child, the top of our stack contains Node D, the other neighbor of our root node.
* From here, pop off Node D and check it’s neighbors to add them to our Stack.
* Again, depending on the order in which these Nodes were added as neighbors to Node D, we should check Nodes A, B, E, H, and F, and we should note that both Node A and Node B have been visited, leaving Nodes E, H, and F as nodes to be `Pushed` onto the Stack.
* With Node E sitting at the top of the Stack, we pop it off the Stack and check it’s neighbors. There is only one, Node D.
* Since Node D has already been visited, we can ignore it and `Pop` the next node off the Stack: Node H.
* We check the neighbors for Node H and notice that both Nodes D and F have previously been visited, so neither are added to the Stack.
* Finally we `Pop` off Node F, and again notice that both neighbors Node D and Node H have already been visited, so we don’t add anything to our Stack.
* We have now completed our traversal with all nodes read in Depth First Order!

## What I want to learn more about

* Practical uses.
