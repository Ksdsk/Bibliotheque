Debugging is the act of figuring out the difference between the expected and reality of the current code and then patching it. A program is called **stable** if it doesn't have a lot of obvious bugs. On the contrary, it is called **buggy** or **unstable** if the code has a large number of bugs that affect the functionality and cause incorrect results.

There are an infinite amount of ways a bugs can come to existence, but most commonly sprouted from:
- Communication issues in the team;
- Misunderstanding of the requirements;
- Software complexity;
- Programming errors;
- Use of unfamiliar technologies;
- An error in a third-party library.
## Avoiding Bugs
It's almost impossible to avoid all bugs in a large program, but it is possible to reduce their number. These are the five steps that can help you, as a developer, to help you avoid bugs:
1. Make sure you know what to do.
2. Decompose a program into smaller units.
3. Write easy-to-read code.
4. Run the program with boundary input values.
5. Write automated tests that will check the program at the build time.

Test automations are possible with debugging frameworks, such as JUnit for Java and PyTest for Python.
## Writing Tests
There are several tools and guidelines on how to make an effective test. A simple test to simply compare the values of the reality and the expectation is called an **assertion**. 

A good assertion should not include the implementation details in the tests. It should also test *only one thing per test*. However, following that rule may make testing pretty difficult because we are no longer sure if we can confidently *expect* the underlying implementation to behave correctly. This is when we can [[#Eliminating dependencies in tests|eliminate dependencies during testing]] to try to make sure our scopes are targeting the exact function we wish to test.
### Eliminating dependencies in tests
Your functions may require dependencies, whether it be a different function that returns a value or an external API call, these functions are irrelevant of the function behaviour we want to test and can be an anomaly during testing. One solution we can do is to try to inject a *pretend dependency* which acts like the actual dependency, but we can control what values will be returned. There are two main methods of pretending, which are the [[#Stubs]] and the [[#Mocks]].
#### Stubs
> A way to provide dummy info instead of making the calling to the actual thing.

Stubs allow you to create a dependency that will return a canned value for calls made during the test. These can be useful when the clients of the stubs expect the same set of responses, e.g. a third party service. Stubs should never fail a unit or integration test where a mock can. They should also not require any sort of framework to run, but usually are supported by mocking frameworks to quickly build a stub.
#### Mocks
> A way to mimic the real function, usually much more simplistic than the actual version.

Mocks are objects that entails *expectations* about a behaviour. For example, you might be interested if the function you're testing for is correctly calling an external function correctly, you'd be using a mock. If a mock receives an unexpected call, they will probably raise an exception! 
#### Spies
> Anything that can record what's happening inside your function during testing.

There are also a special injection called a **spy**. Anything that is injected which can log data can be described as a spy, which may be useful if you wanted to log the behaviours on top of mocking or stubbing them.