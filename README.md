#+TITLE: Software Design
#+AUTHOR: Nelson Rodrigues

* Design Patterns
* S.O.L.I.D
** Class Design (5)
*** SRP - The Single Responsibility Principle
The class should have one, and only one, reason to change
*** OCP - The Open Closed Principle
You should be able to extend a class behaviour, without modifying it
*** LSP - The Liskov Substitution
Derived classes must be substitutable for their base classes
*** ISP - The Interface Segregation Principle
Make fine grained interfaces that are client specific
*** DIP - The Dependency Inversion Principle
Depend on abstractions, not on concretions
** Pack Cohesion (3)
*** REP- The Release Reuse Equivalency
The granule of reuse is the granule of release
*** CCP - The Common Closure Principle
Classes that change together are packed together
*** CRP - The Common Reuse Principle
Classes that are used together are packed together
** Couple Between Packaged (3)
*** ADP - The Acyclic Dependencies Principle
The dependency graph of packages must have no cycles
*** SDP - The Stable Dependencies Principle 
Depend in direction of stability
*** SAP - The Stable Abstractions Principle
Abstractness increases with stability
* GRASP
...
* Design Patterns
** Gof- Gang of Four 
*** Behavioural Patterns
How object communicate between them.
**** Chain-of-responsibility:
Pass the request along the chain until and object handle it.
**** Command:
Encapsulate a request from the invoker in objects
Object-oriented replacement for callbacks
**** Interpreter
Define a grammar for instructions that form a part of a language or notation, allowing the grammar to be easily extended.
**** Iterator:
Standard interface for traversing a collection without the need to understand the underlying structure
**** Mediator:
Encpasulate how a set of objects interact. Intermediary to decouple many peers.
**** Memento
Controls the comunication between two entities storing state of an object to use in future.
**** Observer:
Check when object states changes and all dependent objects are notified
**** State:
Change the object behaviour when internal state change.
**** Strategy:
Encapsulate similar algorithms on a class an choose them in runtime.
**** TemplateMethod:
Similar to Strategy pattern but we could define steps with individual implementations
**** Visitor:
Separates a set of structured data from functionaliy that may be performed uppon it. It separates an algorithm from an object strucutr on which it operates.
*** Creational patterns
Provide ways to instantiate single objects or groups of related objects.
**** Abstract Factory: 
Enables creating objects with common characteristics without expose their convrete class
**** Builder:
Construct complex objects by slice then in multiple operations. Contruct an object step by step 
**** Factory_Method:
Defines an interface for creating objects but subclasses decide which classes to instanciare
Replace class constructors abstracting the process object generation so that the type of the object instanciated can be determined at runtime. 
**** Prototype:
Instanciate a class by cloning the properties of an existing object.
Deep copy: clones main object and child objects.
Shallow copy: duplicates all object's properties, including reference, including referencess.
Shallow copies duplicate as little as possible. A shallow copy of a collection is a copy of the collection structure, not the elements. With a shallow copy, two collections now share the individual elements.
Deep copies duplicate everything. A deep copy of a collection is two collections with all of the elements in the original collection duplicated.
**** Singleton:
The infamous singleton.
Ensures only one instance of a particular class.
*** Structural patterns
Solutions about object composition, interfaces, ..., how to define relationships between class 
**** Adapter:
When an existing class, and its interface does not match
Reuse a class that cooperates with unrelated classes
**** Bridge:
It aims to decouple interface from implementation
C++ is also known as Pimpl (pointer to implementation)
**** Composite:
Create hierarchical objects into tree structures.
Group of objects treated in the same way as single instance of an object.
**** Decorator:
Change the functionality of an object at runtime without impacting the existing functionality of the objects.
**** Facade:
Interface for simplify comunications with complex objects
**** Flyweight:
Optimize resources when working with a very large number of objects
**** Proxy:
Adds a level of indirection for most complex tasks. Is works as an interface for something else.
* Refactor Techniques
** Clean Code 
*** Obfuscating code smells
+ Hard to understand the meaning of variable
+ Meaningless names, choose problem domain
+ Functions should not have more than 10 lines
+ Names with encondigns
+ Ambiguous Names, Reviel your intention
+ Noisy names (names very extensible names), so not too short or not too long
+ C# Namming Conventions: PascalCase or camelCase
  Pascal Case: name of class, methods and proprieties
  Camel Case: private fields, method parameters,local variables, private fifields we nedd to fix them with _ (underline), example private int  _id;
+ The Obfuscators
+ Avoid Regions
+ Comments normally are code smells
+ Poor Names
  - Choose descriptive names
  - Choose names at the appropriate level of abstraction
  - Use standart Nomenclature
  - Choose Unambigous names
  - Use names for long scopes
  - Avoid encodings
  - Names should describe side effects
