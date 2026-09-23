# Reading user input

## The behavior of user input

- We use the built-in `Scanner` class to read user input from the console
- The class provides the `nextLine` method, which blocks the code execution until users writes something to the console and presses the `Enter` key
- The text written by the user is returned by the `nextLine` method as a string and commonly stored to a variable

```java
// Scanner class is a built-in class, which we need to import to our program
import java.util.Scanner;

public class HelloProgram {
    public static void main(String[] args) {
        // Scanner is stored to the input variable
        Scanner input = new Scanner(System.in);

        System.out.print("Enter your name: ")
        // Read user input and store it to the name variable
        String name = input.nextLine();
        System.out.println("Hello " + name);
    }
}
```

## Execution order of the example

- When executing the previous example program, we see the printed message _"Enter your name:"_ in the console
- The execution is blocked to the line `String name = input.nextLine();`. This is because the program is waiting for the user input
- To continue the execution, we must write something to the console and press the `Enter` key. Providing the input will continue the program's execution and the `System.out.println("Hello " + name);` line is executed

```text
Enter your name: Kalle
Hello Kalle
```

## Reading multiple inputs

- The program can read multiple inputs from the user by having multiple `input.nextLine()` statements. Each statement will block the execution until the input is provided by the user

```java
Scanner input = new Scanner(System.in);

System.out.print("Enter your first name: ");
String firstName = input.nextLine();
System.out.print("Enter your surname: ");
String surname = input.nextLine();

System.out.println("Your full name is " + firstName + " " + surname);
```

```text
Enter your first name: Kalle
Enter your last name: Ilves
Your full name is Kalle Ilves
```

## Data type of the input

- The `input.nextLine()` will always provides the user's input as a string value
- We can transform the strings to e.g. integers or doubles using built-in `parseInt` and `parseDouble` methods

```java
Scanner input = new Scanner(System.in);

System.out.print("Enter your age: ");
String ageInput = input.nextLine();
System.out.print("Enter your salary: ")
String salaryInput = input.nextLine();

// Turn the value of ageInput string into the corresponding integer
int age = Integer.parseInt(ageInput);
// Turn the value of salaryInput string into the corresponding double
// Note that, the decimal separator should be "." in the input, not ","!
double salary = Double.parseDouble(salaryInput);
```

## Handling invalid input

- In the previous example, the user might provide a invalid age or salary, which will end up with an error

```text
Enter your age: twentyfour

Exception in thread "main" java.lang.NumberFormatException: For input string: "twentyfour"
at java.lang.NumberFormatException.forInputString(Unknown Source)
at java.lang.Integer.parseInt(Unknown Source)
at UserInputExample.main(UserInputExample.java:8)
```

- In this case, the `parseInt` method throws an `NumberFormatException`, causing the program to crash. This can be handled with a `try` and `catch` statements which we will cover later

## User input example

- Here is an example of a program, which calculates the body max index (BMI) based on the user's input

```java
// Import built-in Scanner and DecimalFormat
import java.util.Scanner;
import java.text.DecimalFormat;

public class BMICalculator {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        DecimalFormat twoDecimals = new DecimalFormat("0.00");

        System.out.print("Enter height (m): ");
        String heightInput = input.nextLine();

        System.out.print("Enter weight (kg): ");
        String weightInput = input.nextLine();

        // Turn the strings values to doubles in order to calculate the BMI
        double height = Double.parseDouble(heightInput);
        double weight = Double.parseDouble(weightInput);
        double bmi = weight / (height * height); // Or weight / Math.pow(height, 2)

        System.out.println("Your BMI is " + twoDecimals.format(bmi));
    }
}
```

```text
Enter height (m): 1.83
Enter weight (kg): 82
Your BMI is 24.49
```
