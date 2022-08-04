# Instance Methods and Variables

## Learning Goals

- Explain constructors
- Create constructors in Java

## Introduction

A **constructor** is a specific kind of method that is called when an object is
instantiated. Constructors, like methods, can have parameters. Unlike methods,
however, constructors do not have an explicit return type because they always
return an object of the type of the class they are defined in.

Let's consider a `Student` class as an example, with fields for their name and
major information:

```java
public class Student {
    private String firstName;
    private String lastName;
    private String major;

    public Student(String firstName, String lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
}
```

In this example, the only constructor we are providing is one that takes in both
the `firstName` and the `lastName` as parameters. We will look at a different
implementation of this constructor as well as another constructor later, but for
now let's inspect the structure of this one constructor:

1. As stated, the constructor does not specify a return type because it always
   returns an object of the type of the class it's defined in, so in this case
   our constructor will return an object of type `Student`.
2. The `this` keyword is used to make a reference to the instance of the
   `Student` class that we are in the process of constructing. We need to use it
   here to make a distinction between the `firstName` variable that belongs to
   this instance we are building vs the `firstName` variable that was passed in
   as a variable to the constructor.
3. Using the `this` keyword, we initialize the value of the `firstName` variable
   of the `Student` instance we're building with the value of the `firstName`
   variable that was passed into the constructor. And we do the same thing with
   `lastName`.

By convention, constructor parameters usually use the same variable names as the
properties in the class they are meant to initialize, which is why we need to
use the `this` keyword to clearly indicate which variable we are referring to in
the constructor. It is possible, however, to use different names for the
parameters into the constructor, in which case the `this` keyword does not need
to be used because there is no ambiguity in the variable names.

Here is a version of the constructor that does that, just for reference. Note
that we will continue to use the generally accepted naming convention in all
subsequent examples.

```java
public Student(String inputFirstName, String inputLastName) {
  firstName = inputFirstName;
  lastName = inputLastName;
}
```

You might have noticed that neither version of the constructors we have shared so
far assign any value to the `major` variable. This not a good behavior, as we
should always try to be explicit about values for all our fields and include
default values if none are provided through the constructor.

There are 2 important things to note here:

1. Not all fields can have default values - for example, what could a "default"
   first name and last name possibly be for a student? Sure it could be "John
   Doe" or "Jane Doe", but that doesn't seem very helpful in the handling of
   student information.
2. Some fields do make sense to have default value - for example, we could
   easily imagine that a student could be initialized in our system before they
   have a chance to define their major. In which case, we would default their
   `major` field to a value that indicates that they haven't picked a major yet.

Here is an example of our constructor that does exactly that:

```java
public Student(String firstName, String lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.major = "Undeclared";
}
```

We also have the ability to have multiple constructors
in a single class. In this example, we can add a constructor that accepts a
declared major in addition to the student's first and last name:

```java
    public Student(String firstName, String lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.major = "Undeclared";
    }

    public Student(String firstName, String lastName, String major) {
        this(firstName, lastName);
        this.major = major;
    }
```

Note that the new constructor makes use of the previously defined constructor to
initialize the two fields that were already supported and then proceeds to
initialize the additional field for which it received a value as a parameter.
