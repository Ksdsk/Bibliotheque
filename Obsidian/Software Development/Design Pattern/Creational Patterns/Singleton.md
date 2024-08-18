> Singleton is a creational design pattern that lets you ensure that a class has only one instance, while providing a global access point to this instance.

All implementations of the Singleton have these two steps in common:
1. Make the default constructor private, to prevent other objects from using the `new` operator with the Singleton class.
2. Create a static creation method that acts as a constructor.

Pros:
- You can be sure that a class has only a single instance.
- You gain a global access point to that instance.
- The singleton object is initialized only when it's requested for the first time.

Cons:
- Violates the [[Single Responsibility Principle (SRP)]].
- The Singleton pattern can mask bad design, for instance, when the components of the program know too much about each other.
- The pattern requires special treatment in a multit