
### Abstract Classes 

```java
public abstract class Shape {

    private int size;
    private Color color;
    
    public Shape(int size) {
        this.size = size;
    }
    
    public int getSize() {
        return size;
    }
    
    public Color getColor() {
        return color;
    }
    
    abstract public void drawMe(); // Subclasses will have drawMe. Have to implement. 
}
```

You cannot instantiate shape. (Cannot do `new Shape()`)

```java
public class Circle extends Shape{

    public Circle(int size) {
        super(size);
    }
    
    @Override
    public void drawMe() {
        System.out.println("Drawing Circle of size " + getSize());
    }

}
```

If you make several more shapes (e.g. Triangle, Square), you can do something like this: 

```java
public static void main(String[] args) {
    List<Shape> list = new ArrayList<Shape>();
    list.add(new Circle(5));
    list.add(new Octagon(7));
    list.add(new Circle(26));
    list.add(new Triangle(2));
    list.add(new Triangle(91));
    for (Shape s : list) {
        s.drawMe(); // Dynamic Binding 
    }
}
```

---

### Interfaces vs. Abstract Classes

You can only extend one [abstract] class, but implement "infinite" interfaces. 

With abstract classes, however, you can **inherit** code. 

---

### Shadowing

- Can override instance variables just like methods. 
- Can access the base class instance variable using super.varName
- *Not Recommended. Why do you want to confuse everyone like that?*

---

### Examples of Overloading / Overriding

Classes: 
```java
public class Base {
public void m (int x) { … } // [1]
}

public class Derived extends Base {
public void m (int x) { … } // Overriding // [2]
public int m (int x) { … } // Error! Duplicate Method
public void m (double d) { … } // Overloading // [3]
}
```

Derived:
```java
Base b = new Base( );
Base d = new Derived( );
Derived e = new Derived( );

b.m (5); -> [1]
d.m (6); -> [2]
d.m (7.0); -> Compiler Error! Base: m(double) not found. 
e.m (8.0); -> [3]
```

---

### The `Object` class. 

Everything *is-a* `Object`

Inherits: 
- toString [className@hexAddress]
- equals [==]
- hashCode
- wait
- notify
- notifyAll

---

### Class v. Type Information 

```java
Person p = new Student();
```

Type of `p` is Person. 

Class of this object is Student.

Type of this object is:
- Student
- Person
- Object

**Accessing Type Information** : 

```java
Student carol = new Student(...);
if(carol instanceOf Person) -> true
```

Think of instanceOf as "is-a"

---

### Object Casting

**Primitives**: 

Chart:
```java
double
float
long (8)
int (4)
short (2)
byte (1)
```

```java

double x = 7.2;
double y = 4;

x = y; // Works, Widening. 
y = x; // Error, Narrowing. 
y = int(x); // Works, Casting 
```

Only Widening works. Narrowing requires explicit casting. 

**Objects**

```java
Person p = new Person();
Student s = new Student();

p = s; // Works, Upcast. 
s = p; // Error. Downcast. 
```

Upcasting
- Casting a reference to a superclass (casting up the inheritance tree)
- Always OK
- Just ignore the parts that were added by the subclass

Downcasting
- Casting a reference to a derived class
- Requires explicit casting operator
- Can cause runtime error

```java
Person p = new Person();
Student s = new Student();
Person tricky = new Student();
```

```java
Student y = p;                  // Downcast – Does not compile
Student y = (Student)p;         // Compiles, but throws exception            
Student y = tricky;             // Downcast – Does not compile        
Student y = (Student)tricky;    // Works fine                
(Faculty)s;                     // Does not compile
(Faculty)tricky;                 // Compiles, but throws Exception    
```





