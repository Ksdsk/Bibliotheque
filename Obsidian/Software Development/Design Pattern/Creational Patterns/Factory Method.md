> Factory Method is a creational design pattern that provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created.

The **Factory Method** pattern suggests that you replace direct object construction calls (using the `new` operator) with calls to a special *factory* method. Well, the objects are still created via the `new` operator, but it's being called from within the factory method. Objects returned by a factory method are often referred to as *products*.

Pros:
- Avoid tight coupling between the creator and the concrete products
- Promotes the [[Single Responsibility Principle (SRP)]] - You can move the product creation code into one place in the program, making the code easier to support.
- Promotes the [[Open/Closed Principle (OCP)]] - You can introduce new types of products into the program without breaking existing client code.
Cons:
- The code may become more complicated since you need to introduc
## Applicability
When you don't know beforehand the exact types and dependencies of the objects your code should work with:
- The factory Method separates product construction code from the code that actually uses the product. Therefore, it's easier to extend the product construction code independently from the rest of the code.
- For example, to add a new product type to the app, you'll only need to create a new creator subclass and override the factory method in it.
## Structure
1. The **Product** declares the interface, which is common to all objects that can be produced by the creator and its subclasses.
2. **Concrete Products** are different implementations of the product interface.
3. The **Creator** class declares the factory method that returns new product objects. It's important that the return type of this method matches the product interface. 
   You can declare the factory method as `abstract` to force all subclasses to implement their own versions of the method. As an alternative, the base factory method can return some default product type.
4. **Concrete Creators** override the base factory method so it returns a different type of a product.
## Pseudocode
![[Pasted image 20240817120047.png]]
[Factory Method in Java / Design Patterns (refactoring.guru)](https://refactoring.guru/design-patterns/factory-method)
1. Make all products follow the same interface. The interface should declare methods that make sense in every product.
2. Add an empty factory method inside the creator class. The return type of the method should match the common interface.
3. In the creator's code, find all references to product constructors. One by one, replace them with calls to the factory method, while extracting the product creation code into the factory method.
4. Now, create a set of creator subclasses for each type of product listed in the factory method. Override the factory method in the subclasses and extract the appropriate bits of construction code from the base method.
5. If there are too many product types and it doesn't make sense to create subclasses for all of them, you can reuse the control parameter from the base class in subclasses.
6. If, after all of the extractions, the base factory method has become empty, you can make it abstract. If there's something left, you can make it a default behaviour of the method.