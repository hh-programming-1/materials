# Methods

## What is a method?

- **A method** is a named block of code that is executed only when called
- A method performs a task and can optionally take parameters. Methods make code reusable: _"write once, use many times"_
- Methods are always declared inside a class and it belongs either to a class or to an object, we will cover this later in the course material
- A method can take any number of parameters, including none. Parentheses are required both in the declaration and in the call, regardless of the number of parameters
- A method can simply perform an action, or it can also **return a single value** using a `return` statement. The data type of the returned value is specified in the method declaration

## Declaring a method

```java
public static double calculateAverage(int[] numbers) {
    int sum = 0;
    for (int i : numbers) {
        sum += i;
    }
    return (double) sum / numbers.length;
}

public static void printHelloWorld() {
    // This method doesn't return anything (void)
    System.out.println("Hello world");
}
```

- In this example, we declare a `calculateAverage` method, which has a single, `numbers` **parameter**, which is an array of integers `int[]`
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
    // Calling the calculateAverage method executes the code inside the method
    // average variable's value will match the method's return value
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

## Calling methods of an object

- Previously we have seen that, for example `String` and `LocalDate` objects have built-in methods we can use
- Compared to the previous `calculateAverage` method, these methods are **bound to the object we are calling them on**
- For example, `name.length()` method call returns the length of the string object in the `name` variable
- Here, `calculateAverage` is a **static method** (`static` keyword at the beginning of the method), it belongs to the class itself and it is not bound to an object
- In constrast, `length` method in `name.length()` method call, is an **instance method**, it is bound to the object we call it on

```java
int[] points = { 23, 33, 100, 42 };
String name = "Kalle";
LocalDate birthday = LocalDate.parse("1993-01-19");

// parseInt is a static method in the Integer class
int number = Integer.parseInt("10");
// If the method is declared in the same class we use it,
// we don't need the class name prefix (e.g. Integer.someMethod())
double average = calculateAverage(points);
int nameLength = name.length();
int birthYear = birthday.getYear();
```

## Thinking in methods

- Programming becomes more simple when we divde a larger problem in smaller problems to be solved individually, _"divide and conquer"_
- Methods are these smaller problems, which are individually relatively easy to implement and together solve the bigger problem
- Let's consider how we can solve our previous example of calculating the sales comission using methods

> Write a program that asks for the selling price of an apartment and calculates the real estate agent's commission for the sale. The commission is 3.44% of the selling price, but at least €2,214.

## Divide the problem

- First, let's consider how we can divide the program logic to methods. The program consists of three main components, which are good method candidates:
  1. Reading the selling price from the user. We can implement a `double readSellingPrice()` method which reads the selling price and returns it as a double
  2. Calculating the comission. We can implement a `calculateSalesComission(double sellingPrice)` method, which returns the comissions based on a `sellingPrice` parameter
  3. Formatting the comission. We can implement a `String formatSalesComission(double comission)` method, which returns the comission as string in two decimal accuracy

```java
public class SalesComission {
    public static double readSellingPrice() {
        // TODO: ask user to enter the selling price and return it
    }

    public static double calculateSalesComission(double sellingPrice) {
        // TODO: return the comission based on the selling price
    }

    public static String formatSalesComission(double comission) {
        // TODO: return the sales comission with two decimal format
    }

    public static void main(String[] args) {
        double sellingPrice = readSellingPrice();
        double comission = calculateSalesComission(sellingPrice);

        System.out.println("The sales commission is " + formatSalesComission(commission));
    }
}
```

## Conquer the problem

- Once we have planned the methods we need, we implement the methods individually
- For example, the `calculateSalesComission` method **doesn't need to know how where the selling price comes from** (e.g. from the user input or somewhere else), which makes it highly reusable

```java
class SalesComission {
    public static double readSellingPrice() {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter selling price: ");
        double sellingPrice = Double.parseDouble(input.nextLine());
        return sellingPrice;
    }

    public static double calculateSalesComission(double sellingPrice) {
        double commissionRate = 0.0344; // 3.44%
        double minimumCommission = 2214.00;

        double commission = sellingPrice * commissionRate;

        if (commission < minimumCommission) {
            commission = minimumCommission;
        }

        return comission;
    }

    public static String formatSalesComission(double comission) {
        DecimalFormat twoDecimals = new DecimalFormat("0.00");
        return twoDecimals.format(commission);
    }

    public static void main(String[] args) {
        double sellingPrice = readSellingPrice();
        double comission = calculateSalesComission(sellingPrice);

        System.out.println("The sales commission is " + formatSalesComission(commission));
    }
}
```

## Method visibility

- The `public` keyword at the beginning of a method declaration specifies that the method **can be called from any class**, including classes outside the class in which it is declared
- In contrast, the `private` keyword specifies that the method **can only be called from within the same class in which it is declared**

```java
public class Calculator {
    // Public method, can be called from any class
    public static int sum(int a, int b) {
        return a + b;
    }

    // Private method, can only be called within this Calculator class
    private static secretOperation(int number) {
        return number - number;
    }
}
```

```java
public class CalculatorApp {
    public static void main(String[] args) {
        // We need to have the Calculator prefix, because the sum method is not defined in this class
        double result = Calculator.sum(2, 5);
        // THIS WON'T WORK, because secretOperation is a private method
        double secretResult = Calculator.secretOperation(6);
    }
}
```

## Same method name, different parameters

- It is possible to declare a method which accepts different parameters
- For example, the same method could accept different number of parameters or the type of the parameters are different
- This is called **method overloading**

```java
// This version of the greet method doesn't have any parameters
public static void greet() {
    System.out.println("Hello!");
}

// This version of the greet method has a single string parameter
public static void greet(String name) {
    System.out.println("Hello, " + name + "!");
}

public static void main(String[] args) {
    // This will call void greet()
    String genericGreeting = greet();
    // This will call void greet(String name)
    String namedGreeting = greet("Kalle");
}
```