> A class should have one and only one reason to change, meaning that a class should only have one job.

This principle gives us a few benefits:
- A class with one responsibility will have far fewer test cases.
- Less functionality in a single class will have fewer dependencies.
- Smaller, well-organized classes are easier to search than monolithic ones.
## Example
Here is a simple book class:
```java
public class Book {
	private String name;
	private String author;
	private String text;
	// Constructor, getters, and setters
}
```

Let's add a couple of methods to query the text:
```java
public class Book {
	private String name;
	private String author;
	private String text;
	// Constructor, getters, and setters
	// Methods that directly relate to the book properties
	public String replaceWordInText(String word, String replacementWord) {
		return text.replaceAll(word, replacementWord);
	} 

	public boolean isWordInText(String word) {
		return text.contains(word);
	}
}
```
