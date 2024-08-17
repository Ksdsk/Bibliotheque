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

The book class works well, and we can store as many books as we'd like in our application. Let's try adding a print method to a book:
```java
public class BadBook {
	//  ...
	void printTextToConsole() {
		// Code for formatting and printing the text
	}
}
```
However, this code violates the SRP we outlined earlier.

To fix the mess, we should implement a separate class that deals with only printing our texts:
```java
public class BookPrinter {
	// Methods for printing text
	void printTextToConsole(String text) {
		// ...
	}

	void printTextToAnotherMedium(String text) {
		// ...
	}
}
```
... relieving the `Book` class of its printing duties, but we can also leverage our `BookPrinter` class to send our text to other media.
