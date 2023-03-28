---
title: "A Tale of Paradigms"
seoTitle: "A Tale of Paradigms"
seoDescription: "The Awareness of the programming paradigm evolution can tell you the whole story of where everything about modern programming languages started, how it evol"
datePublished: Tue Mar 28 2023 22:38:37 GMT+0000 (Coordinated Universal Time)
cuid: clfsualrf000109jr3tvg4ovp
slug: a-tale-of-paradigms
canonical: https://halawa.dev/2023/03/25/a-tale-of-paradigms/
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680042819531/2df74662-d81f-49cf-b758-1dc8a7f39887.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1680043048620/7b6c4646-4ab9-43bc-ba45-f832dc70e85c.png
tags: software-development, developer, software-engineering

---

> **Why should I know about these paradigms?**
> 
> <cite>~ Developer</cite>

While it might seem like a valid disapproving question about the whole topic, let's agree that everything -obviously- was there for a reason, and like everything in computer science, everything existed to solve a specific problem. So, being aware of the programming paradigm evolution can tell you the whole story of where everything about modern programming languages started, how it evolved, and re-shaped multiple times to meet a specific need.

Whether it's cost, usability, ease of use, or extending the capabilities of solving new types of problems using the computing machines we have in hand that would in turn makes our lives easier and enable us to develop new technologies that would extend our capabilities as human beings who came to the world with five senses that we could barely rely on in-terms of precision.

The importance of being aware of the different programming models is to address other possibilities and better solutions for problems that perhaps a single paradigm won't solve efficiently or to widen your understanding of the different paradigms.

Being aware of the past will also allow you to get the full power of the current paradigm in hand, in that knowing why it was shaped the way it's right now will give you a clear understanding of how to use its features efficiently. because every matter of evolution tends to cover a drawback of the old model. Furthermore, to evolve solutions to the next stage and avoid mistakes made in the past.

## Definition of a Programming Paradigm

Paradigms are a way to classify programming languages based on their features, and a single language can be classified into multiple paradigms.

## Paradigms Categories

A paradigm can be Imperative where you would instruct the machine on **how to change its state**. Or it could be **Declarative** where you'd describe what kind of results do you need, and pre-defined routines will take care of that.

### Imperative Paradigms

It's worth noting that Imperative paradigms were inspired by the Turing machine which was a bottom-up step-by-step approach to computation, and there are two main types of them today:

* Procedural
    
* Object-Oriented
    

The imperative programming paradigm assumes that:

* The computer can maintain through environments of variables any changes in a computation process.
    
* Computations are performed through a guided sequence of steps, in which these variables are referred to or changed.
    
* The order of the steps is crucial because a given step will have different consequences depending on the current values of variables when the step is executed.
    

#### Examples

* Lisp
    
* Closure
    
* C, C++, Java
    

### Declarative Paradigms