+ Vertical speration: variables and functions near where they are used; local variables just before first use
*** Comments
+ Don't write comments, rewrite your code
+ Don't explaine "whats" (the obvious)
+ Explain "whys" and "how"
*** Poor Method Signature
+ Boolean flags in parameters of method are normally code smells, because we have to see implementation to see how implemnetation was
+ Check the return type
+ Check the method name
+ Check the parameters
*** Duplicate Code
+ D.R.Y - Don't Repeat yourself
*** Long Methods
+ More than 10 lines of code is a problem
+ Hard to understand
+ Hard to change
+ Hard to re-use
+ Single responsability Principle: we want a method that sepcializes in one thing
+ Things that are related should be together
*** Long Parameter List
+ Encapsulate variables related. Example dateFrom and dateTo encapsulate in one class called DateRange
+ Less than 3 parameters!!!
*** Magic Numbers
+ Use constants or Enums(use in multiple places)
*** Nested Conditionals
+ Use ternary operators for simples (if - else ) when set varibles or return methods from a method
+ Combine
+ Early exit ( return; break; ...)
+ Swap orders
*** Ouput Parameters
+ Avoid Them
+ Return an object from a method instead
*** Switch Statements
+ PolYmorphism(example an enum that says what is type of customers)
+ Logic will be encapsulated in derived classes
+ When we have swith based on type of something is a problem that can be solved with polismorfism
+ Replace them with polymorphic dispatch
+ Use push member down refactoring, passing responsability for sub-classes
*** Tuples
+ Prefer to use a class
*** Variable Declaration At The Top
+ Declare your variables close to their usage 
*** Object orientation abuser code smells
+ Switch normally tells is a problems of lack of abtrasctation and encpasulation, solves with polimorphism
+ Temporary fieds, could be a problem to.
+ *Common refactors*: Push Down Method (passing a method to a child class), Push Down field ( pushing a method to a child class), Replace Inheritance with Delegation 
+ Classes with diferent interfaces is a code smell
+ Abuse static methods and proprieties should only be used on stateless operations and behavior tha will never change. Example global constants such PI, or mathematical operations like add(), ..
+ Avoid child classes call parent classes, in order to avoid circular dependencies
*** Code smells changer preventer
+ Divergent change
  - Class is commoonly changed in at least two diferent ways
  - Indicates a violation of Single Responsability Principle
  - Refactor could be and new class ( Extract Class )
+ Shotgun Surgery
  - Many small changes over all the place
  - Hard to find them all: easy to miss some
  - Refactor could be: move method, move field, inline class, ...
+ Parallel Inheritance Hiearchies
  - Every time you make a subclass, you need a subclass of another
  - Subclasses frequently share same prefix
  - Special case of shutgun surgery
+ Inconsistent Abstraction Level
  - Class interfaces should provide a consistent level og abstraction
  - Often degrades over time with addicton of expedient methods
  - How to solve: Move method and extract method   
+ Conditional Precenting ( multiple if's else's, ....)
  - Tools like Cyclomatic Complexity
  - Solutions
    - Extract method
    - Replace conditional logic with strategy pattern
    - Move Embellishment to Decorator
    - Replace state-altering conditionals with state
    - Introduce Null Object
+ Poorlu Written Tests
  - Tight coupling
  - Difficult changes
