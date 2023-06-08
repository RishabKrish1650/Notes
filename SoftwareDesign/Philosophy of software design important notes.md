#Chapter One: Intro

## Main Problem Devs Face

The main problem Devs face is understanding the systems we are creating. Major issue is that the system grows in complexity as and when the features and the requirements change and increase.

Software design is mainly dealing with the complexity of a situation.

## How do we deal with complexity?

The book asserts two general approaches:

* Make code more simple and obvious
* Encapsulate complexity so that programmers can work on a system without being exposed to all the complexity at once - MODULAR DESIGN
    * Modular Design means means dividing the system into modules(for example - classes), and these modules are designed relatively independent of each other so that a dev can work on one module without having to understand the other modules

## On the nature of software design

- Software Design is a continuous process that spans the entire lifecycle of the software system
- The key problem is that with many software systems, problems don't become apparent until implementation is underway
- Most software development use an incremental approach such as agile development, which works because software is malleable enough to allow for significant design changes partway
-  Therefore the initial design for development is never the best one, experience inevitably shows a better way to do things
- As a developer always be on the lookout for opportunities to improve the design of the system you are working on, this will also help improve your design skills
- One of the key elements of design is recognising and reducing the complexity, so if you are constantly thinking about design, you should also be thinking about complexity and how to minimise it
- A developers job is to not just create code that THEY can work with easily but to create code that others can also work with easily


## Red Flags

- One of the best ways to improve design skills is to learn to detect red flags
- *Red Flags* are signs that a piece of code is more complex than it needs to be
- When you see a red flag stop and look for an alternative design that fixes the problem
- When first trying this approach, use several alternatives i.e. __DO NOT GIVE UP EASILY__, try lots of alternatives to fix the problem so you learn more
- This note will get updated as I keep going through the book
- __NOTE: The list provided in the book is non-exhaustive with more experience you will also learn more red flags to identify design problems. Add them here - if you maintain this for that long you flaky piece of shit__ 

#Chapter Two:

## Important Questions:
- What exactly is complexity?
- How can you tell if a system is unnecessarily complex?
- What causes systems to become complex?

## Recognising Complexity

- Recognising complexity(i.e recognising the symptoms of complexity) is a crucial design skill, once you identify that a system is too complex you can use that to guide your design philosophy towards simplicity
- Allows for pre-identification of problems before development meaning we can make smarter choices around design
- It is easier to recognise that a design is simple rather than *creating* a simple design
- With experience you will understand that there are certain common patterns which aid in creating simpler design while other patterns produce complexity

## Complexity

**DEFINITION:**
Anything related to the structure of a software system that makes it hard to understand and modify

Some forms of complexity:

- A piece of code that is hard to understand
- Huge effort required to make a small improvement
- Which parts to modify to implement the improvement are unclear
- Difficult to fix one bug without introducing another

Another way of thinking about it is via cost and benefit. In a complex system, the cost to make even minor improvements i.e. bring about a small benefit has a high cost

Complexity does not refer to the overall size or functionality of the system. If a system is easy to work on then it is simple, regardless of how large it is or how many features there are.

Another factor that determines complexity is how frequent activities are. For example if a module in your project is complex however it needs to be touched almost never, then it does not impact the overall complexity of the system.

Mathematically we can define Total Complexity(C) as the complexity of each module m (Cm) weghted by the fraction of the time developers spend working on that part(Tm) i.e.

C = (Summation over m)(Cm * Tm)

##A feature of complexity:
- **More apparent to the reader** than the writer -> sometimes code you write is simple to you but to the reader it is complex
- The above situation presents an interesting learning opportunity, if you probe the reader as to why the code is complex.

## Manifestation of complexity
Three General ways complexity manifests:

- Change Amplification
- Cognitive Load
- Unknown Unknowns

## Change Amplification
- Seemingly simple changes requires code modifications in many different places.
- One of the goals of good design is to ensure that design changes affect the least amount of code possible

## Cognitive Load
- How much a developer needs to know before completing a task
- High cognitive load means devs need to spend time learning the system and there is a higher chance of bugs if they missed something
- This **DOES NOT MEAN** that shorter code has lesser cognitive load -> some frameworks allow applications to be written with only a few lines of code but are difficult to understand
- Sometimes an approach which requires more lines of code is actually simpler, because it reduces cognitive load

