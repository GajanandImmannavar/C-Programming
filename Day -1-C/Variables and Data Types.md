# Day 1 → Topic 2: Variables and Data Types

Now we'll learn **variables and data types**, which are the foundation for storing and working with data in C.

---

## 1. What is a Variable?

A **variable** is a named memory location used to store a value.

For example:

```c
int age = 21;
```

Think of it like a box:

```text
Memory
┌─────────────┐
│     21      │
└─────────────┘
      ↑
     age
```

Here:

| Part  | Meaning             |
| ----- | ------------------- |
| `int` | Data type           |
| `age` | Variable name       |
| `=`   | Assignment operator |
| `21`  | Value               |
| `;`   | End of statement    |

---

# 2. Why Do We Need Variables?

Without variables:

```c
printf("21");
printf("21");
printf("21");
```

With variables:

```c
int age = 21;

printf("%d", age);
```

The second approach is useful because the value can change:

```c
int age = 21;

age = 22;

printf("%d", age);
```

Output:

```text
22
```

---

# 3. Declaring a Variable

Declaration tells C:

> "I want a variable of this type."

```c
int age;
```

At this point, we have declared `age`, but haven't given it a useful value.

Then:

```c
age = 21;
```

This gives it a value.

So:

```c
int age;
age = 21;
```

---

# 4. Initialization

You can declare and assign a value at the same time:

```c
int age = 21;
```

This is called **initialization**.

### Declaration

```c
int age;
```

### Assignment

```c
age = 21;
```

### Initialization

```c
int age = 21;
```

---

# 5. Basic C Data Types

The most important basic types are:

| Data Type | Used for                     | Example    |
| --------- | ---------------------------- | ---------- |
| `int`     | Whole numbers                | `25`       |
| `float`   | Decimal numbers              | `3.14`     |
| `double`  | More precise decimal numbers | `3.141592` |
| `char`    | Single character             | `'A'`      |

---

# 6. `int`

Used for whole numbers.

```c
int age = 21;
int marks = 85;
int count = 100;
```

Example:

```c
#include <stdio.h>

int main()
{
    int age = 21;

    printf("%d", age);

    return 0;
}
```

Output:

```text
21
```

`%d` is the format specifier used to print an `int`.

---

# 7. `float`

Used for decimal values.

```c
float height = 5.8;
```

Example:

```c
#include <stdio.h>

int main()
{
    float height = 5.8;

    printf("%f", height);

    return 0;
}
```

Output may look like:

```text
5.800000
```

You can control the number of decimal places:

```c
printf("%.2f", height);
```

Output:

```text
5.80
```

---

# 8. `double`

`double` is also used for decimal values and generally provides **more precision than `float`**.

```c
double pi = 3.1415926535;
```

Example:

```c
#include <stdio.h>

int main()
{
    double pi = 3.1415926535;

    printf("%lf", pi);

    return 0;
}
```

For `printf`, `%f` is commonly used for both `float` and `double`; for `scanf`, `%f` is used for `float` and `%lf` for `double`.

---

# 9. `char`

Used to store a **single character**.

```c
char grade = 'A';
```

Notice the difference:

```c
'A'    → character
"A"    → string
```

Example:

```c
#include <stdio.h>

int main()
{
    char grade = 'A';

    printf("%c", grade);

    return 0;
}
```

Output:

```text
A
```

`%c` is used to print a character.

---

# 10. String vs Character

This is very important.

### Character

```c
char grade = 'A';
```

One character.

### String

```c
char name[] = "Gajanand";
```

Multiple characters.

```text
'A'       → character
"Gajanand" → string
```

We'll study strings properly later.

---

# 11. Multiple Variables

You can create multiple variables:

```c
int age = 21;
float height = 5.8;
char grade = 'A';
```

Then:

```c
printf("%d\n", age);
printf("%.1f\n", height);
printf("%c\n", grade);
```

Output:

```text
21
5.8
A
```

---

# 12. `sizeof()`

C provides `sizeof()` to determine the size of a type or object in bytes.

Example:

```c
#include <stdio.h>

int main()
{
    int age = 21;

    printf("%zu", sizeof(age));

    return 0;
}
```

The exact size of C types is **implementation-defined**, so don't assume `int` is always exactly 4 bytes.

You can check your system:

```c
printf("%zu\n", sizeof(int));
printf("%zu\n", sizeof(float));
printf("%zu\n", sizeof(double));
printf("%zu\n", sizeof(char));
```

---

# 13. Variable Naming Rules

Valid:

```c
int age;
int studentAge;
int marks1;
int _count;
```

Invalid:

```c
int 1age;        // Cannot start with a digit
int student age; // Spaces not allowed
int int;         // Keyword cannot be used
```

### Important rules

A variable name:

* Can contain letters
* Can contain digits
* Can contain `_`
* Cannot start with a digit
* Cannot contain spaces
* Cannot be a C keyword
* Is case-sensitive

For example:

```c
age
Age
AGE
```

are three different identifiers.

---

# 14. Variable Naming Best Practice

Prefer meaningful names:

```c
int studentAge;
float salary;
int totalMarks;
```

Avoid:

```c
int x;
int a;
int abc;
```

unless the short name has a clear purpose.

---

# 15. Changing a Variable

Variables can change:

```c
int age = 21;

age = 22;

printf("%d", age);
```

Output:

```text
22
```

The variable is still called `age`; only its stored value changed.

---

# 16. Constants with `const`

You can make an object non-modifiable through `const`:

```c
const int DAYS = 7;
```

Then this is not allowed:

```c
DAYS = 10;
```

`const` means the object cannot be modified through that identifier after initialization.

We'll cover `const`, literals, `#define`, and constant expressions more deeply later.

---

# 17. Complete Example

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

Output:

```text
Age: 21
Height: 5.8
Percentage: 85.75
Grade: A
```

---

# 🧠 Remember This

```text
Variable
   ↓
Name + Type + Value
   ↓
int age = 21;
│   │    │
│   │    └── Value
│   └─────── Variable name
└─────────── Data type
```

### The four basic types to remember now:

```text
int     → whole numbers
float   → decimal numbers
double  → more precise decimal numbers
char    → single character
```

---

# 📝 Practice Before Moving On

Write these programs yourself:

### 1. Student Information

Create variables for:

```text
Name
Age
Marks
Grade
```

and print them.

### 2. Rectangle

Create:

```text
length
width
```

Calculate:

```text
Area = length × width
```

### 3. Salary

Create a salary variable and print it.

### 4. Temperature

Store a temperature in Celsius and print it.

### 5. Experiment with `sizeof()`

Print the size of:

```text
char
int
float
double
```

---

