# ideas6
Welcome to Ideas for computing - batch 6.



<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons Licence" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.

# 1. Icon grid on the left





# 2. Parallel composition

A GUI that composes elements in parallel.

# 3. Sideways computation

We cannot make cars go faster but we can add more cars to the road.

# 4. Flexible, mutable

# 5. Memory scan GUI

# 6. Data traversal is the program

Traversals are iterators

Prolog is a graph traversal program

Pagination of traversal



# 7. Fan out data structures, O notation

# 8. Can do a lot of the same thing per unit time

Roads, cars



# 9. Offline bulk data processing, logistics summarisation and social networks fan out

A social network has a massive fan out

Can we eliminate all round trips by analysis of all the data access patterns?

If you don't need the entire data set, you can page.

# 10. Separating static infrastructure, online infrastructure

# 11. Fixed buffer lang

# 11. Relocatability

# 12. Don't try model truth in your algebraic system

# 13. Lightweight stacks

# 14. Tail recursion and reusing stack

# 15. Memory ownership maps

# 16. Multiplexing over files

Warpstream optimises a Kafka stream for object storage.

# 17. Online batch processing

This is an extension of the parallel machine. Wait for 1 seconds of buffer to fill then process it with extreme throughput.

# 18. Slow interpreted, fast compiled

You can use a slow interpreted language to generate data cases for a fast compiled language.

# 19. Multiplex any work arrangement

Creating multiplexers should be easy

Concurrent multiplexers is easy, we can create a stack of them.

# 20. Logistics performance

Can move from one place to another, extremely fast.

Numbers, identities.

What's a traversal with counting?

# 21. How does a relational database relate to movement and logistics?

# 22. GPU accelerated web requests and redraw logic

It's an encoding.

```
order(order:1) user(user:1) = in-cart(order:1) | placed(order:1) | fulfilled(order:1) 
```

How many dimensions do we need?

```
dimensions that touch order:1
in-cart 0
placed 1
fulfilled 2
```



Multidimensional movement

How do you "read" a number that is an encoding? Its a traversal

counting, a distinct step to produce a result

a GUI screen with items, x and y

can nested for loops be replaced with addition?

calculus of a contribution of a coordinate to be "inside" another item visually, don't need nested loops or scenegraphs

can redraw expensive screens based on this calculus, pagination

# 23. The amount of work required to use or wrap an API

# 24. Type safety and the http middleware pattern



Async

# 25. Solving dining philosophers with multiplexing and state machine formulation

There is a link between multiplexing and parallelisation.

We generate all statelines, then identify which ones can run in parallel - those that are independent - and which need tests for locks or mutual exclusion.

```
fork_1
fork_2
fork_3
fork_4
philosopher_1_take_fork_1_philosopher_1_take_fork_2
philosopher_2_take_fork_2_philosopher_2_take_fork_3
philosopher_3_take_fork_3_philosopher_3_take_fork_4
philosopher_4_take_fork_4_philosopher_4_take_fork_1
```

Some of these rows refers to the same resource - so they require locks. We can insert a test() and condition variable.

```
```



Alternatively they can run on my multithreaded nonblocking runtime where the schedule is fixed and static and doesn't require locks. 





```
philosopher(philosopher:P) = take_fork(philosopher:P, fork:P take_fork(philosopher:P, direction:P+1%forks) | eat(philosopher:P) | put_fork(fork:abs(P-1)%forks) put_fork(fork:abs(P+1)%forks)
```



| fork | 1    | 2    | 3    | 4    |
| ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      |

# 26. Scaling is a fanout problem

# 27. Rearrangement Shop



# 28. Rearrangement or configuration for high performance kernels

A language that has two halves.

The slow part is python and runs at compile time and it generates an AST which is then compiled and turned into machine code. The slow part determines the configuration objects for the fast kernel.

# 29. Looking up behaviour of a position

If you have a message that is sent to 50 million people.

```
while num > 0:
	
```

# 30. Outcome catalogue







# 30. Multiplexing and parsing and postgres table storage

# 31. Network hop remover based on positioning

Travelling salesman.

# 32. Objects live in buffers

Java gets something right: objects are good for managing memory. And they're also identities.

"My" is a relative position.

```
movq [base+field], %rax
```

# 33. Toggle log

# 34. How to move something between two places efficiently?

In databases it would be updating the foreign key.

# 35. Lock mangers in databases

# 36. Logistics compiler

# 37. Strange structs

`cut` a context of data.

# 38. Evented assembly - Yielding until the next event is reached

