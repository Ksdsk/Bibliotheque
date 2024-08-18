> Builder is a creational design pattern that lets you construct complex objects step-by-step. The pattern allows you to produce different types and representations of an object using the same construction code.

The Builder pattern suggests that you extract the object construction code out of its own class and move it to separate objects called "Builders".

Pros:
- You can construct objects step-by-step, defer construction steps or run steps recursively.
- You can reuse the same construction code when building various representations of products.
- [[Single Responsibility Principle (SRP)]] - You can isolate complex construction code from the business logic of the product.