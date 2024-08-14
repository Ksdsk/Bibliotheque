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
## Building the Graph
The `@Inject` and `@Provides` annotated classes form a graph of objects, linked by their dependencies. Calling code like an application's `main` method accesses that graph via a well-defined set of roots. In Dagger, that set is defined by an interface with methods that have no arguments and return the desired type. By applying the `@Component` annotation to such an interface and passing the *module* types to the `modules` parameter, Dagger then fully generate an implementation of that contract.
```java
@Component(modules = DripCoffeeModule.class)
interface CoffeeShop {
	CoffeeMaker maker();
}
```

The implementation has the same name as the interface prefixed with `Dagger`. For example, the `CoffeeShop` instance of the interface can be obtained by invoking the `builder()` method of the Dagger implementation:
```java
CoffeeShop coffeeShop = DaggerCoffeeShop.builder()
	.dripCoffeeModule(new DripCoffeeModule())
	.build();
```

If all the dependencies can be constructed without the user creating a dependency instance, such as for a module with all static methods, Dagger will add a `create()` method that can be used to get a new instance without having to deal with the builder:
```java
CoffeeShop coffeeShop = DaggerCoffeeShop.create();
```

After this, our `CoffeeApp` can simply use the Dagger-generated implementation of `CoffeeShop` to get a fully-injected `CoffeeMaker`:
```java
public class CoffeeApp {
	public static void main(String[] args) {
		CoffeeShop coffeeShop = DaggerCoffeeShop.create();
		coffeeShop.maker().brew();
	}
}
```