On the other hand, declarative paradigms had their roots in the [Lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus#:~:text=Lambda%20calculus%20(also%20written%20as,to%20simulate%20any%20Turing%20machine.) that was introduced by Alonzo Church in the 1930s, which had a different nature of being a functional top-down approach of computation that is based on constructing [lambda terms](https://en.wikipedia.org/wiki/Lambda_calculus#Lambda_terms) and performing [reduction](https://en.wikipedia.org/wiki/Lambda_calculus#Reduction) operations on them, there are 4 classifications of them.

* Functional
    
* Logical
    
* Reactive
    
* Mathematical
    

## Procedural Paradigm

The procedural paradigm is an Imperative paradigm that uses a structured approach to change a program's state. and it focuses on describing how a program operates.

### Structures

* **Statements** \- those forms and instructions.
    
* **Sequence** \- which consists of multiple statements that get executed in sequence (one by one).
    
* **Selection** \- a block of code that encapsulates a sequence of statements that get executed if a certain state has met, which get tested using what is so-called a Logical Expression. (if ... elseif ...else)
    
* **Iteration** \- A block of code that encapsulates a sequence of statements that get executed N of times based on a logical expression too. e.g. (while, repeat, for, do..while)
    
* **Subroutines** - an encapsulated block of code that could be reused multiple times in different places upon call, which affects the program state.
    

### Benefits

* While it might seem a naïve approach, it was revolutionary and changed how we instruct computing machines. Before, it was only simple statements in (assembly) that weren't simple or easy to maintain! or even worth (the machine language) which was hell!
    
* The code became easier to test or debug because the code was structured in a way humans could understand.
    
* Eliminated the repetition of sequences to some extent using procedures (which are different from functions).
    

### Drawbacks

* It focuses on what needs to be done, rather than on the integrity of the data it manipulates.
    
* **Global variables**. The problem with global variables is that since they can be accessed and modified by every subroutine in a program, which was really hard to trace where it has been changed that makes debugging very hard, especially with large-scale applications.
    
* Even though it accelerated the development process (If compared to ancestor paradigms used in assembly and machine language) more human labor was required and it was expensive and also became a time-consuming factor in software development.
    
* The advances in computer processing allowed more complex problems to be asked of computers, but it also meant that software was getting involved as well that having a big ball of mud won't help scale that software or visualize it in a simple way.
    

### Examples

Here are the most popular languages that followed the Procedural paradigm ordered by release date:

* COBOL
    
* FORTRAN
    
* Algol 68
    

## Structured Approach

The structured approach brought modules and functions to the table, and followed the same coding style as a procedural paradigm, in a way that we can consider an upgrade to the previous paradigm that was adopted by COBOL and Fortran.

### Structures

* **Functions** \- While it's also a subroutine, this type of subroutine allowed encapsulating functionality that returns and answers based on arguments passed to these functions. which is different from Procedure subroutines, which only encapsulated a sequence of statements that get executed and manipulate shared mutable states (aka Global variables).
    
* **Modules** \- Allowed dividing the whole program from one file, into multiple files that either had a specific problem to solve or an enhancement to the program file structure.
    

### Benefits

* Acceleration of the development time required to accomplish a program was minimized, because multiple programmers could work on different modules at the same time.
    
* Enabled the reusability of software because those sub-routines could be saved into libraries that could be imported later into other projects.
    

### Examples

* PASCAL
    
* C
    

## Object-Oriented Paradigm

An imperative paradigm based upon objects (having both data and methods) that aims to incorporate the advantages of modularity and reusability.

### The Origin Of The "object-oriented" Term

> *I made up the term ‘object-oriented’, and I can tell you I didn’t have C++ in mind.*
> 
> *<cite>Alan Kay, OOPSLA ‘97</cite>*

The object-oriented paradigm has been around for almost 8 decades since it was first coined by **Alan Kay** -designer of **Smalltalk**\- between 1966 and 1967. Although, the first programming language widely recognized as “object-oriented” was **Simula 1** (1962) and **Simula 2** (1967).

However, the early inspiration for that paradigm was driven by Ivan Sutherland's Sketchpad application which was created between 1961 and 1962 and published in his [thesis](https://dspace.mit.edu/handle/1721.1/14979). Objects were typically data structures representing graphical images, and featured inheritance via dynamic delegates that Ivan called "masters" and any additional instances of the objects were called "occurrences".

### SIMULA

*SIMULA* (an acronym for Simulation) was designed as a process description language, as well as programming by Ole & Nygaard.

Nygaard's concerns with modeling the phenomena associated with nuclear fission perhaps the main drive behind creating SIMULA that followed Algol 60, which was to Model a specific phenomenon of the real-world based on a description that computers could understand.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680042946248/c9c9fe20-acf1-4cfb-82b4-b4d5085a5e20.jpeg align="center")

So, the main objective, of being Object-oriented here was "Modeling" a phenomenon of the real world, such as humans, weather, events, ... and anything if you can describe their attributes and actions also their possible interactions with another phenomenon.

#### SIMULA Contributions To The Object-Oriented Paradigm

It was not SIMULA code that Models the real world, but the objects created by that code and the ability to see past the code to the objects that it creates.

The code security that SIMULA promoted has also inspired modern languages from multiple perspectives, for example:

* Combining compile-time and run-time checks ensured that errors wouldn't rise in the machine, and the ability to explain the behavior of a program entirely in terms of the semantics of the programming language, which we call ***type-safety.***
    
* References were qualified to refer to objects of a particular class, so the attributes of those objects were known to the compiler. and those attributes could be accessed using a ***connection statement*** (known today as **"dot" notation** e.g., `HttpClient.Get()` )
    

SIMULA has contributed a lot to the evolution of what Object-Oriented looks like today, and those contributions can be summarized as:

* Record Structures (class blocks with variable declarations)
    
* Procedural data abstraction (class blocks with variable and procedure declarations)
    
* Processes (class blocks that continue to execute after their callers have resumed execution)
    
* Incremental abstraction, through *prefixing* one class block with the name of another class block
    

SIMULA was about generalization and liberation of Algol 60 block to create the class, and that was followed too by Bjarne Stroustrup, in that C++ was attempting to make an Object-Oriented C like what SIMULA did with Algol 60, and here I quote his words:

> *C++ was designed to provide Simula’s facilities for program organization together with C’s efficiency and flexibility for systems programming. … The goal was modest in that it did not involve innovation, and preposterous in both its time scale and its Draconian demands on efficiency and flexibility.*
> 
> <cite>Bjarne Stroustrup the creator of C++</cite>

### Kay's Essence of Object-Oriented

![](https://halawadev.files.wordpress.com/2023/03/alan-kay.jpg?w=400 align="left")

> I thought of objects being like biological cells and/or individual computers on a network, only able to communicate with messages (so messaging came at the very beginning -- it took a while to see how to do messaging in a programming language efficiently enough to be useful).
> 
> *<cite>Alan Kay on the Meaning of “Object-Oriented”</cite>*

Alan kay promoted a [recursive design](https://cs.lmu.edu/~ray/notes/whatisrecursion/#:~:text=In%20computer%20science-,Recursion%20in%20Nature,-Self%2Dsimilarity%20occurs), where parts have the same power as the whole. and the need was to stop breaking down programs into separate data structures and procedures. In that every object has to act as a single independent unit, that knows how to handle its internal state and evolve dynamically in run-time if the need arises.

> OOP to me means only **messaging**, **local retention and protection and hiding of state-process**, and **extreme late-binding of all things**.
> 
> <cite>Alan Kay on the Meaning of “Object-Oriented Programming”</cite>

According to Alan Kay, OO Ingredients are **Message passing**, **Encapsulation,** and **Dynamic Binding** that could be explained like this:

* **Avoid shared mutable states** by encapsulating and isolating other objects from local state changes. In that every object will be responsible for its internal state, other objects cannot miss other objects' states without its permission, instead, they can communicate a message with whatever they need.
    
* **Decoupling objects** from each other, objects are loosely coupled, and they can communicate through APIs (aka Interfaces in Java and C#) that the receiver object exposes.
    
* **Adapting to changes at runtime** with [late binding](https://en.wikipedia.org/wiki/Late_binding) a sender object might ask another object to change the state by providing a few arguments to a method bound to the receiver object at runtime, rather than at compilation time.
    

And Said [TimBudd](https://wiki.c2.com/?TimBudd) on explaining Kay's essence:

1. EverythingIsAnObject.
    
2. Communication is performed by objects communicating with each other, requesting that objects perform actions. Objects communicate by sending and receiving *messages*. A message is a request for action, bundled with whatever objects may be necessary to complete the task.
    
3. Objects have their own memory, which consists of other objects.
    
4. Every object is an instance of a class. A class simply represents a grouping of similar objects, such as integers or lists.
    
5. The class is the repository for *behavior* associated with an object. That is, all objects that are instances of the same class can perform the same actions.
    
6. Classes are organized into a singly rooted tree structure, called the *inheritance hierarchy*. Memory and behavior associated with instances of a class are available to any class associated with a descendent in this tree structure.
    

His message didn't include the following feature though:

* Polymorphism - functions in procedural paradigm already allowed that.
    
* Classes are being treated like a type.
    
* Class Inheritance
    
* Static Types
    

Which is very popular with C++, C#, and Java. Even though it doesn't mean that these features are not necessary, it is important to be aware of that perspective about "Objects" because it represents one of the core problems that this paradigm was trying to solve.

## Fast-Forward

The Idea of what an "Object" really means, and the supplementary features needed to shape it with dynamicity and generality in mind has been subject to many debates for decades, and still.

It wouldn't be a coincidence if you have already touched on the difference between a language like Java, and JavaScript's implementation of the Object-Oriented paradigm, perhaps you always wondered why they are different even if they are trying to provide the same thing. and by reading this you might have the answer now, it's because every implementer had his own philosophy about how it should look, and how it should be shaped. but SIMULA shows the core idea, which was Modeling phenomena of the real world, and attempting to let an object behave in dynamicity, and generality and even evolve and reshape itself somehow to accommodate future changes.

So, don't get too attached to a specific programing language or a paradigm, rather be pragmatic about what it can provide you to solve the problem at hand in an efficient way and according to your trade-off results. It might seem overwhelming, but by studying the properties and the potential of everyone, you wouldn't need that huge effort.

That was an attempt to highlight flashes of the history behind the modern languages we know today, the information presented here might be subject to mistakes, it would be my interpretation's fault. Thus, I'll ask gently to leave a comment if any incident has been found.

## References

* [https://www.sciencedirect.com/science/article/pii/S0890540113000795](https://www.sciencedirect.com/science/article/pii/S0890540113000795)
    
* [https://medium.com/javascript-scene/the-forgotten-history-of-oop-88d71b9b2d9f](https://medium.com/javascript-scene/the-forgotten-history-of-oop-88d71b9b2d9f)
    
* [https://www.quora.com/What-did-Alan-Kay-mean-by-I-made-up-the-term-object-oriented-and-I-can-tell-you-I-did-not-have-C++-in-mind](https://www.quora.com/What-did-Alan-Kay-mean-by-I-made-up-the-term-object-oriented-and-I-can-tell-you-I-did-not-have-C++-in-mind)
    
* [https://wiki.c2.com/?EverythingIsAnObject](https://wiki.c2.com/?EverythingIsAnObject)