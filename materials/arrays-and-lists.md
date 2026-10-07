# Arrays and lists

## Storing multiple values

- In programming, we often encounter situations where we want to handle many values, e.g. storing all the grades of a course
- The only method we've used so far has been to define a separate variable for storing each value. This is impractical
- Programming languages offer **data structures**, which purpose is to store multiple values
- The most common such data structures in Java are **arrays** and **lists**

## Arrays

- An **array** is data structure for storing for storing multiple values in a single variable
- It contains a **limited amount of numbered spots** (indices) for values
- The length (or size) of an array is the amount of these spots, i.e. how many values can you place in the array
- The values in an array are called **elements**

```java
// Initialize an grades array that can store 10 integers
int[] grades = new int[10];
```

## Creating an array

$$
\underbrace{\texttt{int[]}}_{\text{array type}}
\quad
\underbrace{\texttt{grades}}_{\text{variable name}}
\quad
\underbrace{\texttt{=}}_{\text{assignment operator}}
\quad
\underbrace{\texttt{new int[10]}}_{\text{create an array of 10 integers}}
$$

- Array contains elements of a specific type. This type is specified when we define the type of the array before the `[]` brackets, e.g. `int[]`
- The array can **only contain elements of the specified type**
- The length of the array is fixed and it is defined when the array variable is initialized, e.g. `new int[10]`

```java
// Initialize a grades array that can store 10 integers
int[] grades = new int[10];
// Initialize a names array that can store 5 strings
String[] names = new String[5];
// Initialize a prices array can store 15 doubles
double[] prices = new double[5];
// We can also initialize an array with predefined elements
// The numbers array can store 4 integers with initial elements of 1, 2, 3 and 4
int[] numbers = {1, 2, 3, 4};
```

## Accessing the array elements

- An element of an array is referred to by its index. In the example below we create an Array to hold 3 integers, and then assign values to indices 0 and 2. After that we print the values
- Assigning a value to a specific spot of an array works much like assigning a value in a normal variable, but in the array you must specify the index within `[]` brackets, i.e. to which spot you want to assign the value

```java
int[] numbers = new int[3];
// The index is specified in square brackets
// Note that 0 is the first index!
numbers[0] = 2;
numbers[2] = 5;

// Print elements in array index 0 and 2
System.out.println(numbers[0]);
System.out.println(numbers[2]);
```

```
2
5
```

## Iterating an array

- We can find the size of the array through the associated variable `length`. We can access this associated variable by writing name of the array dot name of the variable, i.e. `numbers.length`
- We can iterate over the array, i.e. go through each element of the array with a `for` loop

```java
int[] numbers = new int[4];
numbers[0] = 42;
numbers[1] = 13;
numbers[2] = 12;
numbers[3] = 7;

System.out.println("The array has " + numbers.length + " elements");

// Iterate from the first index (0 index) to last index (3 index)
for (int i = 0; i < numbers.length; i++) {
    System.out.println(numbers[i]);
}
```

```
The array has 4 elements
42
13
12
7
```

## The boundaries of an array

- If the index is pointing outside the array, i.e. the element doesn't exist, we get an `ArrayIndexOutOfBoundsException` error
- This error tells, that the array doesn't contain the given index
- You cannot access outside of the array, i.e. index that's less than 0 or greater or equal to the size of the array

```java
int[] numbers = new int[4];
numbers[0] = 42;
numbers[1] = 13;
numbers[2] = 12;
numbers[3] = 7;
// Oops, we are assigning an element outside the boundaries of the array
// This will cause ArrayIndexOutOfBoundsException error and crash the program
numbers[4] = 7;
```

## 💡 Array example: shopping list

> Write a program which asks how many items there are on the shopping list. Then, the program asks to enter a shopping list item until all items are provided. Finally, the items should be printed.

```java
public static void main(String[] args) {
    Scanner input = new Scanner(System.in);

    System.out.print("How many items are on the shopping list?: ");
    int numberOfItems = Integer.parseInt(input.nextLine());
    // Initialize an array of strings of the given length
    String[] shoppingList = new String[numberOfItems];

    // Fill in the array elements based on user input
    // We use a for loop because we know how many inputs there will be
    for (int i = 0; i < shoppingList.length; i++) {
        System.out.print("Enter item: ");
        String item = input.nextLine();
        // Add the item to the next index on the array
        shoppingList[i] = item;
    }

    System.out.println("Shopping list:");
    // Once the items are in the array, we iterate the array to print the elements
    for (int i = 0; i < shoppingList.length; i++) {
        System.out.println(item[i]);
    }
}
```

```text
How many items are on the shopping list? 3
Enter item: Milk
Enter item: Bread
Enter item: Apples
Shopping list:
Milk
Bread
Apples
```

## Lists

- Similarly as arrays, `ArrayList` allows storing multiple values
- In contrast to an array, the size of an `ArrayList` is **not fixed** and it will automatically grow in size while elements are added
- `ArrayList` offers various **methods**, including ones for adding values to the list, removing values from it, and also for the retrieval of a value from a specific place in the list
- In general, `ArrayList` should preferred over an array when we need to store multiple values, but don't know the number of elements we are storing

