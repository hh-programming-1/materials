# Getting started with Viope

During this course, the programming exercises are submitted and automatically evaluated in the Viope platform. Follow these instructions to get started with Viope.

## Submitting exercises to Viope

> [!IMPORTANT]
> Solving problems in VS Code is much easier than in Viope. That is why, **always write your program in VS Code and make sure that your program seems to be working correctly**.

Once your solution works in VS Code, submit it to Viope by following these steps:

1. [Log in to Viope](https://vw4.viope.com/login?org=hh) and select the desired course.
2. Click on "Table of contents".
3. Select the desired chapter of exercises from the list.
4. Select the desired programming exercise in the chapter.
5. Copy/paste your code from VS Code to Viope's code editor.
   - The name of your Java class must be exactly what is required in the task description.
   - In Viope, remove the package directive on the `.java` file's first line (e.g. `package week1;`) from your code (see the example below).
6. Save your code by clicking on "Save".
7. Test your code by clicking on "Run".
   - Your program passes the tests only if its output matches to the expected output.
   - Please notice that in some exercises the matching is 100% strict.
8. If your code passes Viope check, then Viope shows the "Submit" button and you can submit your code by clicking the "Submit" button.

```diff
- package week1;

public class Exercise1 {
    public static void main(String[] args) {
        // ...
    }
}
```
