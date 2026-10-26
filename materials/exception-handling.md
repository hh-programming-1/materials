# Exception handling

## Causes of exceptions

- Certain forbidden operations in a program make continuing the execution of the program impossible, causing it to crash
- Such operations are for example, dividing by zero or accessing an array element of out it bounds
- The internal implementation of these operations "throw" and **exception**, communicating the error and **forcing handling of the error or letting the program crash**

```java
int numberA = 10;
int numberB = 0;
int result = numberA / numberB;

System.out.println("Division: " + result);
System.out.println("Goodbye!");
```

```
Exception in thread "main" java.lang.ArithmeticException: / by zero
        at week1.HelloProgram.main(HelloProgram.java:7)
```

## Behavior of exceptions

```
Exception in thread "main" java.lang.ArithmeticException: / by zero
        at week1.HelloProgram.main(HelloProgram.java:7)
```

- In the previous exaple, diving by zero throws an `ArithmeticException` exception with an error message `/ by zero`, describing the problem
- This exception occurs at line 7 of the `HelloProgram.java` file containing `int result = numberA / numberB;`
- As we see, the program execution ends with this exception and, for example, the `Goodbye!` text is never printed

## Handling exceptions

- The default behavior of exception is that the program crashes and its execution ends
- We can alter this behavior by "catching" exceptions with a `try/catch` block
- With it, we execute code in a `try` block and if that code causes an exception, the execution goes to the `catch` block insteand of crashing the program

```java
int numberA = 10;
int numberB = 0;

try {
    // If code in this block throws and exception, we go to the catch block
    int result = numberA / numberB;
    System.out.println("Division: " + result);
} catch (Exception exception) {
    // Here we handle the exception
    System.out.println("That is forbidden: " + exception.getMessage());
}

System.out.println("Goodbye!");
```

```
That is forbidden: / by zero
Goodbye!
```

## Try/catch block

```java
try {
    int result = numberA / numberB;
    System.out.println("Division: " + result);
} catch (Exception exception) {
    System.out.println("That is forbidden: " + exception.getMessage());
}
```

- In this example, the code in the `try` block throw and exception, causing the execution of the `catch` block
- The `catch` block receives the thrown `Exception` object with details about the problem, for example, the error message

## Catching only specific kind of exceptions

- It is possible to specify what kind of exception we want to
  catch in the `catch` block
- Other type of exceptions will skip the catch block, causing the exception to propagate until it is catched or eventually crash the program if not

```java
try {
    int result = numberA / numberB;
    System.out.println("Division: " + result);
} catch (ArithmeticException exception) {
    // Only catch ArithmeticException exceptions
    System.out.println("That is not how arithmetics work: " + exception.getMessage());
}
```

## Catching multiple kind of exceptions

- A `try` block can be follow by **multiple** `catch` block, which will be matched by the thrown exception
- Only the first `catch` block that matches the thrown exception will be executed

```java
Scanner input = new Scanner(System.in);
int[] points = new int[10];

try {
    System.out.print("Enter index and points: ");
    int index = Integer.parseInt(input.nextLine());
    int value = Integer.parseInt(input.nextLine());
    points[index] = value;
} catch (NumberFormatException exception) {
    // Integer.parseInt throws a NumberFormatException with invalid integer
    System.out.println("Enter two numbers");
} catch (ArrayIndexOutOfBoundsException exception) {
    // Accessing index out of array bounds throws an ArrayIndexOutOfBoundsException exception
    System.out.println("Enter an index between 0 and " + (points.length -1));
}
```

```
Enter index and points: one
Enter two numbers
```

## Throwing an exception

- We can throw exceptions from our code by using the `throw` keyword followed by the exception object
- While throwing en exception, we provide a error message which should describe the problem which caused the exception
- Method that throws an exception should include the exception type in the declaration, e.g. `throws Exception`, or `throws IllegalArgumentException`

```java
// "throws Exception" indicates that the method throws a generic Exception object
public static int calculateGrade(int points) throws Exception {
    if (points <= 0) {
        // Throw a generic Exception object
        throw new Exception("Points should be at least 0");
        // More specific exception objects exist, e.g. for invalid arguments
        // throw new IllegalArgumentException("Points should be at least 0");
    }

    int grade = Math.round(points / 20);

    return grade;
}

public static void main(String[] args) {
    Scanner input = new Scanner(System.in);
    System.out.print("Enter points 0-100:");
    int points = Integer.parseInt(input.nextLine());

    try {
        int grade = calculateGrade(points);
        System.out.println("Grade: " + grade);
    } catch (Exception exception) {
        System.out.println("Error: " + exception.getMessage());
    }
}
```

```
Enter points 0-100: -2
Error: Points should be at least 0
```