## Creating a list

$$
\underbrace{\texttt{ArrayList\<String\>}}_{\text{list type}}
\quad
\underbrace{\texttt{names}}_{\text{variable name}}
\quad
\underbrace{\texttt{=}}_{\text{assignment operator}}
\quad
\underbrace{\texttt{new ArrayList\<\>()}}_{\text{create an empty list}}
$$

- For an `ArrayList` to be used, it first needs be imported into the program. This is achieved by including the command `import java.util.ArrayList;` at the top of the program
- Creating a new list is done with the command `ArrayList<Type> list = new ArrayList<>()`, where `Type` is the type of the values to be stored in the list (e.g. `String`)
- All the elements stored in a given list are of the same type

```java
// Import the ArrayList so the program can use it
import java.util.ArrayList;

public class ListExample {
    public static void main(String[] args) {
        // Create a names list, which doesn't have any elements yet
        ArrayList<String> names = new ArrayList<>();
        // Create a seasons list with predefined elements
        ArrayList<String> seasons = List.of("Winter", "Spring", "Summer", "Autumn");
    }
}
```

## Defining the type of elements that a list contains

- When defining the type of values that a list can include, the first letter of the element type has to be capitalized
- A list that includes int-type variables has to be defined in the form `ArrayList<Integer>` and a list that includes double-type variables is defined in the form `ArrayList<Double>`
- The reason for this has to do with how the `ArrayList` is implemented. Variables in Java can be divided into two categories: **value type (primitive)** and **reference type variables**
- Value-type variables such as `int` or `double` hold their actual values
- Reference-type variables such as `ArrayList`, in contrast, contain a reference to the location that contains the value(s) relating to that variable

```java
// Create a names list of strings and add a string element to the list
ArrayList<String> names = new ArrayList<>();
names.add("Kalle");

// Create a grades list of integers and add a integer element to the list
ArrayList<Integer> grades = new ArrayList<>();
grades.add(5);

// Create a prices list of doubles and add a double element to the list
ArrayList<Double> prices = new ArrayList<>();
prices.add(1.5);
```

## Accessing the list elements

- Adding elements to a list is done with the list method `add`, which takes the value to be added as a parameter
- Similarly as with arrays, list elements are stored to a specific index, **first index being zero**
- To retrieve a value from a certain index, we use the list method `get`, which is given the index of retrieval as a parameter
- If we try to retrieve information from a index that does not exist on the list, we will get an `IndexOutOfBoundsException` error

```java
// Create the word list for storing strings
ArrayList<String> wordList = new ArrayList<>();

// Add two values to the word list
wordList.add("First"); // "First" is stored to index 0
wordList.add("Second"); // "Second" is stored to index 1

// Print elements in list index 0 and 1
System.out.println(wordList.get(0));
System.out.println(wordList.get(1));
```

```
First
Second
```

## Iterating a list

- The size of a list can be obtained using the `size` method, e.g. `wordList.size()`
- We can go through the elements of a list the same way as an array using a `for` loop

```java
ArrayList<String> wordList = new ArrayList<>();

wordList.add("First");
wordList.add("Second");
wordList.add("Third");

System.out.println("The list has " + wordList.size() + " elements");

// Iterate from the first index (0 index) to last index (2 index)
for (int i = 0; i < wordList.size(); i++) {
    System.out.println(wordList.get(i));
}
```

```
The list has 3 elements
First
Second
Third
```

## The for each loop

- Lists and arrays can be iterated using a more convenient type of loop called the **for-each loop**
- The for-each loop specifies the variable that stores the current element and the list or array to iterate over, using the syntax `for (Integer grade : grades)`
- In the following example, `grades` is the list we are iterating over. During each iteration, the `grade` variable is assigned the next element in the list

```java
ArrayList<Integer> grades = new ArrayList<>();
grades.add(5);
grades.add(3);
grades.add(2);

// The grades is the list we are iterating and grade is the next element on the list
// The type of variable must match the type of list's elements. We can choose the name of this variable freely
for (Integer grade : grades) {
    System.out.println(grade);
}
```

```
5
3
2
```

## 💡 List example: total price

> Write a program which asks for a price until an empty string "" is entered. After the empty string, the program should print the total sum of the prices.

```java
// Import ArrayList so that we can initialize a list
import java.util.ArrayList;
import java.util.Scanner;

public class TotalPrice {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        // Initialize a list of doubles, note the Double as the element type
        ArrayList<Double> prices = new ArrayList<>();

        // Read user input in a while loop
        // We use a while loop, because we don't know how many user inputs there will be
        while (true) {
            System.out.print("Enter a price: ");
            String price = input.nextLine();

            // Empty input string will break the loop
            if (price.isEmpty()) {
                break;
            }

            // Add a non-empty price to the list
            prices.add(Double.parseDouble(price));
        }

        double sum = 0;

        // Once the prices are on the list, we iterate the list to count the sum
        for (Double price : prices) {
            sum += price;
        }

        System.out.println("Total price: " + sum)
    }
}
```

```text
Enter a price: 1.5
Enter a price: 4
Enter a price: 3.5
Enter a price:
Total price: 9.0
```
