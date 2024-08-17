> Objects or entities should be open for extension, but closed for modification. In doing so, we stop ourselves from modifying existing code and causing potential new bugs.

It's a pretty simple principle and largely depends on the `extends` keyword or the alike.
## Example
Let's build a guitar:
```java
public class Guitar {
	private String make;
	private String model;
	private int volume;

	// Constructors, getters, and setters
}
```

If we wanted to add some feature to it later, like, a `ElectricGuitar`, we could simply *extend* from the prebuilt `Guitar` class:
```java
public class ElectricGuitar extends Guitar {
	private String ampere;
	// ...
}
```
