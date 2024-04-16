
### 1.Difference between a stack and a queue + real-life scenarios for when each are appropriate to use.

	Stack
   
   A _stack_ is a data structure in which objects are inserted and removed according to the last-in first-out (LIFO) principle. We can perform various operations on stacks, such as push and pop, which respect the LIFO principle. It is also a recursive data structure.

   A classic **real-life example** of a stack is the _plates stacked over one another_. The plate at the top is the first to be removed, i.e. the plate which has been placed at the bottommost position remains in the stack for the longest period of time.

   Some **CPUs** have their entire assembly language based on the concept of performing operations on registers that are stored in a **stack**. 

   The simplest application of a stack is to reverse a word. You push a given word to stack - letter by letter - and then pop letters from the stack. Another application is the "undo" mechanism in text editors; this operation is accomplished by keeping all text changes in a stack.

	Queue
 
   A _queue_ is a data structure in which objects are inserted and removed according to the first-in first-out (FIFO) principle. We can perform dequeue(deletion) and enqueue(insertion).
   The **difference** between stacks and queues is in **removing**. In a stack we remove the item the most recently added; in a queue, we remove the item the least recently added.

   One real-life example of queues is the literal queue of people at the supermarket let's say. It is an ordered list in which insertions are done at one end which is known as the rear and deletions are made from the other end known as the front. 

   One major/popular application of Queues is the Breadth-First Search algorithm.

So, the overall differences between Stacks and Queues are:
* Their working principle(LIFO for Stack and FIFO for Queue)
* their structure: Stack has only one end, queue has 2 ends(front and rear)
* because of the structure difference, there will also be a nr of pointers used difference: 1 for Stacks, 2 for Queues
* Visualization, why not :). A stack is visualized as a vertical collection, a queue is visualized as a horizontal one. 
* The application: Searching algorithms: DFS is implemented with a Stack, BFS is implemented with a Queue.


### 2.What is the difference between an array and a linked list? Provide advantages and disadvantages of each data structure. 

	Array

   An **array** is a data structure in which objects are stored at contiguous(one after the other) memory locations, accessible by an index. They are of fixed size. 
   An array is faster but not memory efficient, it's good to use when we know the number of object we want to store beforehand, and this number does not change. 
   So, _advantages_ of arrays: search time meaning constant search times, specifically O(1). This is actually the best possible run time complexity.
        _disadvantages_: bad memory management(reserving memory for future operations that may not occur), **slow** insertion/deletion times(for insertion, we have to shift all elements starting at the desired insertion index, one position to the right, then place our element) which implies a O(n) time. If we were to insert/delete ONLY at the end of the array, the time complexity would become O(1).

	Linked List
	
   A linked list is a data structure in which elements are stored in nodes, each node containing data and a refference(link) to the next node. It is dynamic in size. 
        _Advantages_: Dynamic sizing, efficient insertion/deletion(only requires changing to the links to the adjacent nodes), efficient memory usage(we only store as much elements as we need, adding more if needed as we go by).
        _Disadvantages_: Inefficient random access(we cannot access elements as in arrays, whichever we want whenever we want, by index, it requires traversing the entire list), extra memory overhead(require additional memory overhead to store the links between the nodes, which can be significant when dealing with large lists), more complex to implement. 

### 3.What is HTTP? How is it different from HTTPS?

   HTTP(HyperText Transfer Protocol) is a protocol designed to transfer information between network devices. A typical flow over HTTP involves a client making a request to a server, which then sends a response message. 
   Common HTTP **requests** include: GET(expects information back in return), POST(client is submitting information to the server). Requests also have _headers_ which contain information stored in key-value pairs. They contain core information, such as the browser that the client is using and what data is being requested.

   There's also the **response**, which the client receives from a server in answer to an HTTP request. These responses contain: status code, response headers, optional HTTP body. Also, status codes are 3-digit codes most often used to indicate whether an HTTP request has been successfully completed. They can represent success, information, redirection, client error, server error.

   On the other hand, HTTPS uses **SSL**  to encrypt normal HTTP requests and responses, making HTTPS far more secure than HTTP. Instead of a normal text containing information such as GET: url.., Host: ...., an attacker will see a bunch of random characters.

   SSL uses _public key cryptography_ to encrypt HTTP requests and responses. 


### 4.Can you give some examples of common HTTP response codes?

   The mighty 404 :), which we all know and represents _Not Found_, that is, the server cannot find the requested resource. Or another status code on the client error response, 400(Bad request), which means the server cannot process the request due to something that is perceived to be a client error.
   Succesful code: 200(OK). Depending on the HTTP method, the meaning may vary but let's say for a successful GET request, 200 would mean that the resource has been fetched and transmitted in the message body.
   Server side error codes: 500(Internal Server Error): The server encountered a situation it does not know how to handle.


### 5. What is the difference between authorization and authentication?

   Authentication is the process of verifying who a user is, while authorization is the process of verifying what they have access to.

   Authentication is done first, and then authorization is done after a successful authentication. 


### 6.How would you explain to a 5-year-old how the WWW works?

   Imagine you are out in the park, in a big playground. Each spot/area in that park is like a website. Now, when you want to play football you need to get to the football area, or if you want to play in the sand area, to build a sandcastle, you ask your friend to tell you where those areas are. That's like typing a website adress. Then,  your friend guides you to where the football/sand area is. That's like the internet sending you to the website you want to visit. So, the World Wide Web is like a giant playground where you can find all sorts of things to do, just by asking around and following directions.  


### 7. Staircase problem

```python
def Staircase(n):
  for i in range(n):
    for j in range(n):
      if i+j == n-1:
        print(" " * j + "#" * (n-j))

print(Staircase(4))

# i = 0, j = 0: no print
#      , j= 2 no print
#      , j = 3: we print 3 spaces(" " * j=3) and also one '#' symbol("#" * 1)
     
# i = 1, j = 0: no print
#      , j = 1: no print
#      , j = 2: print 2 spaces(" " * j=2) and also 2 '#' (because '#' * (4-2))
#thus, we find the formula for printing how many spaces and how many '#' symbols, which is " " * j + "#" * (n-j).

#and so on...
```


### 8. Text encryption problem

```python
def encryption(s):
    ss = s.replace(" ", "")
    L = len(ss)
    rows = int(math.floor(math.sqrt(L)))
    columns = int(math.ceil(math.sqrt(L)))
    output = ""
    for i in range(columns): #iterating over the columns
        k = i
        for j in range(k, L, columns): #iterate over each character, filling the grid
								       # filling the grid column by column
            output += ss[j]
        output += " "
    return output
```