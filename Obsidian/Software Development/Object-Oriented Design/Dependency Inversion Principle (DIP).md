> Entities must depend on abstractions, and not on concretions. It states that the high-level module must not depend on the low-level module, but they should depend on abstractions.

This refers to the decoupling of software modules - instead of high-level modules depending on low-level modules, both will depend on abstractions.
## Example
Let's make a `Windows98Machine` class:
```java
public class Windows98Machine {
    private final StandardKeyboard keyboard;
    private final Monitor monitor;

    public Windows98Machine() {
        monitor = new Monitor();
        keyboard = new StandardKeyboard();
    }
}
```

The problem with this implementation is that we've now tightly coupled these three classes together. Not only does this make our Windows98Computer hard to test, but we've also lost the ability to switch out our `StandardKeyboard` class with a different one should the need arise, and the same with `Monitor` too.

We can decouple our machine from the `StandardKeyboard` by adding a more general `Keyboard` interface and using this in our class:
```java
public interface Keyboard {}

public class Windows98Machine{
    private final Keyboard keyboard;
    private final Monitor monitor;

    public Windows98Machine(Keyboard keyboard, Monitor monitor) {
        this.keyboard = keyboard;
        this.monitor = monitor;
    }
}
```
Here, we use [[Dependency Injection]] to facilitate adding the Keyboard dependency into the class.

