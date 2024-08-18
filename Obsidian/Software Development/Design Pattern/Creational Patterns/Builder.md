> Builder is a creational design pattern that lets you construct complex objects step-by-step. The pattern allows you to produce different types and representations of an object using the same construction code.

The Builder pattern suggests that you extract the object construction code out of its own class and move it to separate objects called "Builders".

Pros:
- You can construct objects step-by-step, defer construction steps or run steps recursively.
- You can reuse the same construction code when building various representations of products.
- [[Single Responsibility Principle (SRP)]] - You can isolate complex construction code from the business logic of the product.

Cons:
- The overall complexity of the code increases since the pattern requires creating multiple new classes.
## Applicability
You can use the pattern when:
- You want to get rid of a telescoping constructor, which is a long overloaded cases of constructors.
- You want your code to be able to create different representations of some product.
- You want to construct [[Composite]] trees or other complex objects.
## Structure
1. The Builder interface declares product construction steps that are common to all types of builders.
2. Concrete builders provide different implementations of the construction steps. Concrete builders may produce products that don't follow the common interface.
3. Products are resulting objects. Products constructed by different builders don't have to belong to the same class hierarchy or interface.
4. The Director class defines the order in which to call construction steps so you can create and reuse specific configurations of products.
5. The Client must associate one of the builder objects with the director. Usually, this is done just once via the parameters of the director's constructor. Then, the director uses that builder object for all further construction.
## Pseudocode
![[Pasted image 20240817220959.png]]
[Builder (refactoring.guru)](https://refactoring.guru/design-patterns/builder)

1. Make sure that you can clearly define the common construction steps for building all available product representations. 
2. Declare these steps in the base builder interface.
3. Create a concrete builder class for each of the product representations and implement their construction steps.
4. Think about creating a director class.
5. The client code creates both the builder and the director objects.
6. The construction result can be obtained directly from the director only if all products follow the same interface. Otherwise, the client should fetch the result from the builder.