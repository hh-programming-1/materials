# Exam and assessment

The final exam consists of the similar programming exercises as in the weekly exercises. The only way to prepare for the exam is by actual programming, that is working on the weekly exercises and perhaps redoing some of them for a recap.

The "Exam and assessment" page on Moodle has an example of a exam. It is highly recommended to complete it before the actual exam.

## Assessment

The final grade consists of the weekly exercise points and the exam points. Both points have the weight in the assessment and the final grade is calculated as the rounded average of the exercise grade (0-5) and exam grade (0-5).

The exercise grade (0-5) is calculated from the weekly exercise points in the following way:

| % of exercise points | Exercise grade |
| -------------------- | -------------- |
| 0% - 39%             | 0              |
| 40% - 51%            | 1              |
| 52% - 63%            | 2              |
| 64% - 75%            | 3              |
| 76% - 87%            | 4              |
| 88% - 100%           | 5              |

The exam grade (0-5) is calculated from the exam points in the following way:

| % of exam points | Exam grade |
| ---------------- | ---------- |
| 0% - 29%         | 0          |
| 30% - 43%        | 1          |
| 44% - 57%        | 2          |
| 58% - 71%        | 3          |
| 72% - 85%        | 4          |
| 86% - 100%       | 5          |

Passing grade from both is required for a passing final grade.

```java
if (exerciseGrade == 0 || examGrade == 0) {
    System.out.prinln("Your final grade is 0");
} else {
    int finalGrade = Math.round((exerciseGrade + examGrade) / 2);
    System.out.println("Your final grade is " + finalGrade);
}
```
