# Methods

## What is a method?

- **A method** is a named block of code that is executed only when called
- A method performs a task and can optionally take parameters. Methods make code reusable: _"write once, use many times"_
- Methods are always defined inside a class. A method belongs either to a class or to an object, we will cover this later in the course material
- A method can take any number of parameters, including none. Parentheses are required both in the declaration and in the call, regardless of the number of parameters
- A method can simply perform an action, or it can also return a single value using a `return` statement. The data type of the returned value is specified in the method declaration

## Defining a method

```java
public static double calculateAverage(int[] numbers) {
    int sum = 0;
    for (int i : numbers) {
        sum += i;
    }
    return (double) sum / numbers.length;
}

public static void printHelloWorld() {
    System.out.println("Hello world");
}
```

- In this example, we define a `calculateAverage` method, which has a single, `numbers` **parameter**, which is an array of integers `int[]`
- The parameter will act similarly as a variable within the method, but the method itself doesn't define its value
- Before the method name, a `double` type is specified. That is the type of value that the method produces, for example the average of the parameter array
- The `return` statement ends the method and **sends a value back to the code that called it**. In this case the value after the `return` statement should be of type `double`
- If the method doesn't produce a value (doesn't have a `return` statement), the return type should be `void`, like in the `printHelloWorld` method

## Calling a method

- A **method call** tells a program to execute the code inside that method
- A method call can pass **arguments** to the method as input. These arguments provide values for the method's parameters
- If the method has a `return` statement, its value will be passed from the method to the code that calls it

```java
public static void main(String args[]) {
    int[] points = { 23, 33, 100, 42 };
    // average variable will have the value of the return statement
    double average = calculateAverage(points);
}

public static double calculateAverage(int[] numbers) {
    int sum = 0;
    for (int i : numbers) {
        sum += i;
    }
    return (double) sum / numbers.length;
}
```
