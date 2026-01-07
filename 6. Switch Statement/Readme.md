
---

# Old Switch Statement vs New Switch Expression

---

## 1. Old Switch Statement (Before Java 12)

### Characteristics

* Works as a **statement**, not an expression
* Uses `case` with `:`
* Requires **break** to avoid fall-through
* Cannot return a value directly
* More **verbose** and error-prone

---

### Example

```java
int day = 3;
String dayName;

switch (day) {
    case 1:
        dayName = "Monday";
        break;
    case 2:
        dayName = "Tuesday";
        break;
    case 3:
        dayName = "Wednesday";
        break;
    default:
        dayName = "Invalid day";
}
```

### Problems

❌ Forgetting `break` causes bugs
❌ Extra boilerplate code
❌ Not usable directly as a return value

---

## 2. New Switch Expression (Java 12+, Stable in Java 14)

### Characteristics

* Works as an **expression**
* Uses `->` arrow syntax
* No need for `break`
* Can **return a value**
* Supports **multiple case labels**
* More **concise and readable**

---

### Example

```java
int day = 3;

String dayName = switch (day) {
    case 1 -> "Monday";
    case 2 -> "Tuesday";
    case 3 -> "Wednesday";
    default -> "Invalid day";
};
```

✔ Cleaner
✔ Safer
✔ Less code

---

## 3. Using Multiple Case Values (New Feature)

### Old Switch

```java
switch (day) {
    case 1:
    case 7:
        System.out.println("Weekend");
        break;
}
```

### New Switch

```java
String type = switch (day) {
    case 1, 7 -> "Weekend";
    default -> "Weekday";
};
```

---


## 4. Fall-Through Behavior

| Feature        | Old Switch         | New Switch |
| -------------- | ------------------ | ---------- |
| Fall-through   | Yes (unless break) | ❌ No       |
| break required | Yes                | ❌ No       |
| Safer          | ❌                  | ✅          |

---

## 5. Return Value Support

### Old Switch ❌

```java
// Not allowed
String result = switch(x) { ... };
```

### New Switch ✅

```java
String result = switch(x) {
    case 1 -> "One";
    default -> "Other";
};
```

---

## 6. Interview One-Line Answer

> **Old switch is a statement and needs break.
> New switch is an expression, uses arrow syntax, avoids fall-through, and can return values.**

---

## Final Comparison Table

| Feature       | Old Switch | New Switch            |
| ------------- | ---------- | --------------------- |
| Type          | Statement  | Expression            |
| Syntax        | `case :`   | `case ->`             |
| break needed  | Yes        | No                    |
| Fall-through  | Yes        | No                    |
| Returns value | No         | Yes                   |
| Readability   | Low        | High                  |
| Introduced    | Java 1.0   | Java 12 (final in 14) |

---
