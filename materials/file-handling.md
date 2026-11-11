# File handling

## The purpose of file handling

- A considerable amount of software is in one way or another based on handling data
- Applications that run on the internet and mobile devices, such as Instagram, WhatsApp, and Discord, handle user information that is stored in file-based databases
- What these all have in common is that they read and manipulate data in one way or another. Also, the data being handled is ultimately stored in some format in one or more files

## The operations on files

- Files are collections of data that live in computers. These files can contain, among other things, text, images, music, or any combination of these
- The main benefit of files is that they provide **persistent storage**, allowing data to remain available even after the computer is restarted or turned off
- The most common operations that applications need to perform on files are **reading data from a file** and **writing data into a file**
- Java, as well as many other programming languages, offer built-in functionality for such operations

## Paths to files

- To access a file, we need to tell Java where it is located. This location is called a **path**
- Java represents paths with the `Path` interface from the `java.nio.file` package. A path can be created with the `Path.of` method
- A **relative** path, such as `grades.txt`, is resolved from the folder where the program is run. An **absolute** path, such as `C:/Users/Kalle/grades.txt`, points to the exact location
- The folders are separated with the forward backslash `/` in the path

```java
import java.nio.file.Path;

Path relativePath = Path.of("grades.txt");
Path absolutePath = Path.of("C:/Users/Kalle/grades.txt");
```

## Checked exceptions in file handling

- Most file operations can fail, for example when the file does not exist or the program does not have permission to access it. Java forces us to handle these failures with the `IOException` exception type (or its subtype `FileNotFoundException`)
- The methods in this material throw `IOException`, so the code is wrapped in a `try/catch` block

```java
try {
    // File operations go here
} catch (IOException exception) {
    System.out.println("File error: " + exception.getMessage());
}
```

## Reading from a file

- If the data on a file (e.g. course grades) are on separate lines, we can use the `Files.readAllLines` method to **return the lines of a file as a list of strings**
- Optionally, we can read the whole file as a string using the `Files.readString` method
- Let's assume that we are reading a `grades.txt` file with the course grades on seperate lines as below

```
1
4
3
5
5
```

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.List;

Path gradesPath = Path.of("grades.txt");

try {
    List<String> lines = Files.readAllLines(gradesPath);
    for (String line : lines) {
        System.out.println("Grade: " + line);
    }
} catch (IOException exception) {
    System.out.println("Could not read file: " + exception.getMessage());
}
```

## Writing to a file

- The `Files.writeString` method writes a string to a file
- If the file does not exist, it is created. If the file already exists, **its previous content is replaced**

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

Path path = Path.of("greeting.txt");

try {
    Files.writeString(path, "Hello from Java!");
} catch (IOException exception) {
    System.out.println("Could not write file: " + exception.getMessage());
}
```

## Appending text to a file

- To add text to the end of an existing file without removing its content, we give the `StandardOpenOption.APPEND` option to the method
- The `System.lineSeparator()` method returns the line break for the operating system, so each appended entry starts on a new line

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.StandardOpenOption;

Path path = Path.of("grades.txt");

try {
    Files.writeString(
        path,
        // Append a new line "4" to the file
        "4" + System.lineSeparator(),
        StandardOpenOption.CREATE,
        StandardOpenOption.APPEND
    );
} catch (IOException exception) {
    System.out.println("Could not write file: " + exception.getMessage());
}
```

## CSV files

- CSV (Comma-Separated Values) is a simple text-based file format used to store tabular data, such as information normally represented in a spreadsheet or database table
- For example, a `grades.csv` CSV file could contain lines of data of students' grades in format `student number,name,grade`
- Data from a CSV file can be transformed into the applications object's such as `Student`

```
1234,John Doe,5
5678,Mary Watson,3
5432,Steve Smith,4
```

```java
for (String line : lines) {
    // Get comma seprated values on the line as an array 
    String[] parts = line.split(",");
    // In "1234,John Doe,5", the first comma separated value is the student number
    String studentNumber = parts[0];
    String name = parts[1];
    int grade = Integer.parseInt(parts[2]);

    Student = new Student(studentNumber, name, grade);
}
```