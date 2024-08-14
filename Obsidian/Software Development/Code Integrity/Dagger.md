Dagger is a tool for dependency injection for Java. It is currently being maintained by Google, and used across tons and tons of codebases. 

> Dagger allows us to generate code that mimics the code that a user might have hand-written to ensure that dependency inject is as simple, traceable, and performant as it can be. [Dagger](https://dagger.dev/dev-guide/)

Its main building block is Java's `javax.inject.Inject` [[Java Annotations|annotation]].
## Declaring Dependencies
Dagger constructs instances of your application classes and satisfies their dependencies. You can use Java's `@Inject` to annotate the constructor that Dagger should use to create instances of a class. When a new instance is *requested*, Dagger will obtain the required parameters values and invoke its constructor:
```java
class Thermosiphon implements Pump {
	private final Heater heater;

	@Inject
	Thermosiphon(Heater heater) {
		this.heater = heater;
	}
	...
}
```

Dagger can also inject fields directly. In this example, it obtains a `Heater` instance for the `heater` field and a `Pump` instance for the `pump` field:
```java
class CoffeeMaker {
	@Inject Heater heater;
	@Inject Pump pump;
	...
}
```

When `@Inject` is not feasible (e.g. Interfaces, third-party classes, ...), you can use `@Provides` annotation to satisfy a dependency. The method's return type defines which dependency it satisfies. For example, the `provideHeater()` is invoked whenever a `Heater` is required:
```java
@Provides static Heater provideHeater() {
	return new ElectricHeater();
}
```

If the `@Provides` method has a dependency, it's still possible to use the annotation as long as the dependency has an `@Inject` constructor.

Additionally, all `@Provides`must belong to a module, which can be added with the `@Module` annotation in the class like so:
```java
@Module
interface HeaterModule {
	@Provides static Heater provideHeater() {
		return new ElectricHeater();
	}
}
```
