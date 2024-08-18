> A client should never be forced to implement an interface it doesn't use, or clients shouldn't be forced to depend on methods they do not use.

Larger interfaces should be split into smaller one. By doing so, we can ensure that implementing classes only need to be concerned about the methods that are of interest to them.
## Example
Let's make a `BearKeeper` class:
```java
public interface BearKeeper {
	void washTheBear();
	void feedTheBear();
	void petTheBear();
}
```
However, the interface is rather quite big and each bear keeper may not need the methods that it describes. For example, a bear keeper could only be in charge of washing the bear, or only in the charge of feeding the bear. 

We can separate the interface so it follows a [[Single Responsibility Principle (SRP)|single responsibility]]:
```java
public interface BearCleaner {
    void washTheBear();
}

public interface BearFeeder {
    void feedTheBear();
}

public interface BearPetter {
    void petTheBear();
}
```

Now, we can implement only the necessary interfaces like so:
```java
public class BearCarer implements BearCleaner, BearFeeder {

    public void washTheBear() {
        //I think we missed a spot...
    }

    public void feedTheBear() {
        //Tuna Tuesdays...
    }
}
```
