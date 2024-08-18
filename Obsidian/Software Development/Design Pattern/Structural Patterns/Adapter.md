> Adapter is a structural design pattern that allows objects with incompatible interfaces to collaborate.

It's a special object that converts the interface of one object so that another object can understand it. It works by wrapping one of the objects to hide the complexity of conversion happening behind the scenes. The wrapped object isn't even aware of the adapter. For example, you can wrap an object that operates in meters and kilometers with an adapter that converts all of the data to imperial units such as feet and miles.
## Structure
### Object Adapter
![[Pasted image 20240818170005.png]]
1. The client is a class that contains the existing business logic of the program.
2. The client interface describes a protocol that other classes must follow to be able to collaborate with the client code.
3. The service is some useful class. The client can't use this class directly because it has an incompatible interface.
4. The adapter is a class that's able to work with both the client and the service. It implements the client interface, while wrapping the service object. The adapter receives calls from the client via the client interface and translates them into calls to the wrapped service object in a format it can understand.

### Class Adapter
![[Pasted image 20240818170027.png]]
1. The class adapter does not need to wrap any objects because it inherits behaviours from both the client and the service. The adaptation happens within the overridden methods.
## Pseudocode
![[Pasted image 20240818170344.png]]
```java
// Say you have two classes with compatible interfaces:
// RoundHole and RoundPeg.
class RoundHole is
    constructor RoundHole(radius) { ... }

    method getRadius() is
        // Return the radius of the hole.

    method fits(peg: RoundPeg) is
        return this.getRadius() >= peg.getRadius()

class RoundPeg is
    constructor RoundPeg(radius) { ... }

    method getRadius() is
        // Return the radius of the peg.

// But there's an incompatible class: SquarePeg.
class SquarePeg is
    constructor SquarePeg(width) { ... }

    method getWidth() is
        // Return the square peg width.

// An adapter class lets you fit square pegs into round holes.
// It extends the RoundPeg class to let the adapter objects act
// as round pegs.
class SquarePegAdapter extends RoundPeg is
    // In reality, the adapter contains an instance of the
    // SquarePeg class.
    private field peg: SquarePeg

    constructor SquarePegAdapter(peg: SquarePeg) is
        this.peg = peg

    method getRadius() is
        // The adapter pretends that it's a round peg with a
        // radius that could fit the square peg that the adapter
        // actually wraps.
        return peg.getWidth() * Math.sqrt(2) / 2

// Somewhere in client code.
hole = new RoundHole(5)
rpeg = new RoundPeg(5)
hole.fits(rpeg) // true

small_sqpeg = new SquarePeg(5)
large_sqpeg = new SquarePeg(10)
hole.fits(small_sqpeg) // this won't compile (incompatible types)

small_sqpeg_adapter = new SquarePegAdapter(small_sqpeg)
large_sqpeg_adapter = new SquarePegAdapter(large_sqpeg)
hole.fits(small_sqpeg_adapter) // true
hole.fits(large_sqpeg_adapter) // false
```
## Applicability
Use the Adapter class when:
- When you want to use some existing class, but its interface isn't compatible with the rest of your code.
- When you want to reuse several existing subclasses that lack some common functionality that can't be added to the superclass.
## Pros and Cons
Pros:
- Promotes the [[Single Responsibility Principle (SRP)]]. You can separate the interface or data conversion code from the primary business logic of the program.
- Promotes the [[Open Closed Principle (OCP)]]. You can introduce new types of adapters into the program without breaking the existing client code.

Cons:
- The overall complexity of the code increases because you need to introduce a set of new interfaces and classes. Sometimes, it can be simpler to change the service class so that it matches the rest of your code.
## Relations with Other Patterns
- [[Bridge]] is usually designed up-front, letting you develop parts of an application independently of each other. On the other hand, Adapter is commonly used with an existing app to make some otherwise-incompatible classes work together nicely.
- Adapter provides a completely different interface for accessing an existing object. On the other hand, with the [[Decorator]] pattern, the interface either stays the same or gets extended.
- With Adapter, you access an existing object via different interface. With [[Proxy]], the interface stays the same. With [[Decorator]], you access the object via an enhanced interface.
- [[Facade]] defines a new interface for existing objects, whereas Adapter tries to make the existing interface usable; Adapter usually wraps just one object, Facade works with an entire subsystem of objects.
- [[Bridge]], [[State]], and [[Strategy]] have very similar structures. However, they solve different problems.