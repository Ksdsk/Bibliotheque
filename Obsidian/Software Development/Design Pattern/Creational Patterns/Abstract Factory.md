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
Let's make a Button and Checkbox interface and the specific classes for MacOS and Windows:
```java
public interface Button {
    void paint();
}

public interface Checkbox {
    void paint();
}

// MACOS
public class MacOSButton implements Button {

    @Override
    public void paint() {
        System.out.println("You have created MacOSButton.");
    }
}

public class MacOSCheckbox implements Checkbox {

    @Override
    public void paint() {
        System.out.println("You have created MacOSCheckbox.");
    }
}

// WINDOWS
public class WindowsButton implements Button {

    @Override
    public void paint() {
        System.out.println("You have created WindowsButton.");
    }
}

public class WindowsCheckbox implements Checkbox {

    @Override
    public void paint() {
        System.out.println("You have created WindowsCheckbox.");
    }
}
```

Let's make an interface as an abstract factory which houses the types and certain methods:
```java
public interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}
```

Concrete factories are then made:
```java
public class MacOSFactory implements GUIFactory {

    @Override
    public Button createButton() {
        return new MacOSButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new MacOSCheckbox();
    }
}

public class WindowsFactory implements GUIFactory {

    @Override
    public Button createButton() {
        return new WindowsButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new WindowsCheckbox();
    }
}
```

Let's make our runner:
```java
public class Application {
    private Button button;
    private Checkbox checkbox;

    public Application(GUIFactory factory) {
        button = factory.createButton();
        checkbox = factory.createCheckbox();
    }

    public void paint() {
        button.paint();
        checkbox.paint();
    }
}

public class Demo {

    /**
     * Application picks the factory type and creates it in run time (usually at
     * initialization stage), depending on the configuration or environment
     * variables.
     */
    private static Application configureApplication() {
        Application app;
        GUIFactory factory;
        String osName = System.getProperty("os.name").toLowerCase();
        if (osName.contains("mac")) {
            factory = new MacOSFactory();
        } else {
            factory = new WindowsFactory();
        }
        app = new Application(factory);
        return app;
    }

    public static void main(String[] args) {
        Application app = configureApplication();
        app.paint();
    }
}
```

