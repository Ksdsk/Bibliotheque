> Factory Method is a creational design pattern that provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created.

The **Factory Method** pattern suggests that you replace direct object construction calls (using the `new` operator) with calls to a special *factory* method. Well, the objects are still created via the `new` operator, but it's being called from within the factory method. Objects returned by a factory method are often referred to as *products*.
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
