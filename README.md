Assignment – 11 : (Please click on the code tab to view in the Programming code format)
1. What are the four access modifiers available in Java and what is their significance in
terms of class, method, and variable accessibility?
In Java, the four access modifiers that control the visibility and accessibility of classes, methods, and variables are:

1)Public:
Classes: A public class is accessible from any other class.
Methods and Variables: Public methods and variables can be accessed from any other class.
Significance: This modifier allows for the widest possible access. When a class, method, or variable is declared as public, it can be accessed from any other part of the program.

2)Protected:

Classes: The protected modifier cannot be applied to top-level classes. However, it can be used with nested classes.
Methods and Variables: Protected methods and variables are accessible within the same package and by subclasses (even if they are in different packages).
Significance: This modifier is useful for allowing access within the same package and in subclasses, promoting inheritance and reuse while still restricting access somewhat.

3)Default (Package-Private):

Classes: A class with no access modifier is accessible only within its own package.
Methods and Variables: Methods and variables with no access modifier are accessible only within their own package.
Significance: This modifier (or lack thereof) restricts access to the package level, providing a moderate level of encapsulation by limiting access to within the same package.

4)Private:

Classes: The private modifier cannot be applied to top-level classes. It can be used with nested classes.
Methods and Variables: Private methods and variables are accessible only within the same class.
Significance: This modifier provides the most restrictive access, ensuring that methods and variables are encapsulated within the class and not accessible from outside. This is key for maintaining encapsulation and hiding implementation details.
Example:

public class PublicClass {
    public void publicMethod() {
        System.out.println("Public method");
    }
}


public class ParentClass {
    protected void protectedMethod() {
        System.out.println("Protected method");
    }
}

public class ChildClass extends ParentClass {
    public void someMethod() {
        protectedMethod(); // Accessible due to inheritance
    }
}

class DefaultClass {
    void defaultMethod() {
        System.out.println("Default method");
    }
}


public class PrivateExample {
    private void privateMethod() {
        System.out.println("Private method");
    }

    public void accessPrivateMethod() {
        privateMethod(); // Accessible within the same class
    }
}


2. What is the difference between Exception and error?
Exception:
o	It is an event that occurs during the execution of the program and interrupts the normal flow of program instructions. These are the errors that occur at compile time and run time. It occurs in the code written by the developers. It can be recovered by using the try-catch block and throws keyword. There are two types of exceptions i.e. checked and unchecked. Any exception that is thrown must be caught by the exception handler.

Types:
In Java, there are two types of exceptions:
1.	Checked exceptions: These are the exceptions that are checked at compile time. Example: IOException, File not found exception
2.	Unchecked exceptions: Example: ArrayIndexOutOfBoundsException (This exception is thrown when we attempt to access an array index that is out of bounds.), NullPointerException (This exception is thrown when we attempt to access a null object reference.), ArithmeticException (This exception is thrown when we attempt to divide by zero or perform an invalid arithmetic operation.)
Error:
Errors are typically caused by mistakes in the program’s code or by external factors such as hardware or network issues. 
Example: a)syntax errors- Syntax errors occur when the program’s code violates the rules of the programming language. 
b)runtime errors- Runtime errors occur when the program tries to execute an invalid operation or encounters an unexpected situation, c)logical errors - Logical errors occur when the program produces incorrect results due to a flaw in the program’s design or implementation.

3. What is the difference between checked Exception and unchecked Exception?
Checked Exceptions
•	They occur at compile time.
•	The compiler checks for a checked exception.
•	These exceptions can be handled at the compilation time.
•	It is a sub-class of the exception class.
•	The JVM requires that the exception be caught and handled.
•	Example of Checked exception- ‘File Not Found Exception’
Unchecked Exceptions
•	These exceptions occur at runtime.
•	The compiler doesn’t check for these kinds of exceptions.
•	These kinds of exceptions can’t be caught or handled during compilation time.
•	This is because the exceptions are generated due to the mistakes in the program.
•	These are not a part of the ‘Exception’ class since they are runtime exceptions.
•	The JVM doesn’t require the exception to be caught and handled.
•	Example of Unchecked Exceptions- ‘No Such Element Exception’

4. Write a Java program that reads user input for two integers and performs division. Handle
the exception that is thrown when the second number is zero, and display an error
message to the user.
Program:
public class ArithmeticException {

	public static void main(String[] args) {
		int a= 100;
		int b = 0;
		try {
		int c = a / b;
		
		System.out.println("Result : " + c);
		
	}catch (Exception ae) {
		System.out.println("cannot divide by zero");

	}
	}
}

