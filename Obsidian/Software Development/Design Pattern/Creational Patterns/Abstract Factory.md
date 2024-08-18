> Abstract Factory is a creational design pattern that lets you produce families of related objects without specifying their concrete classes.

This pattern suggests explicitly declaring interfaces for each distinct product of the product family. Then you can make all variants of products follow those interfaces. For example, all chair variants can implement the `Chair` interface. Many of these designs start by using the [[Factory Method]].

Pros:
- You can be sure that the products you're getting from a factory are compatible with each other.
- You avoid tight coupling between concrete products and client code.
- [[Single Responsibility Principle (SRP)]] - You can extract the product creation code into one place, making the code easier to support.
- [[Open Closed Principle (OCP)]] - You can introduce new variants of products without breaking existing code.
Cons:
- The code may become more complicated than it should be, since a lot of new interfaces and classes are introduced along with the pattern.