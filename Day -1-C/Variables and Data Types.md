# 03-Basics → Variables

> **File:** `01-Basics/03-Variables/README.md`

Your notes are **good for the Variables topic**, especially for a beginner. A few technical points should be corrected/clarified before you keep them as your final `03-Variables` notes.

## Important Corrections

| Topic           | Your version                                | Better / precise version                                                                                                                                   |
| --------------- | ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Variable        | Named memory location used to store a value | A **named object** that has a type and can hold a value.                                                                                                   |
| Declaration     | `int age;`                                  | Declares `age` as an `int`; its value is **indeterminate** if it is a local automatic variable and hasn't been initialized.                                |
| Assignment      | `age = 21;`                                 | Stores a new value in an already-declared variable.                                                                                                        |
| Initialization  | `int age = 21;`                             | Gives the object its **initial value at the time of definition**.                                                                                          |
| `float`         | `float height = 5.8;`                       | Prefer `float height = 5.8f;` because `5.8` is a `double` literal converted to `float`.                                                                    |
| `double printf` | `%lf`                                       | For `printf`, `%f` is the correct conversion for `double`. `%lf` is accepted by some implementations, but don't teach it as the normal `printf` specifier. |
| `double scanf`  | `%lf`                                       | Correct: `%lf` is used with `scanf` for `double`.                                                                                                          |
| `sizeof`        | Size of a type/object                       | Correct. Result type is `size_t`, so `%zu` is appropriate.                                                                                                 |
| `char`          | Stores a single character                   | Correct. A `char` object stores a character value; character constants such as `'A'` have type `int` in C.                                                 |
| `const`         | Make an object non-modifiable               | Better: `const` makes the object **not modifiable through that lvalue/identifier**.                                                                        |
| Variable memory | "Memory location"                           | Fine as a beginner analogy, but technically C variables are **objects**, not simply memory boxes.                                                          |

## Format Specifiers You Should Remember

| Type     | Declaration     | `printf` | `scanf` | Example       |
| -------- | --------------- | -------- | ------- | ------------- |
| `int`    | `int age;`      | `%d`     | `%d`    | `21`          |
| `float`  | `float height;` | `%f`     | `%f`    | `5.8f`        |
| `double` | `double pi;`    | `%f`     | `%lf`   | `3.14159`     |
| `char`   | `char grade;`   | `%c`     | `%c`    | `'A'`         |
| `size_t` | `size_t size;`  | `%zu`    | —       | `sizeof(int)` |

## One Correction to Your Complete Example

This is better:

```c
#include <stdio.h>

int main()
{
    int age = 21;
    float height = 5.8f;
    double percentage = 85.75;
    char grade = 'A';

    printf("Age: %d\n", age);
    printf("Height: %.1f\n", height);
    printf("Percentage: %.2f\n", percentage);
    printf("Grade: %c\n", grade);

    return 0;
}
```

## Practice Order

Do these **without copying the solution**:

| #  | Practice                                                  | Main concept                     |
| -- | --------------------------------------------------------- | -------------------------------- |
| 1  | Student Information                                       | Variables + different data types |
| 2  | Rectangle Area                                            | Variables + arithmetic           |
| 3  | Salary                                                    | `float`/`double`                 |
| 4  | Celsius → Fahrenheit                                      | Variables + formula              |
| 5  | `sizeof()`                                                | Data type sizes                  |
| 6  | Change `age` from 20 → 21                                 | Assignment                       |
| 7  | Store two integers and print their sum                    | `int` + operators                |
| 8  | Store marks of 3 subjects and calculate total             | Multiple variables               |
| 9  | Store price and quantity, calculate total                 | `float` + `int`                  |
| 10 | Store name, age, marks, grade and print a student profile | Combining everything             |

