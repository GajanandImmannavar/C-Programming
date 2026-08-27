# Operators in C

Operators are symbols used to **perform operations on values and variables**.

```text
Operand  Operator  Operand
   10        +        20
              ↓
            30
```

---

## 1. Types of Operators

| Operator Type       | Operators          | Purpose                   |    |                    |
| ------------------- | ------------------ | ------------------------- | -- | ------------------ |
| Arithmetic          | `+ - * / %`        | Mathematical calculations |    |                    |
| Assignment          | `= += -= *= /= %=` | Assign/update values      |    |                    |
| Relational          | `== != > < >= <=`  | Compare values            |    |                    |
| Logical             | `&&                |                           | !` | Combine conditions |
| Increment/Decrement | `++ --`            | Increase/decrease by 1    |    |                    |
| Conditional         | `?:`               | Short `if-else`           |    |                    |
| Bitwise             | `& \| ^ ~ << >>`   | Bit-level operations      |    |                    |

For your basic-to-medium roadmap, learn the first **6** thoroughly. Bitwise can be learned separately.

---

# 2. Arithmetic Operators

| Operator | Meaning        | Example  | Result |
| -------- | -------------- | -------- | -----: |
| `+`      | Addition       | `10 + 3` |   `13` |
| `-`      | Subtraction    | `10 - 3` |    `7` |
| `*`      | Multiplication | `10 * 3` |   `30` |
| `/`      | Division       | `10 / 3` |    `3` |
| `%`      | Remainder      | `10 % 3` |    `1` |

Example:

```c
#include <stdio.h>

int main()
{
    int a = 10;
    int b = 3;

    printf("Addition: %d\n", a + b);
    printf("Subtraction: %d\n", a - b);
    printf("Multiplication: %d\n", a * b);
    printf("Division: %d\n", a / b);
    printf("Remainder: %d\n", a % b);

    return 0;
}
```

---

# 3. Important — Integer Division

This is a common beginner mistake.

```c
int a = 10;
int b = 3;

printf("%d", a / b);
```

Output:

```text
3
```

Because both operands are integers.

But:

```c
printf("%f", (float)a / b);
```

produces approximately:

```text
3.333333
```

So:

```text
10 / 3       → 3
10.0 / 3     → 3.333...
(float)10/3  → 3.333...
```

---

# 4. Modulus `%`

`%` gives the **remainder**.

```text
10 % 3 = 1
15 % 5 = 0
17 % 4 = 1
```

Very useful for programming problems.

### Even/Odd

```c
if (number % 2 == 0)
{
    printf("Even");
}
```

Why?

```text
Even number % 2 → 0
Odd number  % 2 → 1
```

---

# 5. Assignment Operator

The basic assignment operator is:

```c
=
```

Example:

```c
int age;

age = 21;
```

It means:

> Store `21` in `age`.

It does **not** mean mathematical equality.

---

## 6. Compound Assignment Operators

| Operator | Equivalent  |
| -------- | ----------- |
| `x += 5` | `x = x + 5` |
| `x -= 5` | `x = x - 5` |
| `x *= 5` | `x = x * 5` |
| `x /= 5` | `x = x / 5` |
| `x %= 5` | `x = x % 5` |

Example:

```c
int x = 10;

x += 5;

printf("%d", x);
```

Output:

```text
15
```

---

# 7. Relational Operators

Used to **compare two values**.

| Operator | Meaning               |
| -------- | --------------------- |
| `==`     | Equal to              |
| `!=`     | Not equal             |
| `>`      | Greater than          |
| `<`      | Less than             |
| `>=`     | Greater than or equal |
| `<=`     | Less than or equal    |

Example:

```c
int a = 10;
int b = 20;

printf("%d", a < b);
```

Output:

```text
1
```

In C:

```text
1 → true
0 → false
```

---

# 8. `=` vs `==` ⭐

This is extremely important.

### Assignment

```c
x = 10;
```

Means:

> Put 10 into x.

### Comparison

```c
x == 10
```

Means:

> Is x equal to 10?

Example:

```c
if (age == 18)
{
    printf("Eligible");
}
```

Don't accidentally write:

```c
if (age = 18)
```

That performs an assignment rather than the intended comparison.

---

# 9. Logical Operators

Logical operators combine conditions.

| Operator | Name | Meaning                      |    |                                     |
| -------- | ---- | ---------------------------- | -- | ----------------------------------- |
| `&&`     | AND  | Both conditions must be true |    |                                     |
| `        |      | `                            | OR | At least one condition must be true |
| `!`      | NOT  | Reverses true/false          |    |                                     |

