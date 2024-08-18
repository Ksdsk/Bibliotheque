> Abstract Factory is a creational design pattern that lets you produce families of related objects without specifying their concrete classes.

This pattern suggests explicitly declaring interfaces for each distinct product of the product family. Then you can make all variants of products follow those interfaces. For example, all chair variants can implement the `Chair` interface. Many of these designs start by using the [[Factory Method]].

Pros:
- You can be sure that the products you're getting from a factory are compatible with each other.
- You avoid tight coupling between concrete products and client code.
- [[Single Responsibility Principle (SRP)]] - You can extract the product creation code into one place, making the code easier to support.
- [[Open Closed Principle (OCP)]] - You can introduce new variants of products without breaking existing code.
Cons:
- The code may become more complicated than it should be, since a lot of new interfaces and classes are introduced along with the pattern.
## Applicability
Use the abstract factory when your code needs to work with various families of related products, but you don't want it to depend on the concrete classes of those products - they might be unknown beforehand or you simply want to allow for future extensibility.

Consider implementing the abstract factory when you have a class with a set of [[Factory Method|Factory Methods]] that blur its primary responsibility.
## Structure
1. Map out a matrix of distinct product types versus variants of these products.
2. Declare abstract product interfaces for all product types. Then make all concrete product classes implement these interfaces.
3. Declare the abstract factory interface with a set of creation methods for all abstract products,
4. Implement a set of concrete factory classes, one for each product variant.
5. Create factory initialization code somewhere in the app. It should instantiate one of the concrete factory classes, depending on the application configuration or the current environment. Pass this factory object to all classes that construct products.
6. Scan through the code and find all direct calls to product constructors. Replace them with calls to the appropriate creation method on the factory object.
## Example
Let's make a Button interface and the specific classes for MacOS and Windows:
```java
public interface Button {
    void paint();
}
```

```java
public class MacOSButton implements Button {

    @Override
    public void paint() {
        System.out.println("You have created MacOSButton.");
    }
}
```

```java
public class WindowsButton implements Button {

    @Override
    public void paint() {
        System.out.println("You have created WindowsButton.");
    }
}
```