## Unknown unknowns
- Not obvious which pieces of code must be modifed to complete a task
- Unclear as to what information the developer must have to complete the task
- The WORST one because there is something we need to know but there is no way to find out if that is an issue or to find out what it is
- Different from the other two symptoms in that while they are annoying/ difficult to fix, it is possible to understand(albeit at a high cost) what needs to be done
- This is why the most important goals of a good design is for a system to be *Obvious*(discussed in later chapters)

## Causes of complexity

At a high-level complexity is caused by two things: dependencies and obscurity

Dependencies and obscurity contribute to the Three General Manifestation of complexity:

- Dependencies lead to Cognitive Load and Change Amplification
- Obscurity leads to Unknown unknowns

## Dependencies
A Dependency exists when: 
- a given piece of code cannot be understood and modified in isolation
- the code relates in some way to other code and the other code must be considered and/or modified if the given code is changed

Dependencies are a fundamental part of software design, we intentionally introduce them as part of the design process -> every time a class is written, it creates dependencies around the API of that class. So it is not as simple as saying that dependencies = bad. The goals of software design is to reduce the number of dependencies and if there are any dependencies to make them as simple and obvious as possible.

## Obscurity
Obscurity occurs when important information is not obvious or information is inconsitent
Some examples:
- variable name that does not contain any useful information
- Documentation of the variable doesn't specify units, so the only way is to scan code for its use
- A variable name is used for two different purposes(inconsistent)

Obscurity usually arises because of inadequate documentation, but it is also a design issue, since clean obvious design leads to less need for detailed documentation

## Complexity is Incremental

Complexity is not one single thing -> it is an accumulation of small things over time. A single dependency or obscurity might not affect the overall maintainability of the software system -> but hundreds/thousands of them piled up together will affect the system over time.

The incremental nature of complexity makes it very hard to control. It is very easy to suggest that a little bit of complexity introduced by the change you are making is no big deal, but if everyone thinks that way then the complexity accumulates rapidly, and once it has it is very difficult to remove.

In order to slow the growth of complexity we need to adopt a zero tolerance philosophy.

# Chapter 3

## Tactical vs Strategic programming

- Many orgs prioritise the use of tactical programming, where we focus on getting the features out as quickly as possible
- Good design requires a strategic approach, invest time to produce clean designs and fix problems
- In the long term, strategic programming will produce better designs
- Good Design will not come for free, it is something you invest in continually so that problems with the system do not accumulate rapidly.

## Tactical programming

In the tactical approach the main focus is to get something working. This is short-sighted because you are not planning for the future. Instead your main priority is to get the thing working rather than looking for the best design. A developer thinks it is ok to introduce a kludge or hack if it allows the current task to be completed quickly. However complexity is incremental, as such if every developer on the team thinks this way things quickly spiral out of control. Complexity begets more complexity and soon the code is a mess.

## Strategic programming

Working code is not enough -> this is the core principle we need to understand in order to become a good software designer. Introducing complexity is absolutely unacceptable(i.e. we have Zero Tolerance for complexity). 

Our primary goal must be to produce great design, which also happens to work. You will have to make proactive and reactive designs. The proactive ones when you are treading new ground for ex. when designing a new class, try multiple designs to see which one is better. Reactive approaches are for when you inevitably make a mistake, you will have to go back and fix it with better design. 

Remember that the ideal design won't come about immediately, but will become apparent in bits and pieces. Consistent time investments over time will yield results.

# Chapter 4

## Modular design

- One of the most important techniques for managing software complexity is to ensure that devs aren't facing the entireity of the systems complexity at once. 
- We achieve this by seperating the system into modules, which is called modular design
- Modules can take many forms like classes, subsystems, or services etc.
- In an ideal world all modules would be independent and any developer would be able to work on a module without knowledge of the others
- This is nearly impossible in the real world as modules call on each others methods, which creates a dependency between the modules
- The goal of modular design is to minimise the dependencies when possible
- We can think of a module as two parts: an interface and an implementation of that interface.
- An interface should contain everything that another developer needs to know, in order to use it elsewhere i.e. the interface describes what the module does but not how it does it.
- The implementation is what actually does the work








