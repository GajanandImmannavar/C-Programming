# Type Conversion & Casting

**Type conversion** means changing a value from one data type to another.

Example:

```c
int a = 10;
float b = a;
```

Here `int` → `float`.

There are two main types:

| Type                    | Meaning                                 | Example                |
| ----------------------- | --------------------------------------- | ---------------------- |
| **Implicit conversion** | C automatically converts the type       | `float x = 10;`        |
| **Explicit casting**    | You manually tell C to convert the type | `float x = (float)10;` |

---

# 1. Implicit Type Conversion

C automatically converts a value when needed.

```c
int a = 10;
float b = a;
```

Conceptually:

```text
int 10
  ↓
float 10.0
```

Example:

```c
#include <stdio.h>

int main()
{
    int a = 10;
    float b = a;

    printf("%f", b);

    return 0;
}
```

Output:

```text
10.000000
```

No cast was required.

---

# 2. Integer → Floating Point

```c
int age = 21;
float value = age;
```

The integer can be represented as a floating-point value.

```text
21 → 21.0
```

This is generally a safe conversion in terms of preserving the integer's value for the usual range where the floating type can represent it exactly.

---

# 3. Float → Integer

This is different.

```c
float price = 10.75;
int value = price;
```

The fractional part is discarded:

```text
10.75 → 10
```

Example:

```c
#include <stdio.h>

int main()
{
    float price = 10.75;
    int value = price;

    printf("%d", value);

    return 0;
}
```

Output:

```text
10
```

It does **not round**:

```text
10.75 → 11  ❌
10.75 → 10  ✅
```

---

# 4. Explicit Type Casting

You can manually convert a value using:

```c
(type)value
```

Example:

```c
float result = (float)10;
```

Here:

```text
(float)
   ↓
Target type

10
   ↓
Value being converted
```

---

# 5. Integer Division Problem ⭐

This is one of the most important concepts.

Consider:

```c
int a = 10;
int b = 3;

float result = a / b;
```

You might expect:

```text
3.333333
```

But you get:

```text
3.000000
```

Why?

Because:

```text
int / int
   ↓
integer division
   ↓
3
   ↓
float
   ↓
3.0
```

The conversion happens **after** the division.

---

# 6. Correct Way

Cast one operand before division:

```c
float result = (float)a / b;
```

Now:

```text
(float)10 / 3
     ↓
10.0 / 3
     ↓
3.333333
```

Example:

```c
#include <stdio.h>

int main()
{
    int a = 10;
    int b = 3;

    float result = (float)a / b;

    printf("%.2f", result);

    return 0;
}
```

Output:

```text
3.33
```

---

# 7. One Operand Is Enough

You don't need to cast both:

```c
(float)a / b
```

is enough.

Because once one operand is `float`, the other operand is converted for the arithmetic operation.

```c
(float)a / b
```

is effectively:

```text
float / int
    ↓
float / float
```

---

# 8. Common Conversion Examples

| Expression      | Result Type/Behavior  |
| --------------- | --------------------- |
| `10 + 5`        | `int`                 |
| `10 / 3`        | `int` result: `3`     |
| `10.0 / 3`      | floating-point result |
| `(float)10 / 3` | floating-point result |
| `(int)10.75`    | `10`                  |
| `(float)10`     | `10.0`                |

---

# 9. `char` and Integer Conversion

Characters are represented using integer character codes.

Example:

```c
char ch = 'A';

printf("%d", ch);
```

This prints the numeric character code for `'A'` in the execution character set; on the usual ASCII-based systems, it is:

```text
65
```

You can also convert an integer to a character:

```c
int value = 65;

printf("%c", (char)value);
```

Typical ASCII-based output:

```text
A
```

---

# 10. Type Conversion in Expressions

Consider:

```c
int a = 10;
float b = 2.5;

float result = a + b;
```

C converts `a` to a floating-point value for the operation:

```text
10 + 2.5
 ↓
10.0 + 2.5
 ↓
12.5
```

---

# 11. Conversion Can Lose Information

Some conversions can lose information.

### Floating point → integer

```c
float x = 10.99;
int y = x;
```

Result:

```text
y = 10
```

### Large integer → floating point

A floating-point type may not represent every integer exactly once integers become sufficiently large.

So don't assume every conversion preserves the exact original value.

---

# 12. Implicit vs Explicit

| Feature    | Implicit               | Explicit                                         |
| ---------- | ---------------------- | ------------------------------------------------ |
| Done by    | C                      | Programmer                                       |
| Syntax     | No cast required       | `(type)value`                                    |
| Example    | `float x = 10;`        | `float x = (float)10;`                           |
| Control    | Less direct            | Programmer controls conversion                   |
| Common use | Compatible conversions | Avoiding integer division, deliberate conversion |

---

# 13. Type Casting Syntax

The general syntax is:

```c
(target_type) expression
```

Examples:

```c
(float)a
(int)x
(char)value
(double)number
```

Example:

```c
int a = 5;
int b = 2;

double result = (double)a / b;
```

Result:

```text
2.5
```

---

# 14. A Very Important Difference

Compare:

### ❌ Wrong for decimal division

```c
float result = a / b;
```

if both `a` and `b` are `int`.

### ✅ Correct

```c
float result = (float)a / b;
```

The key is **when the conversion happens**.

```text
a / b
 ↓
integer division
 ↓
3
 ↓
float
 ↓
3.0
```

versus:

```text
(float)a / b
 ↓
floating-point division
 ↓
3.333...
```

---

# 15. Practice Programs

Write these yourself.

### Basic

1. Convert an `int` to `float`.
2. Convert a `float` to `int`.
3. Convert a `double` to `int`.
4. Convert an integer character code to `char`.
5. Convert a character to its integer code.

### Important

6. Divide two integers and print the decimal result.
7. Calculate the average of three integers as a decimal.
8. Calculate percentage using integer marks and total marks.
9. Convert Celsius to Fahrenheit using floating-point arithmetic.
10. Calculate the exact average of 5 integers.

### Challenge

Predict the output **before running**:

```c
#include <stdio.h>

int main()
{
    int a = 10;
    int b = 3;

    printf("%d\n", a / b);
    printf("%.2f\n", (float)a / b);
    printf("%d\n", (int)10.99);

    return 0;
}
```

Expected:

```text
3
3.33
10
```

---

# 🧠 Remember These 4 Rules

```text
1. int / int → integer division

2. (float)int → explicit conversion

3. float → int → fractional part is discarded

4. Convert BEFORE the operation when you need
   floating-point arithmetic.
```