Output error message: Exception in thread "main" java.lang.ArithmeticException: / by zero
	at javapackage.ArithmeticException.main(ArithmeticException.java:9)
package javapackage;
Output after try and catch: cannot divide by zero

5. Write the code of ArrayIndexOutOfBoundsException & StringIndexOutOfBoundsException?
ArrayIndexOutOfBoundsException:
package javapackage;

public class ArrayIndexoutofboundException {

	public static void main(String[] args) {
		int a[] = new int [10];
		try 
		{
			a[10] = 20;
			
		}
		catch (Exception e) {
        	e.printStackTrace();
	}
System.out.println("Exception Done");
}
}
Output java.lang.ArrayIndexOutOfBoundsException: Index 10 out of bounds for length 10
	at javapackage.ArrayIndexoutofboundException.main(ArrayIndexoutofboundException.java:9)
Exception Done

StringIndexOutOfBoundsException:

package javapackage;

public class Stringindexoutofbound {

	public static void main(String[] args) {
		
		String str = "Peace";
		
		System.out.println(str.charAt(5));
		
		
	}

}
Output: Exception in thread "main" java.lang.StringIndexOutOfBoundsException: String index out of range: 5
	at java.base/java.lang.StringLatin1.charAt(StringLatin1.java:48)
	at java.base/java.lang.String.charAt(String.java:711)
	at javapackage.Stringindexoutofbound.main(Stringindexoutofbound.java:9)
 
6. You are building a login system for a website using Java. If the user enters an incorrect password, you want to display a message informing them of the error. How would you use exception handling to handle this situation?
package javapackage;

public class IncorrectPasswordException extends Exception {
    public IncorrectPasswordException(String message) {
        super(message);
    }
}

package javapackage;

public class WebsiteLoginController {
    public static void main(String[] args) {
        WebsiteLoginService loginService = new WebsiteLoginService();
        String username = "user"; // example username
        String password = "guvi"; // example user input

        try {
            loginService.login(username, password);
        } catch (IncorrectPasswordException e) {
            // Handle the incorrect password scenario
            System.out.println(e.getMessage());
        }
    }
}



package javapackage;

public class WebsiteLoginService {
    private static final String CORRECT_PASSWORD = "guvi"; // example correct password

    public void login(String username, String password) throws IncorrectPasswordException {
        if (!password.equals(CORRECT_PASSWORD)) {
            throw new IncorrectPasswordException("Incorrect password. Please try again.");
        }
        // Proceed with the login process if the password is correct
        System.out.println("Login successful!");
    }
}


Output: Login successful!

7. Create a custom exception in Java called "InvalidAgeException" that is thrown when the user enters an age less than 18. Implement exception handling in a Java program to catch the "InvalidAgeException" and display an error message.
package javapackage;
public class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);
    }
}

package javapackage;

import java.util.Scanner;

public class AgeValidator {
    
    // Method to check age and throw InvalidAgeException if age < 18
    public void checkAge(int age) throws InvalidAgeException {
        if (age < 18) {
            throw new InvalidAgeException("Age must be 18 or older.");
        }
        System.out.println("Age is valid.");
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        AgeValidator ageValidator = new AgeValidator();

        System.out.print("Enter your age: ");
        int age = scanner.nextInt();

        try {
            ageValidator.checkAge(age);
        } catch (InvalidAgeException e) {
            System.out.println("InvalidAgeException caught: " + e.getMessage());
        }

        scanner.close();
    }

}
Output: Enter your age: 19
Age is valid.

8. Implement exception handling in a Java program that reads data from a file. If the file does not exist, throw a "FileNotFoundException" and display an error message to the user.
package javapackage;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;

public class Filenotfoundexception {

	public static void main(String[] args) throws FileNotFoundException {
		
		File file = new File ("C:\\Users\\mouri\\OneDrive\\Desktop\\File"); //After deleting the created file
		
		
			FileReader fr = new FileReader(file);
			
		
	}

}

Output :

Exception in thread "main" java.io.FileNotFoundException: C:\Users\mouri\OneDrive\Desktop\File (The system cannot find the file specified)
	at java.base/java.io.FileInputStream.open0(Native Method)
	at java.base/java.io.FileInputStream.open(FileInputStream.java:211)
	at java.base/java.io.FileInputStream.<init>(FileInputStream.java:153)
	at java.base/java.io.FileReader.<init>(FileReader.java:75)
	at javapackage.Filenotfoundexception.main(Filenotfoundexception.java:14)
