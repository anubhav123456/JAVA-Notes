# Static Keyword in Java

## What is `static` in Java?

* The `static` modifier indicates that a **field, method, block, or nested class** belongs to the **class itself**, not to objects (instances).
* Static members can be accessed **without creating an object** of the class.
* A **single copy** of static members is shared among **all instances** of the class.

---

## Key Characteristics of Static Members

* Associated with the **class**, not with individual objects
* Loaded into memory **once**, when the class is loaded
* Can be accessed using `ClassName.member`
* Useful for:

  * Constants
  * Utility methods
  * Counters / shared data
  * Factory methods

---

## Static Variables (Class Variables)

* Declared using the `static` keyword
* Only **one copy exists**, shared by all objects
* Commonly used to maintain **global state** for a class

### Example: Static Variable

```java
public class Person {
    private String name;
    private String eyeColour;

    public static int numberOfPeople;

    public Person(String name, String colour) {
        this.name = name;
        this.eyeColour = colour;
        numberOfPeople++;
    }

    public getName(){
        return this.name;
    }
    public getEyeColour(){
        return this.eyeColour;
    }
}
```

### Accessing Static Variables via Class

```java
public static void main(String[] args) {
    Person chris = new Person("Chris","Blue");

    System.out.println(Person.numberOfPeople);
    // output: 1
}
```

### Accessing Static Variables Without Creating an Object

```java
public static void main(String[] args) {
    System.out.println(Person.numberOfPeople);
    // output: 0
}
```

---

## Static Methods

* Belong to the **class**, not to instances
* Can be called **without creating an object**
* Cannot directly access **non-static (instance) variables or methods**
* Typically used for **utility or helper operations**

### Example: Static Method

```java
public class Person {
    private String name;
    private String eyeColour;

    public static int numberOfPeople;

    public Person(String name, String colour) {
        this.name = name;
        this.eyeColour = colour;
        numberOfPeople++;
    }
    // Getters and Setters

    public static void setNumOfPeople(int numPeople){
        Person.numberOfPeople = numPeople;
    }
}
```

### Using the Static Method

```java
public static void main(String[] args) {

    Person chris = new Person("Tom","Blue");
    Person tom = new Person("Tom","Brown");

    Person.setNumOfPeople(0);

    Person stephan = new Person("Stephan","Greenish-Brownish-Blueish");

    System.out.println(Person.numberOfPeople);
    // output: 1
}
```

---

## Static Blocks

* Used to **initialize static variables** that require **multiple lines of logic**
* Executed **once**, when the class is loaded
* A class can have **multiple static blocks**
* Executed in the **order they appear** in the class

### Single-Line Static Initialization

```java
public static int num = 24;
```

### Multi-Line Initialization Using Static Blocks

```java
public class StaticBlockDemo {
    public static List<String> languages = new LinkedList<>();

    static {
        languages.add("Java");
        languages.add("C++");
        languages.add("Python");
    }

    static {
        languages.add("HTML");
        languages.add("Groovy");
    }
}
```

---

## Static Nested Classes

* Java allows defining a class **inside another class**
* Two types of nested classes:

  * **Static nested classes**
  * **Inner (non-static) classes**

### Differences

| Feature                     | Inner Class | Static Nested Class |
| --------------------------- | ----------- | ------------------- |
| Requires outer class object | Yes         | No                  |
| Access to instance members  | Yes         | No                  |
| Access to static members    | Yes         | Yes                 |

---

## Example: Static Nested Class (Singleton Pattern)

```java
public class Singleton  {
    private Singleton() {}

    private static class SingletonHolder {
        public static final Singleton INSTANCE = new Singleton();
    }

    public static Singleton getInstance() {
        return SingletonHolder.INSTANCE;
    }
}
```

### Key Points

* Static nested classes:

  * Can access **only static members** of the outer class directly
  * Can access private static members
  * Do **not** require an instance of the outer class
* Commonly used in:

  * Singleton pattern
  * Builder pattern
  * Helper classes

---

## Important Rules & Notes

* ❌ Top-level classes **cannot** be declared `static`
* ✅ Only **nested classes** can be static
* Static members:

  * Exist independently of objects
  * Are shared across all instances
* `static` + `final` is commonly used to define **constants**

---

## Summary

* `static` binds members to the **class**, not objects
* Used for:

  * Class-level variables
  * Utility methods
  * Initialization logic
  * Nested helper classes
* Helps in:

  * Memory efficiency
  * Clear separation of shared vs instance data
  * Cleaner and more organized design
----