This is a design for evented assembly paired with my multithreaded barrier runtime. This is a general event handling solution for high concurrency. Design goals:

* High throughput for coroutines on the same thread for decoupling code.
* High throughput between threads.
* How much space do we allocate to a coroutine? **It depends how parallel it is.**
* It handles observers.
* This is the object hierarchy: we have mailboxes for threads, there are facts and there are coroutine objects.
* Go language has moveable goroutines but we don't.
* The only things written to a coroutine's mailbox are events that interest it.
* A lot of the time, coroutines shall only be on one thread.
* Either the thread has a mailbox and the thread routes data in a mailbox to a particular coroutine or each coroutine can own a mailbox, it depends on your memory requirements.

```
fact-1
	coroutine-2
fact-2
	coroutine-1
	
thread-1
	runqueue-lower
	runqueue-higher
	coroutine-1
        mailbox-1
        mailbox-2
        mailbox-3
        mailbox-4
        mailbox-5
thread-2
	runqueue-lower
	runqueue-higher
	coroutine-1
        mailbox-1
        mailbox-2
        mailbox-3
        mailbox-4
        mailbox-5
thread-3
	runqueue-lower
	runqueue-higher
	coroutine-1
        mailbox-1
        mailbox-2
        mailbox-3
        mailbox-4
        mailbox-5
thread-4
	runqueue-lower
	runqueue-higher
	coroutine-1
        mailbox-1
        mailbox-2
        mailbox-3
        mailbox-4
        mailbox-5
thread-5
	runqueue-lower
	runqueue-higher
	coroutine-1
        mailbox-1
        mailbox-2
        mailbox-3
        mailbox-4
        mailbox-5
```

* Could we assign mailboxes to particular coroutines, for cross thread usage?
* Could we assign mailboxes to **facts**?

The runqueue for threads looks like this:

```
{0: [[1, 4, 7, 10, 13, 16, 19, 1, 4, 7, 10, 13, 16, 19]],
 1: [[2, 5, 8, 11, 14, 17, 0, 2, 5, 8, 11, 14, 17]],
 2: [[3, 6, 9, 12, 15, 18, 0, 3, 6, 9, 12, 15, 18]]}
```



In assembly, our state machine formulation might need to wait until an event fires occurs so that it can continue.



State location moves through the system as it moves between threads. The beautiful thing about this design is that it doesn't require centralised state.

```
state1 = state2 | state3
```

* When there is a yield we know the yield point based on the instruction pointer (**%rip**)

* Each coroutine has its local variables and state stored relative to **%rax**
* Local variables are always kept by a coroutine, they are local. But they are available to other coroutines on the same thread.
* Each thread **AND** coroutine has an output buffer called **higher** (**%rdi**) and input buffer called **lower** (**%rsi**) for double buffering which allows them to be thread safe when executed with the barrier runtime.
* You might want to broadcast the same data to multiple threads.
* [base_reg + index_reg*scale + displacement] is enough to get all the local variables
* `yield` places **%rip** into (**%rax**) to store the coroutine's position into memory. This pauses the coroutine. If the coroutine has its own stack, it also stores **%rsp** into **24(%rax)**.
* `activate` moves **(%rax)** the coroutine position into a register %r10 and **jmp *%r10** to jump **inside the coroutine to the resume point**
* `fire` indicates something is true, which may cause readiness for another coroutine. This can potentially cause multiple things to execute at the same time, based on parallelism and concurrency.
* There's an element of pattern matching here because facts are parametered.
* Fire will have to insert into other threads.
* For events that are parallelised we can do a replicated parallel (fork) which writes to multiple thread coroutines.
* The coroutine writes its data into **X(%rdi)** higher buffer that it wants to share with other coroutines. This shall be exchanged at the next synchronization event by the multithreaded barrier.
* The `fire` takes a fact, and some parameters and writes an **activation record** into triggered coroutine's mailbox (**higher**) input buffers, which is thread safe. And it adds that coroutine to the **higher** runqueue of that coroutine's thread.
* If the coroutine ALWAYS operates on the same thread, then it can reuse the same buffer and doesn't need to use `higher`.
* Does the firing thread or the receiving thread check if event critieria is met?
* Eager criteria checking or delayed criteria checking.
* **Yield** decides which coroutine to activate based on a runqueue.
* Each thread has its own runqueue which is double buffered.
* Streamlining coroutines - if two coroutines directly talk to eachother, we can always run them sequentially and share buffers and avoid data moving.
* The topology between coroutine is an API surface.