---

## AND `&&`

```c
age >= 18 && age <= 60
```

Both must be true.

```text
true && true   → true
true && false  → false
false && true  → false
false && false → false
```

---

## OR `||`

```c
day == 6 || day == 7
```

At least one condition must be true.

```text
true || true   → true
true || false  → true
false || true  → true
false || false → false
```

---

## NOT `!`

```c
!(age >= 18)
```

Reverses the result.

```text
!true  → false
!false → true
```

---

# 10. Increment `++`

Increases a value by `1`.

```c
int x = 5;

x++;

printf("%d", x);
```

Output:

```text
6
```

Equivalent to:

```c
x = x + 1;
```

---

# 11. Decrement `--`

Decreases a value by `1`.

```c
int x = 5;

x--;

printf("%d", x);
```

Output:

```text
4
```

Equivalent to:

```c
x = x - 1;
```

---

# 12. Pre-Increment vs Post-Increment ⭐

This becomes important when you start solving problems.

### Post-increment

```c
int x = 5;

printf("%d", x++);
```

Output:

```text
5
```

Afterward:

```text
x = 6
```

### Pre-increment

```c
int x = 5;

printf("%d", ++x);
```

Output:

```text
6
```

The value is incremented **before** it is used.

### Remember

```text
x++ → use first, increment later
++x → increment first, use later
```

Same concept applies to `--x` and `x--`.

---

# 13. Conditional Operator `?:`

A short form of simple `if-else`.

```c
condition ? value_if_true : value_if_false;
```

Example:

```c
int age = 20;

age >= 18 ? printf("Adult") : printf("Minor");
```

Output:

```text
Adult
```

Another example:

```c
int a = 10;
int b = 20;

int max = (a > b) ? a : b;

printf("%d", max);
```

Output:

```text
20
```

---

# 14. Operator Precedence

When multiple operators appear together, C follows precedence and associativity rules.

Example:

```c
int result = 10 + 5 * 2;
```

Multiplication happens first:

```text
10 + (5 * 2)
10 + 10
20
```

Not:

```text
(10 + 5) * 2
= 30
```

### Basic order to remember

```text
()
↓
* / %
↓
+ -
↓
< > <= >=
↓
== !=
↓
&&
↓
||
↓
= += -= ...
```

When in doubt, **use parentheses**:

```c
int result = (10 + 5) * 2;
```

---

# 15. Type Casting

You can explicitly convert a value to another type.

```c
int a = 10;
int b = 3;

float result = (float)a / b;

printf("%f", result);
```

Output:

```text
3.333333
```

Here:

```c
(float)a
```

converts `a` to `float` before division.

---

# 16. Important Operator Table

| Category    | Operators          | Example          |
| ----------- | ------------------ | ---------------- |
| Arithmetic  | `+ - * / %`        | `a + b`          |
| Assignment  | `= += -= *= /= %=` | `a += 5`         |
| Relational  | `== != > < >= <=`  | `a > b`          |
| Logical     | `&& \|\| !`        | `a > 0 && b > 0` |
| Increment   | `++`               | `a++`            |
| Decrement   | `--`               | `a--`            |
| Conditional | `?:`               | `a > b ? a : b`  |

---

# 🧪 Practice

Write these programs yourself:

### Basic

1. Take two numbers and perform `+`, `-`, `*`, `/`, `%`.
2. Find the remainder of two numbers.
3. Check whether a number is even or odd.
4. Check whether a number is divisible by 5.
5. Calculate the average of three numbers.

### Comparison

6. Find the greater of two numbers.
7. Check whether a person is eligible based on age.
8. Check whether a number lies between 10 and 100.

### Logical Operators

9. Check whether a number is positive **and** even.
10. Check whether a number is divisible by 3 **or** 5.

### Increment / Decrement

11. Demonstrate `x++` and `++x`.
12. Demonstrate `x--` and `--x`.

### Type Casting

13. Divide two integers and produce a decimal result.
14. Take marks and calculate the average as a `float`.

### Challenge

15. Take three numbers and find the largest using the **conditional operator**.

---

## 🧠 Quick Check

You should now understand:

```text
+ - * / %
      ↓
  Arithmetic

= += -= *= /=
      ↓
 Assignment

== != > < >= <=
      ↓
 Comparison

&& || !
      ↓
 Logical

++ --
      ↓
 Increment / Decrement

?:
      ↓
 Conditional
```
