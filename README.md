# ideas6
Welcome to Ideas for computing - batch 6.



<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons Licence" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.

# 1. Small Icon grid on the left

AWS console is very large and there are lots of panels and interfaces to all the different services in AWS. I would like a quick way to navigate every component.



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

`cut` a context of data which can go up or down a traversal, which is a struct in itself, like a reduce which is dynamic. They're compatible.

# 38. Evented assembly - Yielding efficiently until the next event is reached

If you think of the TCP protocol, HTTP or interacting particles in physics or actors or concurrency in programming of IO and the user, the disk, you can think of each "thing happening" as an event.

Given an event, I need to dispatch to an event handler, a bit like an event loop that a GUI program such as Win32 or programming language such as Nodejs would use.

This is a design for evented assembly paired with my multithreaded barrier runtime. This is a general event handling solution for high concurrency and parallelism. [Link to multithreaded barrier runtime](https://github.com/samsquire/assembly). Detailed assembly examples are further down. Design goals:

* High throughput, low latency for coroutines communicating on the same thread for decoupling code. The compiler can elide inserting movements and scheduler calls or yields when coroutines are on the same thread for efficiency and are binpacked next to eachother. Then it's basically a method call or inlining. 
* High throughput, low latency between threads when coroutines are running in parallel.
* Can fork coroutines cheaply.
* The multithreaded barrier is a "phaser" which means it runs a sequence of supersteps in lockstep (the pattern is visualised below) in a predictable and deterministic rhythm, which also provides thread safety or mutual exclusion. The first number is the thread the second number is the task number. Each thread has its own set of tasks, which can be different (8 threads × 8 tasks = 64 independent tasks) Notice how the thread numbers can be in any sequence and unpredictable but the task numbers are predictable and monotonically increasing before resetting and starting the pattern again. [Jump to go past the example](#after-task-sequence)

```
8 Arrived at task 0
5 Arrived at task 0
2 Arrived at task 0
6 Arrived at task 0
3 Arrived at task 0
4 Arrived at task 0
7 Arrived at task 0
0 Arrived at task 0
1 Arrived at task 0
9 Arrived at task 0
9 Arrived at task 1
3 Arrived at task 1
4 Arrived at task 1
8 Arrived at task 1
7 Arrived at task 1
5 Arrived at task 1
6 Arrived at task 1
1 Arrived at task 1
2 Arrived at task 1
0 Arrived at task 1
5 Arrived at task 2
6 Arrived at task 2
0 Arrived at task 2
1 Arrived at task 2
8 Arrived at task 2
7 Arrived at task 2
9 Arrived at task 2
2 Arrived at task 2
3 Arrived at task 2
4 Arrived at task 2
4 Arrived at task 3
7 Arrived at task 3
3 Arrived at task 3
9 Arrived at task 3
6 Arrived at task 3
8 Arrived at task 3
5 Arrived at task 3
1 Arrived at task 3
2 Arrived at task 3
0 Arrived at task 3
4 Arrived at task 4
8 Arrived at task 4
1 Arrived at task 4
5 Arrived at task 4
7 Arrived at task 4
6 Arrived at task 4
2 Arrived at task 4
9 Arrived at task 4
0 Arrived at task 4
3 Arrived at task 4
3 Arrived at task 5
5 Arrived at task 5
9 Arrived at task 5
6 Arrived at task 5
7 Arrived at task 5
8 Arrived at task 5
4 Arrived at task 5
0 Arrived at task 5
1 Arrived at task 5
2 Arrived at task 5
4 Arrived at task 6
2 Arrived at task 6
7 Arrived at task 6
6 Arrived at task 6
8 Arrived at task 6
5 Arrived at task 6
3 Arrived at task 6
9 Arrived at task 6
0 Arrived at task 6
1 Arrived at task 6
4 Arrived at task 7
9 Arrived at task 7
5 Arrived at task 7
7 Arrived at task 7
3 Arrived at task 7
6 Arrived at task 7
8 Arrived at task 7
2 Arrived at task 7
1 Arrived at task 7
0 Arrived at task 7
3 Arrived at task 8
5 Arrived at task 8
6 Arrived at task 8
2 Arrived at task 8
4 Arrived at task 8
7 Arrived at task 8
8 Arrived at task 8
1 Arrived at task 8
9 Arrived at task 8
0 Arrived at task 8
```

<a id="after-task-sequence"></a>

* When `task number == thread number`, there is nobody else running this particular instance of one of those 64 tasks, providing mutual exclusion in that thread.

* During this mutual exclusion phase, we can exchange the "higher" and "lower" buffer pointers and then coroutines can read from the "lower" buffer and everything they sent before in "higher" shall be transferred to another thread.
* How much space do we allocate to a coroutine? **It depends how parallel it is.**
* 
* This is the object hierarchy: we have mailboxes for threads, threads and runqueue.
* Go language has moveable goroutines but we don't.
* The only things written to a coroutine's mailbox are events that interest it.
* A lot of the time, coroutines shall only be on one thread.
* Either the thread has a mailbox and the thread routes data in a mailbox to a particular coroutine or each coroutine can own a mailbox, it depends on your memory requirements.

Here is the object structure:

```
thread-1
	inbox-2-higher
	inbox-3-higher
	inbox-4-higher
	inbox-5-higher
	runqueue
	coroutine-1
        mailbox-1-lower
        mailbox-2-lower
        mailbox-3-lower
        mailbox-4-lower
        mailbox-5-lower
thread-2
	inbox-1-higher
	inbox-3-higher
	inbox-4-higher
	inbox-5-higher
	runqueue
	coroutine-1
        mailbox-1-lower
        mailbox-2-lower
        mailbox-3-lower
        mailbox-4-lower
        mailbox-5-lower
thread-3
	inbox-1-higher
	inbox-2-higher
	inbox-4-higher
	inbox-5-higher
	event-mailbox
	runqueue
	coroutine-1
        mailbox-1-lower
        mailbox-2-lower
        mailbox-3-lower
        mailbox-4-lower
        mailbox-5-lower
thread-4
	inbox-1-higher
	inbox-2-higher
	inbox-3-higher
	inbox-5-higher
	runqueue
	coroutine-1
        mailbox-1-lower
        mailbox-2-lower
        mailbox-3-lower
        mailbox-4-lower
        mailbox-5-lower
thread-5
	inbox-1
	inbox-2
	inbox-3
	inbox-4
	runqueue
	coroutine-1
        mailbox-1-lower
        mailbox-2-lower
        mailbox-3-lower
        mailbox-4-lower
        mailbox-5-lower
```

* The runqueue for a thread is a FIFO queue. But all runqueues for all threads can be thought of as a grid where the leftmost column is executed in lockstep, column by column, left to right.

The runqueue for threads looks like this. I have enqueued 40 tasks, two batches of 20 for 3 threads. Notice the two empty slots of 0 in middle of thread 1 and thread 2, this is required for maintaining synchronization.

```
{0: [[1, 4, 7, 10, 13, 16, 19, 1, 4, 7, 10, 13, 16, 19]],
 1: [[2, 5, 8, 11, 14, 17, 0, 2, 5, 8, 11, 14, 17]],
 2: [[3, 6, 9, 12, 15, 18, 0, 3, 6, 9, 12, 15, 18]]}
```

Runqueue submission is an event that is sent and processed by a thread as usual. It doesn't need to be thread safe because the mailboxes are thread safe and only a thread enqueues to its own runqueue.





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
* `register` registers a position (label) with an event, which is a bit like a callback entry. Register sends the callback entry to every thread via that thread's mailbox. This is a bit like shift/reset
* When `fire` runs, it checks the callback entries in the local thread, it checks if the coroutine can run on the local thread where the fire happened. Alternatively, it submits a runqueue item for another thread or however many threads it needs to fork to.
* Fire can cause forking.
* `wait` puts a coroutine into a state where it is blocked until a registered state is reached.
* `fire` indicates something is true, which may cause readiness for another coroutine. This can potentially cause multiple things to execute at the same time, based on parallelism and concurrency.
* The stateline syntax restricts the level of parallelism and concurrency, where events can be handled where.
* Fire around. Wait masks.
  Effects/latches, register can create a stack.
* Fire depends on current state.
* There's an element of pattern matching here because facts are parametered.
* Fire will have to insert into other threads.
* For events that are parallelised we can do a replicated parallel (fork) which writes to multiple thread coroutines.
* The coroutine writes its data into **X(%rdi)** higher buffer that it wants to share with other coroutines. This shall be exchanged at the next synchronization event by the multithreaded barrier.
* The `fire` takes a fact, and some parameters and writes an **activation record** into triggered thread's mailbox (**higher**) input buffers, which is thread safe. And it adds that coroutine to the **higher** runqueue of that coroutine's thread.
* If the coroutine ALWAYS operates on the same thread, then it can reuse the same buffer and doesn't need to use `higher`.
* Does a coroutine live on a particular thread?
* Does the firing thread or the receiving thread check if event critieria is met?
* Eager criteria checking or delayed criteria checking.
* **Yield** decides which coroutine to activate based on a runqueue.
* Each thread has its own inbox to every other thread which is double buffered.
* Streamlining coroutines - if two coroutines directly talk to eachother, we can always run them sequentially and share buffers and avoid data moving.
* The topology between coroutine is an API surface.
* Movement sequences, permutations are different named states

A fact can be represented by a sequence of numbers

In assembly, our state machine formulation might need to wait until an event fires occurs so that it can continue.

Do we guarantee that after a fire and yield that the event was processed? Callbacks?

```
yield:
deactivate | schedule

fire:
check-activations-graph | send-starts | schedule

register:
insert-activation-record
```

effects, how is it similar to a promise?

(pos, state) tuple

state machine formulation is like a mixture of a stack and a sequence

```
x = new Promise(function () {

});
x.resolve(); # this is like "fire"


```

exceptions

```
exception-error | do-something | exception-error-final
exception-error | do-something | error | exception-error-final

```



```
print_number:

something | print-number | something | something
something | X | something | something
```

reminds me of method dispatch in self and inheritance

reactivate the past

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

Loop instances

Loop and write data, then run body of loop

```
state1:
	mov $10, %rdi # loop variables
	mov $1, (%rax)
	fork		# sends runqueue submission request to another thread mailbox
	
```



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

for sideways iteration through a collection (execution)

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

a* equivalent positions

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

how do you read a value that could be updated at any time? left-right concurrency control

two event streams that can be interleaved arbitrarily

```
set x y
publish x
// x cannot be read by this thread anymore

read x


```



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

# 108. Transparent functions

A function grouping can contain other function groupings. They're transparent white line diagrams.

 dynamic reconfiguration

# 109. Value grid

# 110. Tablegrid - loose association

value grid bullet pointed lists cross references 

# 111. Type Teeth mesh

Two or more types can intersect to form a cartesian product.

# 112. Lots of different serial tasks

What can a computer desktop environment provide that is useful to developers?

* defragmentation
* spell check
* data organisation
* indexing
* cross referencing
* simulation



# 113. Scope is powerful

Can be used for memory management

# 114. Language sequences

# 115. Sources and Sinks

# 116. Fast compositing

# 117. Message passing route to widget

# 118. "When" is important

# 119. Token boundary Mapping

If I generate a text stream of tokens and there are boundaries of the tokens, I can work out how to produce which piece efficiently! for efficient refresh logic.
generate schedules

token boundaries are spans

# 120. Endless HTML

# 121. Recording spans as a language feature and repathing

Find alternative journeys to get the same output.

# 122. Placeholder token boundary mapping

Generics

# 123. You can have compile time performance for what would be a runtime elegance: Rubyisms

Because at compile time you know the steps you need to take in the future.

# 124. An event happens in another thread

How do you react to an event that is happening in another thread, that you are interested in?

* You can check for it when it is time to handle it. This is a "during" relation. Scope, span.
* Thread safe way of checking for an event.



```
task (input_rb)
	input_rb.check
	
```

# 125. Channels have a scheduling cost

How do you pass data between coroutines efficiently?

```
coroutine_1:
emit <record>

coroutine_2:
consume <record>
```

You can inline the calls at the compiler level. For runtime coroutines

```
coroutine_1.dependents:
coroutine_2

coroutine_1:
mov $1, dest(%rdi)
yield

coroutine_2:
add $1, mine(%rdi)
yield

yield:
jmp coroutine_1.dependents[coroutine_1.curdependent + 1 % dependents.size]

```





# 126. Dense meaningful keywords

The sequence and combination of keywords should be enough to understand its meaning.

# 127. Movement agents

Model movement through assembly - units.

Indirection is address calculation, addition

# 128. LLM and next token prediction and Data flow

# 129. Directed constraints/requirements

On the way to fulfilling this goal, I want you to maintain these criterias.

# 130. Multithreaded QUIC server

# 131. Sametime directive

```
sametime(tcp-server cron-timer )
	tcp-server cron-timer
		x
					x
						
```

multiplexing coroutines

generate a line separated schedule and the computer works out how to arrange code to generate it.

```
```



# 132. Fast traversal of chunks

a browser is essentially this.

# 133. Semantics and ASTs everywhere

# 134. Solve the mutable code problem

how to upgrade systems

# 135. Automatic route decomposition into AST

Create a superobject with every piece of functionality in it, then extract its usages into subcomponents.

# 136. REST APIs are too low level

# 137. Traversal dispatch

A traversal is a O complexity problem.

# 138. Adaptive behaviour, thresholds

such as JIT compiler compilation initiation

# 139. The gridrel is the program's input

Grid rel is the idealised efficient execution of something.



# 140. Types are valuable things

Type inference tries to hide types, but types are useful, they're what you have!

Can use propositions and logical reasoning over types and traversals

```
after :wrt thing
```

if what you have is useful and what you can do with it, you can chain it together with something else like intellisense, the timeline and algorithm can be optimised with token boundary recording

# 141. A protocol event stream

QUIC is event driven

# 142. Protocols and movement through space, memory, control flow, traversals

a protocol can be a traversal pattern

what do you visit?

what is the semantics of Ocaml?



# 143. The feature is that you don't have to do anything

# 144. Realtime interruptibility

# 145. Timeslicing

Arrange a program based on time.

# 146. Must happen before

A line that is drawn in concurrent programs that things must happen before or after.

# 147. Causality and atomics

```
thread1:
1 while compare and swap
1 store data[X] = something
1 set Y = X

thread2:
2 while compare and swap
2 store data[X] = something
2 set Y = X

Can these two go on in any order?

2 while compare and swap
1 while compare and swap
2 store data[X] = something
1 store data[X] = something
2 set Y = X
1 set Y = X

If the first set Y = X happens after the second, Y goes backwards in time, but on the next write, X is incremented from X, so the data at data[X] is not overwritten, but a reader might take a while to read that occluded Y

1 while compare and swap
2 while compare and swap
2 store data[X] = something
1 store data[X] = something
```

# 148. System is an AST

# 149. Protocol adoption

We can adopt the memory protocol of MOSEI and cache coherency protocols as our cross-thread protocol.

# 150. Align two streams

READ events

WRITE eevents

align them

# 151. Bucketer

text based format for buckets of data that can be independently queried

# 152. The hard thing

With concurrency, is ordering?

it's sliding puzzles all over

# 153. Flow simulation/data shift

# 154. Multidimensional computing - semantics

there are interactions at different layers levels of the program that need to be wired up

these layers can be projected to 2d space

A* on a rubiks cube that rotates

logistics

hololocation - project path

rotate meaning



# 155. Stacks of behaviour

A cell that is a list of keywords that compose to cause a behaviour.

# 156. Concurrency Pegs

When you atomically set the value, you cause movement, you can have mutual pegs that spinlock.

# 157. All valid interactions

```
```

# 158. Move between

if X is inside A > B > C > D and then we want to move it somewhere?

kinematics rotations

# 159. Crystallalsis

You create a equivalent movement through logistics and then you have an efficient execution plan based on the least movements to the same places with A*. rotation is a loop?

A map, table, list are all placement patterns.



# 160. IT in a box

issue numbers for cross referencing

# 161. Talk about as if you're doing it

Talk about what needs to be done, where things need to go and what needs to happen in the future.

Linguistical?

variables

"talk about a thing"

traversal

where do words reside?

mutual sequences

(one -> two -> three -> four)

(a -> b -> c -> d)

traversal patterns, are they relations?

every traversal is valid



# 162. LLM to AST

# 163. Connect relationships of parts, assembly

# 164. Bindings/associations can be pointers or not

# 165. Fast dispatcher/traverser

# 166. Thoughts on Postgres query compilation

A tuple access is compiled and switch statements are generated.

# 167. The communication is inferred

# 168. Infer straight line control flow based on rules

# 169. Recording token boundaries: recording interpreted languages

How do you efficiently map token boundaries to elements for refresh logic?

Can we record an interpreter's actions and then compile it?

Can we arrange state machine formulation into a grid?

Can we determine memory frees from an interpreter and then compile those frees into the application.

need an accurate determination of state

scope is state

linking garbage collection frees to lines of code for free insertion

# 170. Aggressive parallel traversal

# 171. Hyper state machine

States live in different places and they have logistics to get between places.

parameters are in registers or memory locations prepared for a call.

# 172. Something as complicated as multithreaded program described at a high level

interactions are states, an interaction of these two boxes can cause an effect over there

default case - other side

set the context, the gap, then define the cases.

```
a b c = d e k
```

use the sigma symbol for enumeration

infer the minimum data for those cases to be representable, don't do it manually

behaviour is a traversal

rotations of data, and equivalencies, that's plurality

when a b c happen, do d e k

```
a
b
c

b
a
c



```

# 173. Scaling plan is a series of fixpoints

# 174. How do you traverse lots of things simultaneously?

If I've traversing two lists in parallel and there may be interesting links between the two sets, that's a join.

# 175. "As if" I moved it here

# 176. Virtual Execution

A trace of code. from code sourcecode.

# 177. "Mental Model" is a program/API

program against my mental model.

relationships are traversals



# 178. Useful general purpose transformations

# 179. Linked thing "auth"

# 180. Parallel movements

# 181. Iteration is just execution

TCP and control flow and iteration

a line to delineate locks and synchronization, barriers

```
  one two three four
	-----------------------------------
		do-something else
		            ------------------------
		                    other thing
```



# 182. Traversal is iteration

# 183. Code Animation as pixels

# 184. Token boundaries and canvases

for efficent reexecution, immediate mode

# 185. A database that is not network reachable but storage reachable

# 186. Type Traversal Fingerprint

# 187. Traversing fast

It's limited by rate of instruction execution.

# 188. Semantic equivalence

rust and C

# 189. Adaptive latency to throughput

What's the fastest way for a GUI to react to action in the background?

# 190. Everything is a traversal

# 191. Lambdas are named events

# 192. Equivalent slot - visual understanding of slotting

# 193. Lifetimes, scope, ownership, and OOP

Explicit lifetimes.

# 194. Monads bind takes a function that accepts the wrapped item  that returns a monad

```
```

# 195. Traversal types and algebra inferred from output code

# 196. GUI leaf detection traversal

What is the minimum traversal to get the data ready for the screen?

# 197. Behaviour stacks

```
```

a behaviour is a series of events, in order

# 197. Why a single threaded program need reference counting

# 198. Code Reachability

# 199. Parallel lines and whilst

# 200. Want spec from any point

Import behaviours.

# 201. Parallel line GUI - Async System Surface

Can issue multiple requests to GUI for rendering, network or storage.

sharding framework Tuples of options.

NVMe storage, async IO, 

# 202. Overlapping in multiple directions, lifetimes

lifetimes overlap in typical programs

# 203. Stack item is a context

# 204. Label is a closure

# 205. State space package manager with standard cycle

# 206. Arrow lang

Direction can be swapped but meaning and semantics stays the same.

```
executor <- future
future -> waker
```

the order of the words decides the direction the arrow decides the call direction

# 207. Simplification of async

Callbacks interfere with understandability of data flow.

Rust saving a waker is like a flag.

```
			set_waker -> context
future ->
	^							<-- executor
	|__________waker ---------->				
					
```

# 208. Tree async data structure sharding framework visualisation: Aync units

"Rectangular queued Block" units

# 209. Embedded web system language

Every data structure has GUI component associated.

# 210. Execution tracing Back to present, control flow loop/cycle

Specify everything in relationship to other things on the path to repeating a cycle.

# 211. Graphical state management as token stream

# 212. Community Idea: Infographic home

Generate canvases/image files from interesting data.

# 213. Flags between threads

Just use an atomic instruction and double buffering and a mailbox for each thread to thread pair. RCU

# 214. Representing semantics of code

A query engine has useful properties that would be useful for a typical process. How to represent equivalence.

# 215. 

# 216. Comments in the sourcecode are the output, REPL as comments

# 217. You don't need a base case: Properties on sets

# 218. Accelerated lazy coroutines and lazy browsers: TLA + Incremental parsing + compilation

With a 33MB `dot` file, this program is very slow.

```
dot -Tsvg -o ringbuffer-tla/spec.svg ringbuffer-tla/spec.dot
```

Typesetting a big graph, is slow. Can we do it incrementally?

Facts look like method calls

# 219. My problem with scheme is nonlinear traversal

# 220. Monad generation

Auomatically infer monads based on facts ("vary operator")

one of my PL ideas is to just allow direct modification of sequences and infer the monad

Monad applicators, transformers in haskell are just a way of modifying traversal order (control flow) of your code in relation to other functions

```
sampl edit <type name> 
```

then a text editor comes up
it has in it

```
original-call
```

and
you modify it to

```
begin-span-call
original-call
end-span-call
```



# 221. Tree of parallel children and message passing

Efficient handover.

# 221. Parallel sequences that are synchronized or out of synchronization

Direct I/O, sequences



# 221. Drawing backends - is iteration the bottleneck? Latency? Refresh?

# 222. Bucket cloud

We'll scale you up to a bucket automatically.

# 223. Aligned iterators

This is wonderful idea, an iterator is a sequence and they can run in parallel, and they need or not be aligned.

Sum types.

Handover, efficient.

Structured interaction proramming.

# 224. A system that supports drastic changes while running

# 225. Common AST

# 226. Behaviour cycles, virtual processes, "bite command"

Interleaving of behaviour cycles

behaviour cycles correspond with lifetimes

an event stream goes to a virtual process, sync and resync ("bite")

compilation is a static event stream

alignment

joins

fabric - what you basing on, linear memory, function application etc

the decision generation can be slow

ticker units - synchronize with

# 227. Public AST

# 228. Proportionate

# 229. Pay people to define behaviours/Pay people to interact

# 230. 

# 231. 

# 232. Persistent actor REPL, not a nodal editor, not a notebook

# 233. Delegation interception, dispatch is the hard problem

Animate data rather than control flow State machine formulation as asserting fact movements

# 234. Semantic AST and fused behaviour

# 235. Placeholder layouting & algebra

You're always describing algebraic layouts of formulas and time, in a bounded collection or not.

Algorithms are just ordered algebra.

# 236. Parsing is a rule encoding?

recursive parsing, for ASTs too and the AST is recursively parsed, that's a fixpoint! 

could this be the behavioural fusion?

detect recursive loop sequences in the AST, where the fixpoint grows monotonically

get types that depend on characteristics of data for free

AST is an input to the parser and can replace any part.

lexical scope

garbage-collector, events, arguments

s-expressions as types

```
(https-server (http-server (tcp-server)))
```

beautiful

assembly programming, meta language

sets of tokens, context

substititution?

parsing collects into a tree structure, how to parse a tree and decide on subsumption?

```
parent = child | child2 | child3
child < subchild1
child < subchild2
```

Where to subsume up to?

And if you want to skip wrapped items, equivalence?

# 237. Immediate mode GUI to retained mode inferences

# 238. Properties, over time

# 239. Streams that meet in the middle

An iterator that is paginated.

# 240. Show cycling on the screen!

need to implement TLA state space generation

# 241. GUI updates is term rewriting

# 242. "Parellize" command cycler

 # 243. A new behaviour is the synthesis of new types and events

What's an invariant?

# 244. Explicit closures

It's a function call with the environment.

# 245. Numeric blocks

# 246. Parsing application state

# 247. Copy pastable prologues

# 248. Parse application state

# 249. Engine all the thing, it's not a framework

multithreading data scaling

# 250. Enrichment, crossinvariants, masking

cross invariants where each behaviour maintains properties, interleaving is how behaviour is maintained with regard to other objects.

# 251. Billion scheduling

O notation taken literally.

# 252. Instruction counting

# 253. Try to get toward something

scheduling, slots

# 254. High level Kubernetes-like

Depend on properties.

# 255. Rope data structure and standard iterators

# 256. Autoiterator

State machine formulation can handle iteration behind the scenes, and accelerated traversal.

# 257. State machine formulation tells where to put the code

You "depend" by creating a reference!

# 258. A deeply nested data structure to English

# 259. Every program is a compiler, prolog

# 260. Call tracing

# 261. Iterators are trees

# 262. You need to decide on the steps

state machine formulation knows what you need to define for the behaviour to be complete.

# 263. Multiplexing defined with state machine formulation

# 264. Value Grid standard library

```
date time file http-get http-post 
socket dns ip-address 
```

Time and date could be extremely powerful primitives for coroutines.

Read Compile Execute (RECLoop) prepare AST and process it for compilation, automatic thread safety

scheduling algorithm - interleave events

event grids

wait soak, wait event, join

iteration/relations

event sequencing combined with imperative part

mailboxes, events

```
stream
	t = datetime.now()
	while True:
		yield t + timedelta(seconds=1)
```

thread safety and mutual exclusion and execution

barrier runtime?

dining philosophers

handles for threads



# 265. Unscheduled time is latency

and direct adjacency is super low latency

# 266. Text based editor, ropes for GUIs

Extremely efficient recalculation

arbitrary insert between, wrapping and other interactions that are efficient.

# 267. Dancing future state equivalency

Graph exploration



# 268. Software browser II

URL configurs everything.

# 269. One giant state space

Type check the entire state space. And it is verified.

# 270. Community computer

Don't break anything but you can add behaviours to it.



# 271. Memory block region mapper and Memory grid

Memory layout is a protocol.

hierarchy of memory managers

the article on object orientated programming being pitfalls and the visualisation of the cache



# 272. Combining the skills of multiple programmers

# 273. Split keys asdf, hjkl, relative, absolute

# 274. Signal travelling from inside a box out the box

ISR routines, contexts, lifetimes,

Signal send from inside a box

# 275. Tree box programming

contexts that transmit from boxes

 # 276. Keepwith, try, invariant maker

minimize, maximise, autofit

# 277. Useful register algorithms

Assembly join algorithm?

# 278. Static ordered regions of data is easy to process

serialization is branching

# 279. Regrouping, reparenting a line stream

This is the behaviour of the pipeline:

```
```

I want to customise the pipeline.

# 280. Delegating is cross boxes, it's adjacency

# 281. Branchless programming and traversal patterns

# 282. Iterator of types

Control flow regions are types?

# 283. OOP is slow but easy to understand, can we map OOP to ECS?

# 284. Async is just a message

map function:

```
divide list in to chunks
send chunk to thread
send work function to thread
thread executes work function
thread send result back to originating thread
wait for all replies, merge
```

this formulation can be processed for dependencies to see what can run, topological sort

flatmap parallel

```
```

event wait type soak, where to branch to in the future

state machine formulation for microop definition, need to specify what events stack and don't stack

```
map = thread(start) divide(list, N, chunks[]) | send(chunks, threads) send(function, threads) | execute(function, chunk, result) | wait(start, threads, result) send(threads, result, start)  ) 
```

synchronous programming is a event soak state 

# 285. Eventually consistent parallelism that scales reads and writes

If you add different numbers to the same number in different threads, you're getting 12 reactions for the price of 1.

Interpret the output?

That's a vector.

Musical sequences? Patterns?

Tree relationships

how to represent tree relationship with points on a grid?

sort on the client

# 286. Programs are slow due to branching and OOP

# 287. Traverse states, numbers changing

A value's position is a number in memory.

```
a = 6
b = a + 7

# a moves from the memory of a to the location of b
```



# 288. Lots of time in a day

# 289. Infer the rotations in memory

# 290. Escape context layering

# 291. App Images

# 292. Path as-is

What are all the paths to this line of code?

# 293. Causality to state

An AST simulaneously describes steps and what should go on.

where everything is



# 294. Interaction visualiser with placeholders

# 295. The microops of parallel map AST

# 296. Understanding how Java does the async

The runtime pauses the current "thread" which is not a function but an instruction stream.



# 297. Hyper relation

Traversals of traversals. Position of a piece of data in global space and in traversal space.

Global identity movement

# 298. This happens, then this happens

AST, the computer works out how to efficiently schedule it. (where to add the change) Connect the paths.

Parallel map implementation. Microops

Traversals

# 299. Graph properties

The graph is the properties of the system, not the system itself.

# 300. Transpose YAML

Refer to YAML blocks inline like this and it unpacks.

```
block1 | block2 | block3
```



# 301. Types and state

# 302. Browser that actually a server

# 303. Parser puts down

A loop in a database, is on a stack. Stacks get in the way of compositional code.

Intuition about btrees. An if statement tells you where you go.

# 304. Intermediate representation everywhere - every function is an intermediate representation stream that can be bucketed and then scheduled

Time is a ticker. File systems and files are streams.

```
while True:
	yield time.now()

```



# 305. Select memory locations for traversal

# 306. Pointers as folders

# 307. Write a program that saturates network, disk, threads

# 308. Types in C are just numerics

# 309. Using a hashmap as basic unit for message sending

Can hash set permutations to make set publish a constant time thing.

compile out unused requirements

# 310. Dispatch an object to multiple possible receivers

loop and OR

# 311. Object locality

# 312. Shift the position of the future

In C and assembly, you feel the effects of it and the app crashes.

Future shapes, state exploration

# 313. Presentable surface: unerstandable programming

A large codebase is difficult and opaque to understand, but there are stories which are easy to understand.

# 314. trying to get the heap usage of a program, is manual string parsing of /proc/self/maps

# 315. Assembly programming, what should happen

Just like that.

register allocation and imaginary registers

sync with (sides)

what's very convenient to write, and let the computer fill the details in

create a stack explicitly

margin represents the context?

# 316. JSON B-tree and layered trees

# 317. Shortest path scheduling

traversals

# 318. Expertise match, requirements

say all my skills, representations

# 319. Representations are work

# 320. Layers can be useful

# 321. Name protocol

Protocol for moving about names

# 322. Event handling protocol

Binary protocol. Generate the sequence from any program, learn the sequence of types.

Can use OCaml or Haskell!

Turing completeness and handling of states, scenarios.

You get the advantage of proramming language parsing for free.

Driver callflow.

websockets, http, QUIC, 

it's a standard data flow API.

How to get any programming language to control something?

Efficiency?

Protocol for protocols.

rigid part is the runtime

dream API

async

binary AST

# 323. Parallel Log eventual consistency

You can look at the last committed log for other threads.

```
thread-1 log | VAL VAL
thread-2 log | VAL VAL VAL
thread-3 log | VAL VAL
thread-4 log | VAL VAL

Eventual consistency, no writes are lost
Are you trying to accelerate writes to the same field?
```



thunk, do processing for 1 second, check for marker

bucket scheduling

how do drivers get written?, timing

# 324. You're the storage

# 325. State space exploration of eventual consistent system

# 326. People programmable systems

just act, and the computer works it out, ad hoc

# 327. Iterator database

Btree backed iterators

# 328. Stop the world rewrite

explicit call when details change.

call a function to change the type of something



# 329. Static types makes sense

# 330. Infer the redraw with boundary analysis

# 331. Thunk pooling/persistent thunks

relationships between invocations

windowing relationships



# 332. Customer self hosts and we poll them

No high SLA requirements

Must not Go down.

# 333. File system object for files

fast archive

mount a file system and local loopback file system?

# 334. Compiler abstract tokens

The C parser is generating meaningful tokens from the lexical context.

# 335. The line between caller, callee, 

wrapping values, pratt parser, replacement

have to make a decision that is flexible for the future

# 336. Performance templates

# 337. Multiplication of "things" and algebra for their placement

traversal over those algebraic things, btree for position indexing

# 338. Term rewriting and TLC

# 339. Low latency Thread pool and efficiency

In general, the more writers or more threads that you need to be thread safe between the more latency.

If there's one thread handling IO and multibarrier thread pool. The barrier has 2 threads in each pair.

If we want to submit a different piece of work from multiple threads.

1 io thread, 5×2 barrier threads.

external thread ingest can only be from one thread to one thread, to the barrier.

io thread 

# 340. Inspection samples for codebase

Like a Python notebook for an end-to-end scenario for planning.

# 341. Memcpy can move an object of any size

Sequence in memory, rectangles. bin packing

# 342. GUI text named panels

Lots of useful serialisations for different scenarios. All text based. Like typora tree view on the left.

# 343. Data structures visit sequences

# 344. Indexed iterators

can a btree be tied to a loop?

# 345. Tree/Graph paginator

# 346. Layers of expertise

state machine formulation

# 357. Meaningfulness direction

it just keeps being meaningful

# 358. Movement through space

Programming, logistics around control flow.

# 359. Bidirectional term rewriting

pointers, unions

# 360. Efficient term rewriting - just use memory as a state machine

# 361. Types are two-value tuples, but traversals can be any length

# 362. Term rewriting with regard to time

the situation changes depending on what you're doing, different orderings or collections of objects or directions

API baskets and relationships



```
epoll.register
	fds that need to be subscribed
epoll.wait
```

unification?

transforming API baskets, contextual transformations

program from one basket to another

refactoring?

# 363. Event ordering

In memory, traversal patterns

# 364. Rewrite recursive function as iterative function

pratt parser

click the visitor order and the loop is generated, buckets with traversals inside?

loop maker

# 365. Minimum cost equivalence, rule traversal

Generics is an example.

# 366. Movement through static thunks, useful groupings of API calls

Grains of sand

# 367. Token sequences and change range detection, boundarise

# 368. Pattern database (table of named colourful patterns) that can be arranged and combined into layers

a useful collection of words in IDE, like APL

# 369. State machine formulation and loops unfolded

We never return to an old position, so we can always memory "free".

# 370. "Useful" tool

# 371. APIs aren't data structures

An API or request-response is not a datastructure.

# 372. Context search

OR AND AND search when you phone something and do a query for relevant cases.

# 373. Additive programming

# 374. Behavioural Spec that isn't tied to a language



# 375. When do you pop return?

That's when you can free.

# 376. Layered community cloud

# 377. How many operations can you do in parallel, buffers



# 378. Blog post sequence generator

# 379. Architecture schematics

directory structure is an architecture

# 390. Compile database query to machine code

# 391. Boxes that are alive

# 392. Behaviour tokens

# 393. Virtual reply

Host content, then user merges it together for reply chain.

# 394. Page bulk query



# 395. Visitor pattern and sequences you can resynchronize

# 396. Valid emission sequences

Rust, borrow checker

# 397. Goto isn't bad if you have a type too

# 498. Variables and method calls

# 599. Sequence To Monad

holes you fill, polymorphism

# 600. Movement in constant time

Lookup is O(1)

# 601. Notational work

Semantics, work

model the machine's abilities, O notation

# 602. A program that is an event dispatcher with limited runtime

We can host it with low latency and low effort, it doesn't necessarily need to be turing complete

# 603. Contiguous regions of memory

My contiguous hashmap relies on contiguousity for cheap memcpy, using array accessor syntax.

You can grow in 4 directions

```
block-1 1 GB region
block-2 1 GB Region
block-3 1 GB region


```

Freeing memory

relationships between stacks, contiguity

file systems store things in blocks

binary serialization

btrees

we can add pointers together, dereferencing

navigation?

a collection object, state machine formulation

growable collections

pretty much all data structures rely on contiguity

windows of TCP

when is a buffer not needed anymore?

# 604. Movement patterns

fire in a grid

# 605. Interaction sequences

A file with the merging of two sequences.

# 606. Control flow hash

put a log comment and the log output picks it up

# 607. Barrier star

Low latency replication between pairs. Forking cheaply.

Like a register

```
a1 -> a2 is fast
a1 -> b1 is slow
a2 -> b1 is slow
```

Map



```
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
*2
```

start thread send

```
[[1, 2], 3, 4, 5, 6, 7, 8, 9 , 10]

```

reduce can happen in the fast pair

# 608. Valuable conventions

# 609. Backward forward reference struct definition format

For thread objects configuration

# 610. Concurrency intermediate representation

# 611. Arbitrary sequence movement

[ a, b , c , d] these things refer to different things, i might want to pop this collection and overlay it to the original

# 612. Layers of intermediate representations

# 613. Mailbox data structure

```
group-1
	thread-1
		task-1
			mailbox-1-me
			mailbox-2-friend
			mailbox-3-external
		task-2
			mailbox-1-friend
			mailbox-2-me
			mailbox-3-external
		task-3
	thread-2
		task-1
			mailbox-1-friend
			mailbox-2-external
			mailbox-3-external
		task-2
		task-3
group-2
	thread-3
		task-1
			
		task-2
		task-3
	thread-4
group-3
	thread-5
	thread-6
```

# 614. Physical objects we move around (division etc)

# 615. IR mappings, algebra, variables

# 616. Graph pagination with output format

# 617. Query Intermediate representations

A GUI that you can make IR match, like VIM and query a GUI for file and line number and column efficiently

# 618. Programs are train circuits

movement sequences between states

# 619.  Moving queue FIFO/LIFO semantics and algebra and movement and concurrency and parallelism

# 620. 2 way Ownership

```
thread-1
	owns thread-2-mailbox-1
thread 2
	owns thread-1-mailbox-2
```

# 621. Apply mutual exclusion property  to range

intermediate representation for exclusion, locks then postprocessed as train tracks. 

# 622. Rotate to face, match up

channel ends, stacks

# 623. Run in context (in a loop or out of a loop), rotating contexts

# 624. Cache lvalues

# 625. Head toward state space which is your desired scenario

# 626. Assignments of mailboxes, then transformation to swapped mailboxes, index movements	

# 627. Can only be in one position (set) linear types, affine types

# 628. You must put down what you overwrite, three valued assignment

# 629. Swap API

# 630. Movement visualiser

Just set the position of everything and the next position and watch everything swap.

# 631. Problems with the star barrier

In the star barrier, there are two phases: a synchronized phase that only executes in one thread of the group and another phase that every group member executes simultaneously.

The mailbox higher/lower swapper happens in the synchronized phase.

Sending and receiving happens in both phases.

```
task-1 process messages sent to task-1 and swap

```



```
group-1
	thread-1
		task-1
		task-2
	thread-2
		task-1
		task-2
group-2
	thread-3
		task-1
		task-2
	thread-4
		task-1
		task-2
```





```
group-1
	thread-1
		mailbox-2
	thread-2
		mailbox-1

mailbox-2 lower = mailbox-1 higher

```

When my thread wants to exchange with another barrier pair, I am on task "t". The other barrier could be on any 	

# 632. Grow rectangles

Nested rectangles that grow up or down or left or right

# 633. Visit lists

These are a data structure, an intermediate representation for visiting. They can be used for optimisation.

# 634. Behaviour visitation

# 635. TCP/IP functions

# 636. Line up processes/operations and then apply functions across them, allocators, reorderes

processes visitation ordering

you're specifying the state of everything everywhere and the IR optimises it to something efficiently executable.

# 637. This mutual exclusion pattern



| thread 1 | thread 2 | thread-3 | thread-4 |
| -------- | -------- | -------- | -------- |
| x        | x        | x        | x        |
|          | x        |          |          |
|          | x        |          |          |
|          | x        |          |          |

# 638. Layered IR, IR all the way up

# 639. Traversal equivalents

# 640. Server software browser

# 641. The system can be in any state

# 642. Directioned traversal

direction of control flow between threads or machines

understandability and directions, orders, sequences

# 643. Scheduler

different systems do different things

# 644. Relational event time

Join time, represents a divergence.

# 645. Minimum spanning trees of event sequencing

# 646. Stamp programming

the computer can do this much work in a stamp, time epoch.

# 647. Terms allocation, and terms are processes, and states

each variable is a process. this is inspired by types.



# 648. Community idea: Add behaviour to the stack

# 649. Parsing is dispatch and parsing parallelism

We know the next state based on current state.

```
init1 | init2 | init3
one | two | three
```

Combine operator

# 650. Protocol definition and "this happens there"

# 651. A program that runs to completion, high probability it will work

# 652. Manual memory management is easier without event loops

# 653. Play audio button, play a behaviour

# 654. Implementing a large interface is hard in every language because of invariants

# 655. "Keep this running"

Ask a company to keep this running.

serverless, upload AST of program

# 656. Learn the state machine through events

 # 657. Visitation

# 658. Invertation programs

Write an inefficient base run program and the interacting pieces are inferred and optimised.

# 659. Outside facing programs

If the program works out what IO to do.

They have behaviour.

Behaviour is maintained if all the outside calls work.

# 660. Runtime to static time

Do you what you want inefficiently and it optimises.

# 671. Output data movement positioning

Run a program to generate the new outputs given the inputs. It tracks movements of every piece of data and operations that went against it, a path of its flow. The flow can be optimised.

# 672. Shade security

shading things colouring in

# 673. Event handlers serialised is codegen

# 674. Hyperreactor

# 675. Extract from loop, actor, coroutine or run a loop

Server code that loops over every item or an actor that interacts with the outside world

# 676. Sequence to type monad

call order to type that implements that call order

# 677. AST

# 678. Output tokens

# 679. Session log

# 680. Direction operator

Methods call eachother in either direction

# 681. Arguments are referenceable tables

# 682. Thunks as patches

# 692. Algebraic position language, terms

related to terms are variables, movement between positions, affine, linear

# 693. Event grouping, loop detection between events (sequences +1)

# 693. Generate mailboxes, invariants creation and algebraic assignment

# 694. Slider invariants data structure

joins?

# 695. Parser token causality

printf cause tracking, for recalculation.

# 696. SIMD movement

# 697. Simple language and causality of movement

Like C or python but analysed for change tracking

# 698. Parallel async

```
any {
	await something
	await something2
	await something3
}
```

# 699. State space exploration with multiple processes

Fix it for 2. pairs that depend on different variables.

What are the rules for safety?

```
thread-1								thread 2
checking available == 0			checking available == 1
	write available = 1				write available = 0
	
```

or for multiple workers

```
thread-1							thread-2
	my.arrived++						my.arrived++
	if other.arrived == my.arrived:		if other.arrived == my.arrived:
		do_something						do_something
```



# 700. Inferring data schema based on behaviour

# 701. Framed Protocol tokens

```
http-header
header
header
body
```



How do we run "msquic" with the multithreaded barrier?



A coroutine is asleep while waiting for wakeup.

```
all_queries = generate_all_queries()
pageserver.send(all_queries)

pageserver.on "resultset" =>


```

Process tree, what take execution context

```
[_] processes
	[+] request
        [+] account-name
        [+] recent
        [+] data-view
        [+] 
```

A protocol 

A layout inside a container

```
{
	
}
```

# 702. Event buckets "thunks"

Stateful containers of events

Like tcp connections or processes

types are matched on, a bit like IR

types are system state that is matched on

# 703. Scale to multithread when needed

# 704. Interleaved request-responses for performance

buckets

temporary buckets collects/sampled that are serviced periodically

# 705. ASTs for work

# 706. Control flow is an event sequence and so is the data

# 707. The request budget (100ms) and stamping

# 708. Types of app scaling

# 709. Sorting buckets and scheduling? Optaplanner

# 710. Protocol segmentation

the topology of the protocol defines what can be grouped into a batch for batch processing

concurrency scenarios

causality is maintained even in concurrency

```
1 -> 2: y
2 -> 3: x
3 -> 1: b
```



# 711. Memory is a topology, thunk spaces: fixed memory pools

# 712. State machine formulation and Parsing directions

# 713. Complexity is dispatch

# 714. A layer of indirection is enough to dispatch

```
indirection x y
```



# 715. Method call is a fact

# 716. Indexed loops

# 717. Construct data to send from multiple threads

# 718. Barrier can be used for accelerating writes

# 719. Type is control flow path

# 720. Reads are a traversal against all written data

# 721. Relational database used to store JSON keys and reconstructed

# 722. GraphQL is a parser read traversal

# 723. A data structure to define the data structure that is event storeable

```

```

# 724. Loop over a callstack

Create the callstack then loop over it to transform it to how you want it to look.

# 725. Information theoretic

security

# 726. Interpreter semantic discovery through causality

write inefficient code, get efficient code out

# 727. State machine formulation and generating useful APIs



# 728. Situations, runbooks and data loss through server reconnections

# 729. Theory tree and IR

# 730. Do I want to build a database?

I want to accelerate writes in memory.

Durable computation, loops etc

# 731. Paginated spreadsheet

# 732. AST business Architecture, business processes easy to change

# 733. Draw lines across code in order



# 734. Add a constraint on the pile



# 735. Expertise notation

# 736. Move a calloc inside a method outwards

# 737. Async routing, Lanes that the code can move through in a circuitboard nested box  pattern, memory layout, direction

# 738. There's no such thing as a process, movement through memory

# 739. An API for how things work right now, such as a business

# 740. DirectProblem.com

# 743. Preplan async, btree, parallel walk, CPUs move through things, does it matter to you what order things happen in?

parallel update

parallel IO?

compose an order of things

sheer amount of data

```
ORDERED RESULTS
UNORDERED
```

can parallelism solve the latency problem?

```
send()
```

data is memory, but things happening is control flow, IO is control flow

rocks db parallel read

good for mutation

# 744. Binary token protocol with piecetree

Can navigate lots of data this way

btree, lineStarts, piece table

# 745. Terms grid

add behaviours to grid items

properties all the way down

# 746. Emit actions behaviours, programming is animation

Everything is a fresh loop for what you want it to be now, everything is a mutation.

total system state modification

efficient movement between states is learned by positioning of the output, through patterns

diff two collections

movement

a* between positions

relational diff

# 747. Sorted concentric circles, perspective - sorted from the middle



# 748. Mover - the thing that moves things between things

# 749. Process package manager

# 750. C struct code generator

# 751. Mental model database

# 752. Rows and columns parallelism, scaling

# 753. Processes in a cluster and algebra, swaps

# 754. Move things into a parameter list, then do the task, like a process

rules and algebra for the parameters and what is in memory



# 755. You want to change its state or its relation to another thing

# 756. Tree of data caching, cached traversals

# 757. Lifetimes are rectangles

# 758. Efficient insertation into the middle

# 759. Identities and lifetimes, and splitting in the middle (in memory) contiguity

If I have an event loop and I need a place for memory. I have a lifetime problem.  Different sized identities.

Shouldn't be possible to write a program that uses past tokens that are invalid in the future, due to context.

Loops challenge ownership

```
while (true) {

	buffer = malloc()
	recv(buffer, 1024)
	free(buffer)
}
```

need to be freed in a different part of the app

is each object in a different state?

object graph, directions

ownership, it's "inside" another data structure

can't drop inner item while there is an outer item referring to it

```
hashmap:
  key: value
```

object pools automatically

```
hashmap.put(key, pointer)

```

tree of pools, dependencies

hashmap has a pool that can grow,

entrances and exits, compile time determination

whose arena?

arena

where to put the free?

reachability of the state machine

pointer enters the hashmap

```
loop = accept | add-client | recv | 
client close = destroy-client
```

destroy relationship

hashmap links key to pointer

when to destroy pointer and when to destroy key?

structured concurrency?

scope is different to the code method calls

interleaved scopes

hashmap.put(key, pointer) puts pointer in the scope of hashmap's key

```
imagine you have a server event loop and you allocate memory for a client
where do you put the free for resources of different lifetimes?
scopes that interleave the stack, not based on stack

scope1.enter
client = objectpool.malloc(1024)
<compiler creates inferred scope2>
hashmap.put(socket, client)
# implementation of hashmap has a bind(client, socket) compiler instruction
<compiler infers scope2 associates hashmap with client with scope1 with socket as the identity>

# client.disconnect

hashmap.destroy(socket)
<compiler sees scope1 is being destroyed, and socket is linked to client>
scope1.exit
inferred scope2.exit
<the memory of client is freed>

scopes are bound together
destroying the last reachable scope, destroys both, that's where you put the free

```







# 760. Order data in order of use, gravity to plan

# 761. Implementing behaviour with events

# 762. Algebra of positions of input to output

# 763. Movement algebra numbers represent positions, you can handle extreme number of requests per second if it's just a movement

It's the end result that matters. Tracking a movement.

# 764. Navigable data structures

# 765. On id generation and shards

# 766. Fixed graph rendering, graph archetypes

# 777. Expansions to bucket of tokens

is a behaviour an expansion to tokens?

expressions are a form of term rewriting

# 778. Traversal struct: Fast multi dimensional middles

* navigating children fast
* navigating all children fast
* navigating sequential blocks fast
* inserting into any position, block sequence efficiently

```
struct block {
	
}
blockseq block[]

split a sequential block scan

blockseq.children = 55
use SQL for joins
btree



```



# 779. Sentence upvotes

# 780. Add to a past traversal, on the way

# 781. Actor SQL - join order is a traversal



can insert events

# 782. The grid is the primitive that behaviours work against: for scheduling




# 783. REPL recorder

# 793. Control flow graph programming

programming blocks that are larger than method calls but data flow.

match up parameters

# 794. Method calls to events and then schedule

```
for item in items:
	item.seek()
	item.next()
	
```

Sliding window scheduling, bucketing and eventing



# 795. Time and events and buckets

How to model time properly.

# 796. Reorder output events

# 797. Barrier runtime ordering

Commit,

exchange data until all reach the same epoch.

# 797. Mailbox binding

IO thread to worker thread

Even communication from sequent lines of code is a binding of mailboxes.

# 798. Protocols and control flow

# 799. Iteration is a protocol?

# 800. Text replacement term rewriting

egraphs

# 801. Anything goes reconciliation

What does something mean?

# 802. Movement dashboard

Watch things move around and notice bottlenecks.

# 803. Essence of turing completeness

# 804. Data layout and scans

Place data into place for efficient scanning

# 805. Input journeys

trace of all executed code

# 806. Message topology

joins, message passing
forks

# 807. How to bucket schedule

The event faucet is fast and comes from multiple threads, how to schedule and fork work evenly across buckets?

# 808. Movement algebra 

Turing machines that are movements instead of stateful.

not getting into strange states

# 809. Relations and control flow

a bunch of data in memory can be changed in states efficiently. its a whole buffer.

grid and control flow

send compute to storage nodes

compute references sent to storage nodes


memory ownership

# 810. Apply for me .com

List your skills

# 811. Intermedia equivalincia

mutual recursice notation between people

# 812. Monads and coroutines

# 813. The different apps that are in an operating sysytem are just data structures

# 814. Function and object composer

# 815. Compile SQL query to code



