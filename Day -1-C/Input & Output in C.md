# Day 1 → Topic 3: Input & Output in C

This topic covers **`printf()` and `scanf()`**, format specifiers, taking user input, and common input mistakes.

## 1. Output — `printf()`

`printf()` is used to display output on the screen.

```c
#include <stdio.h>

int main()
{
    printf("Hello World");

    return 0;
}
```

Output:

```text
Hello World
```

---

## 2. Printing Variables

| Data Type | Variable                    | `printf()` Specifier |
| --------- | --------------------------- | -------------------- |
| `int`     | `int age = 21;`             | `%d`                 |
| `float`   | `float price = 10.5f;`      | `%f`                 |
| `double`  | `double pi = 3.14159;`      | `%f`                 |
| `char`    | `char grade = 'A';`         | `%c`                 |
| String    | `char name[] = "Gajanand";` | `%s`                 |

Example:

```c
#include <stdio.h>

int main()
{
    int age = 21;
    float height = 5.8f;
    char grade = 'A';

    printf("Age: %d\n", age);
    printf("Height: %.1f\n", height);
    printf("Grade: %c\n", grade);

    return 0;
}
```

---

# 3. What is a Format Specifier?

A format specifier tells `printf()` or `scanf()` what type of data is being processed.

```text
%d  → int
%f  → float
%c  → char
%s  → string
```

Example:

```c
int age = 21;

printf("%d", age);
```

Here `%d` is replaced by the value of `age`.

---

# 4. New Line — `\n`

```c
printf("Hello\nWorld");
```

Output:

```text
Hello
World
```

Without `\n`:

```c
printf("Hello");
printf("World");
```

Output:

```text
HelloWorld
```

With `\n`:

```c
printf("Hello\n");
printf("World");
```

Output:

```text
Hello
World
```

---

# 5. Taking Input — `scanf()`

`scanf()` is used to read formatted input from the user.

Example:

```c
#include <stdio.h>

int main()
{
    int age;

    scanf("%d", &age);

    printf("Age: %d", age);

    return 0;
}
```

If the user enters:

```text
21
```

Output:

```text
Age: 21
```

---

# 6. Why `&age`?

This is very important.

```c
scanf("%d", &age);
```

`scanf()` needs the **address of the variable** so it can store the input there.

```text
age
 ↓
memory location
 ↓
&age
 ↓
scanf() stores input
```

For now, remember:

```c
scanf("%d", &age);
```

For ordinary numeric/character variables, use `&` with `scanf()`.

Strings are a special case:

```c
char name[20];

scanf("%19s", name);
```

You don't use `&name` here.

Pointers will make the reason clearer later.

---

# 7. Input for Different Data Types

| Type     | Declaration      | `scanf()` |
| -------- | ---------------- | --------- |
| `int`    | `int age;`       | `%d`      |
| `float`  | `float price;`   | `%f`      |
| `double` | `double salary;` | `%lf`     |
| `char`   | `char grade;`    | `%c`      |
| String   | `char name[20];` | `%19s`    |

### Example

```c
#include <stdio.h>

int main()
{
    int age;
    float height;
    double salary;
    char grade;

    scanf("%d", &age);
    scanf("%f", &height);
    scanf("%lf", &salary);
    scanf(" %c", &grade);

    printf("%d\n", age);
    printf("%f\n", height);
    printf("%lf\n", salary);
    printf("%c\n", grade);

    return 0;
}
```

Notice:

```c
scanf(" %c", &grade);
```

The space before `%c` helps skip leftover whitespace such as a newline.

---

# 8. Multiple Inputs

You can read multiple values in one `scanf()`:

```c
int age;
float marks;

scanf("%d %f", &age, &marks);
```

Input:

```text
21 85.5
```

Or:

```text
21
85.5
```

Both can work because whitespace in a `scanf` format generally matches optional whitespace in the input.

---

# 9. Multiple Variables with `printf()`

