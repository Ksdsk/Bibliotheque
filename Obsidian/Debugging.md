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

A good assertion should not include the implementation details in the tests. However, following that rule may make testing pretty difficult because we are no longer sure if we can confidently 