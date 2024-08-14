> Dependency injection is a programming technique in which an object or function received other objects or function that it requires, as opposed to creating them internally. [Dependency injection - Wikipedia](https://en.wikipedia.org/wiki/Dependency_injection)

Dependency Injection is a [[Design Pattern|design pattern]] to promote the *separation of concerns*, while ensuring that an object or function that wants to use a given service should not have to know how to construct those services. Instead, the receiving *client*, the object or function, is provided ith its dependencies by external code.

This is a key partner to the [[Object-Oriented Design|object-oriented design]], the **Dependency Inversion Principle**.

This makes testing much more effective, especially combined with [[Debugging#Eliminating dependencies in tests|mocking frameworks]].
## Dagger
Dagger is a tool for dependency injection for Java. It is currently being maintained by Google, and used across tons and tons of codebases. 

> Dagger allows us to generate code that mimics the code that a user might have hand-written to ensure that dependency inject is as simple, traceable, and performant as it can be. [Dagger](https://dagger.dev/dev-guide/)

Its main building block is Java's `javax.inject.Inject` [[Java Annotations|annotation]].
### Declaring Dependencies
Dagger constructs instances of your application classes and satisfies their dependencies. You can use Java's `@Inject` to annotate the constructor that Dagger should use to create instances of a class. When a new instance is *requested*, Dagger will obtain the required parameters values and invoke its constructor.

```java
class T
```