```c
int age = 21;
int marks = 85;

printf("Age = %d, Marks = %d", age, marks);
```

Output:

```text
Age = 21, Marks = 85
```

The order matters:

```c
printf("%d %d", age, marks);
```

means:

```text
%d → age
%d → marks
```

---

# 10. Width and Decimal Precision

For floating-point output:

```c
float marks = 85.6789f;

printf("%f", marks);
```

Output:

```text
85.678902
```

You can control the number of digits after the decimal point:

```c
printf("%.2f", marks);
```

Output:

```text
85.68
```

| Format | Meaning                       |
| ------ | ----------------------------- |
| `%f`   | Default floating-point output |
| `%.1f` | 1 digit after decimal         |
| `%.2f` | 2 digits                      |
| `%.3f` | 3 digits                      |

---

# 11. Character Input

```c
char grade;

scanf(" %c", &grade);

printf("Grade: %c", grade);
```

Input:

```text
A
```

Output:

```text
Grade: A
```

---

# 12. String Output

```c
char name[] = "Gajanand";

printf("%s", name);
```

Output:

```text
Gajanand
```

For a simple single-word string:

```c
char name[20];

scanf("%19s", name);
```

If the input is:

```text
Gajanand
```

it works.

But:

```text
Gajanand Immannavar
```

will not be read as one complete string with `%s`; we'll learn safer line-based string input later.

---

# 13. Complete Example — Student Input

```c
#include <stdio.h>

int main()
{
    int age;
    float marks;
    char grade;

    printf("Enter age: ");
    scanf("%d", &age);

    printf("Enter marks: ");
    scanf("%f", &marks);

    printf("Enter grade: ");
    scanf(" %c", &grade);

    printf("\nStudent Information\n");
    printf("Age: %d\n", age);
    printf("Marks: %.2f\n", marks);
    printf("Grade: %c\n", grade);

    return 0;
}
```

---

# 14. Common Mistakes

### ❌ Missing `&`

```c
scanf("%d", age);
```

### ✅ Correct

```c
scanf("%d", &age);
```

---

### ❌ Wrong format specifier

```c
float price;

scanf("%d", &price);
```

### ✅ Correct

```c
scanf("%f", &price);
```

---

### ❌ Character input issue

```c
scanf("%c", &grade);
```

If a previous input leaves a newline in the input stream, `%c` may read that newline.

### ✅ Common beginner solution

```c
scanf(" %c", &grade);
```

---

# 15. `printf()` vs `scanf()`

| `printf()`                            | `scanf()`                             |
| ------------------------------------- | ------------------------------------- |
| Output                                | Input                                 |
| Displays data                         | Reads data                            |
| Usually doesn't use `&` for variables | Usually uses `&` for scalar variables |
| `%d`, `%f`, `%c`, `%s`                | `%d`, `%f`, `%lf`, `%c`, `%s`         |
| Sends data to screen                  | Receives data from standard input     |

---

# 🧠 Remember

```text
printf() → Output
scanf()  → Input
```

And:

```text
printf("%d", age);
             ↑
          value
```

```text
scanf("%d", &age);
             ↑
          address
```

### Must-remember specifiers

| Type     | `printf()` | `scanf()` |
| -------- | ---------: | --------: |
| `int`    |       `%d` |      `%d` |
| `float`  |       `%f` |      `%f` |
| `double` |       `%f` |     `%lf` |
| `char`   |       `%c` |      `%c` |
| String   |       `%s` |      `%s` |

---

# 📝 Practice

Write these yourself:

1. Take two integers and print them.
2. Take two integers and print their sum.
3. Take a student's name, age and marks and print them.
4. Take length and width and calculate rectangle area.
5. Take radius and calculate circle area.
6. Take temperature in Celsius and convert to Fahrenheit.
7. Take three numbers and print their average.
8. Take `int`, `float`, `double`, and `char` values from the user and print them.
9. Take principal, rate and time and calculate simple interest.
10. Create a program that takes a student's marks in 3 subjects and prints the total and average.

