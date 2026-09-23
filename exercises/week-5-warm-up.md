# Arrays & Lists Warm-up Exercises

For this week's exercises, create a new `week5` package (folder) under the `src/main/java` folder. For each exercise, create an exercise-specific `.java` file in the `week5` folder.

```
src/
└── main/
    └── java/
        ├── ...
        └── week5/ 👈
            └── WarmUp1.java 👈
```

> [!IMPORTANT]
> **Warm-up exercises are not submitted or evaluated in Viope**. The purpose of these exercises is to practice the topics with the help of the model solutions.

## Warm-up exercise 1

Create an array containing numbers 2, 9, 5, 1, 7 and 4. Using a loop (no hardcoded solutions), find and print the largest number in the array.

## Warm-up exercise 2

Create an `ArrayList` containing the words "milk", "chips", "soda" and "hot dogs". Using a loop (no hardcoded solutions), find and print the longest word on the list.

## Warm-up exercise 3

Ask the user to enter an integer until they enter an empty string. Add the integers to an `ArrayList`. After the empty string is entered, print the even integers on the list.

Example:

```
Enter integer: 1
Enter integer: 9
Enter integer: 4
Enter integer:
Even integers:
1
4
```

> [!TIP]
> Read the user input in a `while` loop until the input is an empty string:
> 
> ```java
> while (true) {
>   String value = input.nextLine();
>   if (/* Condition to stop reading the input */) {
>     // End the while loop 
>     break;
>   } else {
>      // Do something with the input
>   }
> }
>
> System.out.println("Done!");
> ```

## Warm-up exercise 4

Ask the user to enter a word until the enter a empty string. Add the words to an `ArrayList`. After the empty string is entered, ask user to enter a word to search from the list. If the word is on the list, print "The word X is on the list", otherwise print "The word X is not on the list".

Example:

```
Enter word: milk
Enter word: chips
Enter word: candy
Enter word:
Search word: milk
The word milk is on the list
```