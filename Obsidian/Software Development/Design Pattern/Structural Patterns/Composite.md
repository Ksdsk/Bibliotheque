> Composite is a structural design pattern that lets you compose objects into tree structures and then work with these structures as if they were individual objects.

The composite pattern suggests that you work with the common hierarchical classes through a common interface which declares a method for recursively determining the properties of each classes. Obviously, using the composite pattern makes the best sense only when the core model of your application can be represented as a tree.
## Structure
![[Pasted image 20240818180758.png]]
1. The Component interface describes operations that are common to both simple and complex elements of the tree.
2. The Leaf is a basic element of a tree that doesn't have sub-elements. Usually, leaf components end up doing most of the real work, since they don't have anyone to delegate the work to.
3. The Container, or the Composite, is an element taht has sub-elements - leaves or other containers. A container doesn't know the concrete classes of its children. It works with all sub-elements only via the component interface.
   Upon receiving a request, a container delegates the work to its sub-elements, processes intermediate results, and then returns the final result to the client.
4. The Client works with all elements through the component interface. As a result, the client can work in the same way with both simple or complex elements of the tree.