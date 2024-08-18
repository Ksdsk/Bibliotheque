> Composite is a structural design pattern that lets you compose objects into tree structures and then work with these structures as if they were individual objects.

The composite pattern suggests that you work with the common hierarchical classes through a common interface which declares a method for recursively determining the properties of each classes. Obviously, using the composite pattern makes the best sense only when the core model of your application can be represented as a tree.
## Structure
![[Pasted image 20240818180758.png]]
1. The Component interface describes operations that are common to both simple and complex elements of the tree.
2. The Leaf is a basic element of a tree that doesn't have sub-elements. Usually, leaf components end up doing most of the real work, since they don't have anyone to delegate the work to.
3. The Container, or the Composite, is an element taht has sub-elements - leaves or other containers. A container doesn't know the concrete classes of its children. It works with all sub-elements only via the component interface.
   Upon receiving a request, a container delegates the work to its sub-elements, processes intermediate results, and then returns the final result to the client.
4. The Client works with all elements through the component interface. As a result, the client can work in the same way with both simple or complex elements of the tree.
## Pseudocode
![[Pasted image 20240818181747.png]]
```java
// The component interface declares common operations for both
// simple and complex objects of a composition.
interface Graphic is
    method move(x, y)
    method draw()

// The leaf class represents end objects of a composition. A
// leaf object can't have any sub-objects. Usually, it's leaf
// objects that do the actual work, while composite objects only
// delegate to their sub-components.
class Dot implements Graphic is
    field x, y

    constructor Dot(x, y) { ... }

    method move(x, y) is
        this.x += x, this.y += y

    method draw() is
        // Draw a dot at X and Y.

// All component classes can extend other components.
class Circle extends Dot is
    field radius

    constructor Circle(x, y, radius) { ... }

    method draw() is
        // Draw a circle at X and Y with radius R.

// The composite class represents complex components that may
// have children. Composite objects usually delegate the actual
// work to their children and then "sum up" the result.
class CompoundGraphic implements Graphic is
    field children: array of Graphic

    // A composite object can add or remove other components
    // (both simple or complex) to or from its child list.
    method add(child: Graphic) is
        // Add a child to the array of children.

    method remove(child: Graphic) is
        // Remove a child from the array of children.

    method move(x, y) is
        foreach (child in children) do
            child.move(x, y)

    // A composite executes its primary logic in a particular
    // way. It traverses recursively through all its children,
    // collecting and summing up their results. Since the
    // composite's children pass these calls to their own
    // children and so forth, the whole object tree is traversed
    // as a result.
    method draw() is
        // 1. For each child component:
        //     - Draw the component.
        //     - Update the bounding rectangle.
        // 2. Draw a dashed rectangle using the bounding
        // coordinates.

// The client code works with all the components via their base
// interface. This way the client code can support simple leaf
// components as well as complex composites.
class ImageEditor is
    field all: CompoundGraphic

    method load() is
        all = new CompoundGraphic()
        all.add(new Dot(1, 2))
        all.add(new Circle(5, 3, 10))
        // ...

    // Combine selected components into one complex composite
    // component.
    method groupSelected(components: array of Graphic) is
        group = new CompoundGraphic()
        foreach (component in components) do
            group.add(component)
            all.remove(component)
        all.add(group)
        // All components will be drawn.
        all.draw()
```
## Applicability
Use the Composite pattern when:
- When you have to implement a tree-like structure.
- When you want the client code to treat both simple and complex elements uniformly.
## How to Implement
1. Make sure that the core model of your app can be represented as a tree structure. Try to break it down into simple elements and containers. Remember that containers must be able to contain both simple elements and other containers.
2. Declare the component interface with a list of methods that make sense for both simple and complex components.
3. Create a leaf class to represent simple elements. A program may have multiple different leaf classes.
4. Create a container class to represent complex elements. In this class, provide an array field for storing references to sub-elements. The array must be able to store both leaves and containers, so make sure it's declared with the component interface type.
5. Finally, define the methods for adding and removal of child elements in the container.
## Pros and Cons
Pros:
- You can work with complex tree structures more conveniently - use [[Polymorphism]] and [[Recursion]] to your advantage.
- Promotes the [[Open Closed Principle (OCP)]]. You can introduce new element types into the app without breaking the existing code, which now works with the object tree.
Cons:
- It might be difficult to provide a common interface for classes whose functionality differs too much. In certain scenarios, you'd need to overgeneralize the component interface, making it harder to comprehend.
## Relations with Other Patterns
- You can use [[Builder]] when creating complex Composite trees because you can program its construction steps to work recursively.
- [[Chain of Responsibility]] is often used in conjunction with Composite. In this case, when a leaf component gets a request, it may pass it through the chain of all of the parent components down to the root of the object tree.
- You can use [[Iterator]] to traverse the tree.
- You can use [[Visitor]] pattern to execute an operation over an entire Composite tree.
- You can implement shared leaf nodes of the Composite tree as [[Flyweight]] to save some RAM.
- Composite and [[Decorator]] have similar structure diagrams since both rely on recursive composition to organize an open-ended number of objects.
- Designs that make heavy use of Composite and [[Decorator]] pattern can often benefit from using [[Prototype]].