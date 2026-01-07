
---

## 1. **public**

🔓 **Most open access**

* Accessible **from anywhere**
* Within the **same class**
* Same **package**
* **Other packages**
* Subclasses (even in other packages)

```java
public class Test {
    public int x = 10;

    public void show() {
        System.out.println(x);
    }
}
```

✅ Use when the member is part of an **API** or must be accessible globally.

---

## 2. **protected**

🛡️ **Package + inheritance access**

* Accessible:

  * Within the **same class**
  * Same **package**
  * **Subclasses** (even in different packages)
* ❌ Not accessible to non-subclass classes in other packages

```java
class Parent {
    protected int data = 20;
}

class Child extends Parent {
    void display() {
        System.out.println(data);
    }
}
```

✅ Commonly used in **inheritance-heavy designs**.

---

## 3. **default (no modifier)**

📦 **Package-private access**

* When **no access modifier is specified**
* Accessible:

  * Within the **same class**
  * Same **package only**
* ❌ Not accessible outside the package (even by subclasses)

```java
class Sample {
    int value = 30; // default access

    void print() {
        System.out.println(value);
    }
}
```

✅ Useful for **internal package-level logic**.

---

## 4. **private**

🔒 **Most restrictive**

* Accessible **only within the same class**
* ❌ Not accessible in same package
* ❌ Not accessible in subclasses

```java
class Account {
    private double balance = 1000;

    private void showBalance() {
        System.out.println(balance);
    }
}
```

✅ Enforces **encapsulation** (very important in Java).

---

## 🔥 Access Level Comparison Table

| Modifier      | Same Class | Same Package | Subclass (Other Package) | Other Classes |
| ------------- | ---------- | ------------ | ------------------------ | ------------- |
| **public**    | ✅          | ✅            | ✅                        | ✅             |
| **protected** | ✅          | ✅            | ✅                        | ❌             |
| **default**   | ✅          | ✅            | ❌                        | ❌             |
| **private**   | ✅          | ❌            | ❌                        | ❌             |

---

## ⭐ Important Interview Points

* **Top-level classes** can only be `public` or `default`
* `protected` members in **different packages** are accessible **only via inheritance**
* `private` members are accessed via **public getter/setter**
* Default access ≠ protected

---
