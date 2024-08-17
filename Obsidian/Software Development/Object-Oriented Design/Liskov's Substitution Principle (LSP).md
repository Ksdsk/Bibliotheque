> Every subclass or derived class should be substitutable for their base or parent class.

This means if a `class A` is a subtype of `class B`, we should be able to replace `B` with `A` without disrupting the behaviour of our program.
## Example
Let's make a Car interface:
```java
public interface Car {
	void turnOnEngine();
	void accelerate();
}
```

Let's implement our interface and provide some code for the methods:
```java
public class MotorCar implements Car {
	private Engine engine;

	// Constructors, getters, and setters

	public void turnOnEngine() {
		engine.on();
		// ...
	}

	public void accelerate() {
		engine.powerOn(1000);
		// ...
	}
}
```

That's for a motor vehicle, but we don't have any of that in an Electric car:
```java
public class ElectricCar implements Car {
	// Constructors, getters, and setters

	public void turnOnEngine() {
		throw new AssertionError("I don't have an engine!");
	}

	public void accelerate() {
		// ...
	}
}
```

This would be a clear violation of the LSP principle. However, if we implement the interface as:
```java
public interface Car {
	void turnOnCar();
	// ...
}
```
... and make the necessary changes