> Prototype is a creational design pattern that lets you copy existing objects without making your code dependent on their classes.

The prototype pattern delegates the cloning process to the actual objects that are being cloned. The pattern declares a common interface for all objects that support cloning. This interface lets you clone an object without coupling your code to the class of that object. Usually, such an interface contains just a single `clone` method.

An object that supports cloning is called a *prototype*. When your objects have dozens of fields and hundreds of possible configurations, cloning them might serve as an alternative to subclassing.

Pros:
- You can clone objects without coupling to their concrete classes.
- You can get rid of repeated initialization code in favour of cloning pre-built prototypes.
- You can produce complex objects more conveniently.
- You get an alternative to inheritance when dealing with configuration presents for complex objects.

Cons:
- Cloning complex objects that have circular references might be very tricky.