A fact can be represented by a sequence of numbers

Do we guarantee that after a fire and yield that the event was processed? Callbacks?

```
state1:
	fire state2 # my coroutine activation record is indicated in the fire request
	yield
state2:
	# my state is only read by me now
```

* A thread always writes to a mailbox of another thread and to the higher buffer, since this is thread safe.
* How do we link mailboxes associated with coroutines?
* Does a coroutine exist on all threads?
* One approach which is strange is that the same coroutine object exists at every thread's barrier superstep, so it's thread safe if it's a singleton coroutine. Its coroutine function is called with a different mailbox in its lower %rsi buffer. But this increases latency.
* I think the coroutine must be called repeatedly with each mailbox to serve requests to it.

```
fire:
	mailbox[mailbox_count++] = activation_record;
```

hash Join's for things that are moved?

```
state_1:
	# do something
	# do something
	yield # until state2
state2:
	# do something
	# do something
	yield # until state3
state3:
	# do something
	
```

Register clobbering is fine, all local variables come from memory.



```
while running:
	number = number + 1
	fire numberadded
	
	
# paralell-coroutine
numberadder1:
	movq 25(%rax), %r1
	addq $1, %r1
	movq 10(%rsi), %r2		# get the size
	movq %r1, (%rsi,%r2,)	# move the item to be read by the next coroutine
	movq %r1, 25(%rax)
	yield
	cmp $1, 20(%rax)
	jz numberadder1

# shared-register-coroutine
# a coroutine that sends to another coroutine on the same thread
# the source coroutine's local data is in %rdi and
numberadder1:
	movq 25(%rax), %r1
	addq $1, %r1
	yield
	cmp $1, 20(%rax)
	jz numberadder1
	
# this coroutine receives the data from the previous coroutine
numberadder2:
	movq 25(%rdi), %r1
	addq $1, %r1
	movq %r1, 25(%rdi)
	yield
	cmp $1, 20(%rax)
	jz numberadder1
	
# merged-coroutine
numberadder1:
	movq 25(%rax), %r1		# from coroutine-1
	addq $1, %r1			# from coroutine-1
	addq $1, %r1			# from coroutine-2
	yield
	cmp $1, 20(%rax)
	jz numberadder1

numberadder1()
numberadder2()
numberadder3()

```

```
numberadder1 | numberadder2 | numberadder3
```



Double buffering for source location and destination locations

Or register handoff.

Efficient sending data between assembly

Bulk Iterators

if you do it one at a time or all, does it make a difference to program semantics

local variables can be heap allocated

offsets

2d dimensional object mapping, a linear ordering where relative positions of heterogenous everything are arranged in memory.

just numbers

stack relationships, you poke the rsp on the stack for restore?



side: adding numbers to lots of numbers and see the shape of the coordinates it creates

"sametime lists"

# 39. Serverless with simple code generation

# 40. Language semantics and the lack of reuseability of things written in Rust or C++

# 41. Logistics of JSON data structures from APIs

# 42. API Engine

Handle all ingestion and logistics.

# 43. Optimisation in spare cycles

# 44. Position tree

Update position of sets of items

# 45. Programming against behaviours

# 46. Matrix translation fun GUI

# 47. Traversal lines with stacks on them 

# 48. Insert into an access pattern

# 49. Database engine traversals and logic and data flow and logistics and assembly number relationships

# 50. Inflection towards on a graph and matrix multiplication

# 51. Position and logistics is algebra

# 52. Logistics grid

Use SIMD and threads to search for location of items. Numbers can be subsets of eachother

```
If X == 1:
	it's in collection 1

if X == 2:
	it's in collection 1 and 2
```

```
samuel-squire	
cat				
phone			
```

Construct separate lists based on the number when scanning.

Moving subsets of groups efficiently for reading and writing.

# 53. Server event ingest

# 54. Business fanout

# 55. There's value in fast fanout

# 56. Membership in a collection: most frameworks are about "where" you arrange things

# 57. Define the semantics you want

# 58. Generate the output given a case, then infer the movements with a neural network?

# 59. Paralellism thoughts

* To fork and parallelise with low latency, you need a thread that is ready and spinning on an integer until it can continue. You also need a thread pool.
* The multithreaded barrier enables high throughput and requires no locks but there is a high latency on synchronization.
* Scale/fan out is interleaving and multiplexing.

# 60. Buffer filling parallelism

# 61. Alternating thread groups

# 62. Sideways

# 63. Latency and throughput



# 64. Need log - FIFO stack



