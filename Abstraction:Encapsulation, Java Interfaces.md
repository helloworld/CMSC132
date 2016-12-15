
### Interfaces

```java
interface CanFly {
    public void takeOff();
    public void flyTo(String destination);
    public void land();
}

class Bird implments CanFly {
    public void takeOff() {
        ...
    }
    public void takeOff(String destination) {
        ...
    }
    public void land() {
        ...
    }
}
```

Java interface can only contain method signatures and fields. They do not contain the implementaiton. 

----

```java
void flyToFrance(CanFly x) { // x is a Polymorphic variable
    x.takeOff(); 
    x.flyTo(); // We know x has these methods because it implements CanFly
    x.land();
}
```

---

### Abstract Classes

Abstract classes are like interfaces, but they can have many more things, such as instance variables, etc. 

```java
public abstract class GraphicObject {
   // declare fields
   // declare nonabstract methods
   abstract void draw();
}
```

---

### API - Application Programming Interface

Vocabulary: 
- Encapsulation: Wrap in private shell
- Data Abstraction: Don't know what's happening behind the scenes with data
- Procedural Abstraction: Don't know algorithms/procedure

Think about how LinkedLists were implemented. The internal `Node` class was a Data Abstraction, and the methods like `insert(T element)` and `removeFirst()` used Procedural Abstraction. 

Example API for Student Roster: 

```
Roster
------
- createRoster
- addStudent
- removeStudent
- sort
```

---

### Java Collection Framework

Example: ArrayList

Old Java without Generics: 
```java
ArrayList l = new ArrayList();
l.add(c); // C is-a Cat
Cat d = (Cat)l.get(0); // Cast
```

Java with Generics:
```java
ArrayList<Cat> l = new ArrayList<Cat>();
l.add(c);
Cat d  l.get(0); // No need for Cast.
```

---

### Java Collection Interface

`<E>` = unknown type
`<? extends E>` extensions of unkown type

Can pass in a collection to method, and methods that are implemented as part of the Collection Inteface work. 
```java
public void foo(Collection<Cat> c) {
    ...
    c.add(d);
}
```

---

### Class Collections (Notice the `s`)

- Tool for Collections. 
- Not a class to instantiate. Only has static methods. 
- Example: `Collections.sort(a)`, where `a` is a Collection. 

---

### Imports

The following are the exact same:

```java
import Java.Util.Scanner;
Scanner s = ...;
```

```java
Java.Util.Scanner s = ...;
```

---

### Foreach loops

```java
for(Cat value : c) {...}
```

---

### Java Primitives

Java primitives have a corresponding wrapper class. 
Example: `int` -> `Integer`

```java
int x = new Integer(7); // Auto un-boxing
Integer y = 12; // Auto-boxing
```

Java seamlessly converts between primitive and wrapper types. 
This is useful for generics, since you can't use primitives. 



