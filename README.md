# Instance Methods and Variables

## Learning Goals

- Explain Instance Variables
- Explain Instance Methods

## Instance Variables

An **instance variable** is a variable that is declared _inside a class_ but not
within a method. Instance variables belong to the object of the class, not the
class itself. This means that when an object is created, it has its own copy
of instance variables created along with it.

Let's look at our `Student` class from the last lesson:

```java
public class Student {
    private String firstName;
    private String lastName;
    private String major;
}
```

The attributes `firstName`, `lastName`, and `major` are all instance
variables. Notice how the instance variables have an access modifier
attached to it. Since all these attributes are `private`, we could even say
that they are **private instance variables**. It is usually recommended to
make these variables private to restrict other classes from using these
variables directly.

Instance variables also always get a default value. If we don't explicitly
assign a value to an instance variable, then the instance variable still has a
value.

### Instance Variables vs. Local Variables

Instance variables are **not** the same as local variables. A **local variable**
is declared within a method, not at the class level.

For example, say our `Student` class has a method called `calculateGrade`:

```java
public class Student {
    private String firstName;
    private String lastName;
    private String major;
    
    public int calculateGrade() {
        int grade;    // This is a local variable
        ...
        return grade;
    }
}
```

The variable `grade` declared in the `calculateGrade` would be a local variable.
It cannot be used outside the method nor does it have a default value. Local
variables must be initialized before use; otherwise we will run into a
compilation error.

## Instance Methods

An **instance method** is a method that belongs to the object of the class, not
the class itself. This means that we must create an object of that class prior
to using any of its methods. An instance method usually directly correlates with
the object itself. For example, in our `Student` class, if we were to calculate
Suzie's grade, it most likely will be different from Dustin's grade. This is
where instance methods come in handy.

In the above example, we can say that the `calculateGrade()` method is an
instance method. In order to call it, we would need to instantiate a
`Student` object:

```java
Student suzie = new Student("Suzie", "Bingham", "Computer Science");
int suzieGrade = suzie.calculateGrade();
```

### Instance Methods vs. Static Methods

There are some methods that do not need a reference to an object to call a
method. These methods are called **static methods**. We remember the `static`
keyword from the Non-Access Modifiers lesson. When a method has the keyword
`static` in its header, then it can be called without creating an instance of a
class.

Let's go back to our `Bicycle` class for a minute:

```java
public class Bicycle {
    private String color;
    private int height;
    
    public void ride() {
        System.out.println("We're going for a ride! Whee!");
    }
}
```

Currently, the `ride()` method is considered an instance method; however,
isn't going on a bike ride the same for whether John rides his bike or
Claire rides her bike? This method could be shared across all instances of the
same class. When this happens, we could make it a `static` method by applying
the `static` non-access modifier to the method heading like so:

```java
public class Bicycle {
    private String color;
    private int height;
    
    public static void ride() {
        System.out.println("We're going for a ride! Whee!");
    }
}
```
