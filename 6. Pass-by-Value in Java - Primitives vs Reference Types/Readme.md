
---

## 1. Pass by Value with **Primitives**

### What happens?

* When you pass a **primitive variable** (int, double, boolean, etc.) to a method,
  **a copy of its value** is passed.
* Changes made inside the method **do NOT affect** the original variable.

### Example

```java
class Test {
    static void change(int x) {
        x = 50;
    }

    public static void main(String[] args) {
        int a = 10;
        change(a);
        System.out.println(a); // Output: 10
    }
}
```

### Explanation

* `a = 10`
* `change(a)` → value `10` is copied to `x`
* `x = 50` modifies only the copy
* Original `a` remains unchanged

📌 **Key Point:**
Primitive values are copied → **no side effects**

---

## 2. Pass by Value with **Reference Types**

### Important concept

* Java passes **the value of the reference**, not the object itself.
* The reference value is a **memory address**.
* Both variables point to the **same object**.

---

### Example 1: Modifying object data (changes reflect)

```java
class Person {
    String name;
}

class Test {
    static void changeName(Person p) {
        p.name = "Rahul";
    }

    public static void main(String[] args) {
        Person person = new Person();
        person.name = "Amit";

        changeName(person);
        System.out.println(person.name); // Output: Rahul
    }
}
```

### Explanation

* `person` holds a reference → say `0x123`
* `p` gets a **copy of the same reference**
* `p.name = "Rahul"` modifies the same object
* Change is visible outside

📌 **Key Point:**
Object data changes → **visible outside method**

---

### Example 2: Reassigning reference (NO effect)

```java
class Test {
    static void changeObject(Person p) {
        p = new Person();
        p.name = "Rohit";
    }

    public static void main(String[] args) {
        Person person = new Person();
        person.name = "Amit";

        changeObject(person);
        System.out.println(person.name); // Output: Amit
    }
}
```

### Explanation

* `p` initially points to same object as `person`
* `p = new Person()` changes **local copy of reference**
* `person` still points to original object

📌 **Key Point:**
Reassigning reference → **no effect outside**

---

## 🔥 Final Summary (Very Important)

| Case                         | What is Passed    | Can Modify Original? |
| ---------------------------- | ----------------- | -------------------- |
| Primitive                    | Copy of value     | ❌ No                 |
| Reference Type (object data) | Copy of reference | ✅ Yes                |
| Reference Reassignment       | Copy of reference | ❌ No                 |

---

## One-Line Rule to Remember

> **Java is always pass by value.**
> For objects, the **value passed is the reference**.

---