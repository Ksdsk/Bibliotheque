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
1. 

## Pros and Cons
Pros:
- Promotes the [[Single Responsibility Principle (SRP)]]. You can separate the interface or data conversion code from the primary business logic of the program.
- Promotes the [[Open Closed Principle (OCP)]]. You can introduce new types of adapters into the program without breaking the existing client code.

Cons:
- The overall complexity of the code increases because you need to introduce a set of new interfaces and classes. Sometimes, it can be simpler to change the service class so that it matches the rest of your code.
## Relations with Other Patterns