*** Code smells Dispensables
+ Lazy class
  - Classes that don't do enought to justify their existance should be removed
  - Solution: collapse hierarchy, inline class (https://refactoring.com/catalog/inlineClass.html)
+ Data class
  - Likely to be manipulated far too much by other classes
  - Refactor solution: move/extract method, hide method/ remove settings method, encapsulate field/collection
+ Duplicated code
  - Solution: extract method, pull up method, extact class, form template method
+ Dead code
+ Speculative generality
  - Solutions: Collapse Hierarchy, inline class, remove parameter
*** Code Smells the couplers
+ Feature Envy: tries to implement a future from an other object
  - Characterized by calling getters
  - Keep together things that change together
  - Some patterns breaks this rule. Strategy, visitor
  - Solution: move method, extract method
+ Inapproprieate intimacy: when classes that know way too much about another
  - Keep class honest by going throught clean interfaces
  - Watch out for: inheritance, biderectional relationships, ...
  - Solutions: move methos, move field, change biderectional association to unidirectional     
  - Replace inheritance with delegation
  - Fewer methods, fewer variables, fewer instance variables 
+ Law of demeter: a given object assume as litlle as possible about the structure or proprieties of anything else (including own subcomponents)
+ Indecent Exposure
  - Sometimes classes or methods are public and shouldn't be
  - Violates encapsulation
  - Solution: classes with a factory
+ Message Chains
  - Occur when client as an object for another object
  - Solution : Hide Delegate extract method, move method  
+ Middle Man
  - Sometimes delegations goes too far
  - Solution: remove middle man, inline method, replace delegation with inheritance
+ Tramp Data
  - Data passed only because someting else its neds it
  - solution: remove middle man, extract method  
+ Aritifical Coupeling
  - Avoid cupple things in your application that don't need to be couple
  - solution: Move method  
+ Hiddent Temporal Coupling
  - Structure code to enforce required order
  - Solution: introduce intermediate results, from template method, passing variables that are dependent, next method needs a variable from previous method  
+ Hidden Dependencies
  - Classes should declare their dependecies in their constructors  
  - Solution: Replace fixed variable wiith a parameter
  - Dependency injection  
*** Environment and Testing code smells
+ Environment smells
+ Test smells
  - Slow tests, poort tests, over-couple, inconistent, ...
+ Not Enought test
  - Test everything that can break
  - Use a coverage tool
  - Write tests to document how the API should work
  - Test boundary conditions
  - Test both sucess and failure paths  
+ Dry vs DAMP
  - Dry: Don't repeat yourself
  - DAMP - Descriptive and MEaningful Pheases
  - Unit test concevntions http://ardalis.com/unit-test-naming-convention  
+ Fragility
  - Small changes in the system break many tests
  - Test that break constabtly coud give some bad name to teh testes 
+ The Liar
+ Excessive set up
+ the Giant
+ The mockery
+ the inspector
+ Generous leftlovers
+ The Local hero
+ The Nipicker
+ The Secrete Catcher
+ The Secret Catcher
+ The Loudmouth
+ The Greedy catcher
+ The Sequencer
+ The Hidden Dependency
+ The Enumerator
+ The Stranger
+ The OS Envangelist
+ Sucess Against All odds
+ The Free Ride
+ The One
+ The peeing tom
+ The slow Poke
+ The constradicion
+ The Roll the Dice
+ Hidden Tests
+ The Second class Citizens
+ Wait and See
+ Innapropriate test group
+ The optimist
+ The Sleeper
+ The Void
*** Method refactorings
+ Extract method
  - Several lines of code that can be grouped toguether and given an intention-revealing name
+ Rename method
  - The name of a method does not reveal its propose
+ Inline method
  - A method's body is just as clear as its name
+ Introduce Explaining Variable
+ Inline Temp
  - You jave a temp that is assigned to once expression
+ Replace Temp with Query
+ Split temporary Variable
  - You have a temporary variable assigned to more than once, but is not a loop variable not a collecting variable
+ Parametrize Method
  - Several methods do similar things but with diferent values contained int the method body
+ Replace Parameter with Explicit Methods
  - you have a method that runs different code depending on the value of an enumerate parameter
+ Add Parameter
+ Separete Query from Modifier
  - You have a method that returns a value but also  changes the state of an object
*** More method Refactorings
+ Perserve whole object
  - You are gettings several values from an object and passing them as Parameters in a method call 
+ Replace parameter with method
+ Introduce Parameter Object
  - You have a group of parameters that naturally go together n
+ Remove Setting Method
  - A property should be set at creation time and never altered
+ Hide method
+ Replace Constructor with Factory Method
+ Replace Erro Code with Exception
+ Remove Assignments to Parameters
+ Replace Exception with a test
+ Replace method with Method Object
+ Compose method
+ Substitute Algorithm
*** Class and Object Refactorings
+ Encapsulate filed
 - This a public Field. create gets and sets methods don't expose them directly
+ Encapsulate Collection
+ Move field
  - Field is used more from other classe than is own
+ Move method
  - Method is  used more from other classe than is own
+ Extract class
+ Inline class
+ Extract Interface
+ Extract Subclass
+ Extract Superclass
+ Hide Delegate
+ Remove Middle man
*** Class and Hierarchy Refactorings
+ Pull up Field
  - Two subclasses have same field
+ Push Down Field
+ Pull up method
  - Methods with identicl results on subclasses
+ Push down method
+ Collapse hierarchy
+ Replace Inheritance with Delegation
+ Replace Delegation with Inheritance
+ Replace Type Code With Class
+ Replace Type Code with subclasses
+ Replace Conditional with polymorphism
*** Patterns-Based Refactorings
- Encapsulates classes with factory
- From Template Method
- Introduce null object
- Move Accumulation to visitor
- Move Embellishent to decorator
- Replace Conditional Dispatcher with Command
- Replace Conditional Logic with Strategy
- Replace State-Altering Conditionals with State
- Replace Type Code with State (or Strategy
- Unify Interfaces with Adapter
*** Gilded Rose Kata
- Gilded Rose Kata Setup
- Beginning the Kata
- Adding First Tests
- Testing Aged Brie
- Testing Sulfuras
- Testing Backstage Passes.
- Refactoring with StoreItem
- Testing Individual Strategies
- Adding Conjured Item Support


* Links
[[http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod][PrinciplesOfOod (Uncle Bob)]]