# 65. Content addressed file systems and pointers

This would be amazing. Everything would be O(1) lookup time.

# 66. The Go Toolchain and A* and logistics

Is not building software a traversal? How do you know something works with what you have?



# 67. Preexecution

# 68. Traversing lots of data in parallel

# 69. Masking the future

What can chess teach us about this?

# 70. Language composition

# 71. The GUI is just data

# 72. How do you generalise a move

The kernel for example, things are moving around.

# 73. Tuples of thunderbird application

# 74. Runpatterns

can we change the Linux scheduler to run threads in a pattern?

# 75. Latency is a product of how much work you have to do

# 76. Number of state changes per second

# 77. Surf cloud

Create resources in clouds, with placeholder names. As-if

# 78. Business process shop

# 79. Designing a language with semantics , semantic editor

# 80. Compact and equivalent traversals, traversal graphs

Can a traversal be algebra and automatically deduced?, prexecution

# 81. Communication editor and placeholders



# 82. Maximum possible future

# 83. Number lines

Memory is billions of number lines. If you don't need to serialise a number line, to see it at a given position.

1... 100

1.. 100

Each number line is an identity. Each number is a position. K nearest neighbours.

If I have 4 number lines,

Couldn't we create a lookup table of combinations that sum to 100?

register programming, syscall for output

# 84. Organisational software

security

# 85. Chunk stacks

A browser is a chunk stack.

# 86. Software URL

handle versioning, migrations

# 87. Parallel updated layers

you can composite at the end

# 88. Expressions work the same in most languages

# 89. Immediate fire - communication is just memory

In my disruptor and nonblocking barrier, the latency to handling a request is as low as 66 nanoseconds up to a few hundred nanoseconds. 

If you want to interlock or send-and-reply, you're paying 66 nanoseconds each time.

To interlock, you set a memory location and then update a field.

```
struct Thread {
	int ready;
}

thread1:
mov $2, %rbx
mov $6, %rax
mov %rax, b(dest) 		
mov $1, (threads,%rbx)	# signal ready for consumption
						# other thread can see a in ~100 nanoseconds		
# can do things while other thread is doing things
loop:
cmp 


thread2:
wait:
cmp $1, threads(dest)
je receive
jmp wait
receive:
mov a(dest), %rax
add $1, %rax

mov %rax, a(dest)
mov $2, %rbx
mov $1, (threads,%rbx)		# send data back






```

```

```

safe to only write from one thread

# 90. Versions webpage

parallel lines

# 91. Semantics algebra

# 92. Multiplexing semantics and algebra

# 93. Synchronized turning and movement

How do you move multiple things simultaneously to get an effect?

# 94. Overlapping rectangles and the borrow checker

# 95. "Self" can be the local variables and the stack

# 96. N to N-1 many peers

```
```

# 97. Cheap iterators or passing data between coroutines

# 98. Placeholders for control flow mapped onto a grid - should do these things

# 99. Parallelisation and serialised resources

Route around resources.

```
Resource()
```

# 100. Signal animation

We can think of an object orientated program as lines (wires) connecting pieces and then signals being sent down wires. This is in effect a protocol.

# 101. Tail call optimisation generic AST pattern



# 102. Parsing is dispatch

# 103. Optional past window: structured interaction programming

Events, interact.

# 104. Numbers affecting numbers

C Compiler

# 105. Markup output: highlight and instantiate and connect

Structs in assembly are moves into 0x18(%rbp)



```
    buffers[x].count = buffer_size;                                                                                                                   
    5efb: 8b 85 14 fe ff ff     mov    -0x1ec(%rbp),%eax  # move x into %eax                                                                                       # sign extend
    5f01: 48 98                 cltq                                                                                                                  
    5f03: 48 c1 e0 04           shl    $0x4,%rax                                                                                                      
    5f07: 48 89 c2              mov    %rax,%rdx         # rax is shifted by 4 in both rax and rdx                                                                                             
    5f0a: 48 8b 85 00 ff ff ff  mov    -0x100(%rbp),%rax # overwrite rax with data from 0x100 (buffers)                                                                                            
    5f11: 48 01 c2              add    %rax,%rdx         # add data from %rax to shifted left %rdx                                                                                             
    5f14: 8b 85 8c fe ff ff     mov    -0x174(%rbp),%eax # move buffer_size into buffers[x].count                                                                                             
    5f1a: 89 02                 mov    %eax,(%rdx)
```



# 106. Lockdown GUI

# 107. Multiplexing CPU/Multiplexing IO
