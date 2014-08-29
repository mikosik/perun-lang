## Perun Language high level design

Perun is a general purpose programming language. It is built on two premises:
 * "Unless simple things are easy, complex things are impossible".
 * "It seems that perfection is attained, not when there is nothing more to add,
but when there is nothing more to take away." Antoine de Saint Exupéry

### High level ideas that influenced design

Each programming language designer has to decide what concepts are available
in the language and what construct (or constructs) represents them.
For example concept of 'iterating over list' is represented using 'for' loop
construct in most imperative languages.
When deciding which concepts are present inside the language and what
constructs represent them, following values were taken into account:

* Simplicity - Concept should be represented using the simplest construct available.
Simpler is the one that requires less capacity of human brain to process it
(understand/learn/memorize/use). Simpler things have lower conceptual weigh.

* Symmetry - If two concept are similar/symmetrical then they should be represented
by symmetrical constructs. This way conceptual weight of both constructs is
lower.

* Consistency - Construct should always have the same meaning independent
of usage context.

* Orthogonality - Each construct should represent exactly one concept.
This way different constructs can be combined together freely.

* Density - Ideally we would like to be able to combine constructs in every way and
convey different meaning with each combination. Both requirements are impossible to
achieve especially if we want resulting language to be easily understandable by human.


### Concepts present in language:
 * Object oriented - Each element of the language (literal, variable,
parameter, method, function, class and even package) is an object.
Each object has separate internal state kept in its fields that are references
to other objects.
Each object has set of methods that can be called and which have access to
object's fields.
 * Functional - As function is also an object, it can be passed as an argument
to other function, which mean higher order functions are possible.
Closures (functions that are defined in scope of other block and have access
to objects that are accessible by outer block) are also possible.
In fact method is just a closure - it has access to fields defined in
outer scope - class's body.
 * No global state - There's no other state except one kept inside object fields.
This means there's no global state (global variables or other constructs) that
is accessible by all code directly.
 * no keywords (reserved words) - There's no list of special keywords (reserved words)
that cannot be used as identifiers. How to express concepts like 'for' loop without
using 'for' keyword will be described below.
 * dependency injection - There's no 'new' operator. All objects are created by
dependency injection mechanism and their internal fields are created and injected
the same way transitively.
If some method needs to create objects on demand then that its object should have
Provider field (that will be automatically injected) and use that Provider for creating
new objects.
 * exceptions - Error handling is done through unchecked exceptions.
This is the only way to make it orthogonal to the function logic.
 * Control flow statements - There's no special keywords for control statements.
They are just ordinary functions inside core library. Iterating over a list
can be implemented as 'for' function that takes a list to iterate over and
a function that has one parameter of type equal to list element types.
It is yet to be decided how to design language syntax to make such function
calls simple.

### Concepts outside of language definition
There's couple of concept that outside of the scope of language specification.

 * compiled or interpreted - It is not defined whether language is compiled
or interpreted and it is not necessary. 
Different tool sets (compiler + runtime) can be created for the language and
can solve this problem differently as long as they fulfil language specification
and provide core libraries.


TODO think about it
 * concurrency - message passing (no shared state) http://en.wikipedia.org/wiki/Actor_model
 * immutability
 * no nulls - don't want nulls but how to avoid them? Introducing 'dummy' objects?
 * function overloading - 
 * annotation - yes
 * no inheritance? effective java: "favour composition over inheritance", inheritance breaks encapsulation
 * reflection


not forbidden but might be handled as warnings by compiler tool - circular package dependency(?),
unused variables




