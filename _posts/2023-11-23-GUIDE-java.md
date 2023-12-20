---
title: Java Guide
slug: java-guide
date: 2023-11-23
category: guide
---
## Java Guide
Welcome to my large(ish) java guide!

### The basics
First, you probably want to know some data types, those are key to everything.

But... how you plan to run and develop this java code? Simple. You are gonna want to get your hands on [IntelliJ IDEA](https://www.jetbrains.com/idea/download/), make sure to scroll down and get the Community Edition, it's free so no worries there. (For this tutorial I am using 2023.2)

Now creating a project is easy, select "New Project", it should look something like this

<img src="/images/screenshots/java_guide/image1.png">

Your JDK may look different, I recommend JDK 17 or higher as that has the main features you'll need.

Alright, you've got your project ready, wonderful!

Open the src folder, then java, and navigate to the "Main" file, that's the file you'll be editing. (Also keep note of pom.xml as that's how you'll add libraries)

<img src="/images/screenshots/java_guide/image2.png">

Now, everything must be in a class for java, so this means everything we do (except imports) must be in our "Main" class. To rename this class you must also change the file name to the same as the class name. You'll see a function called "main", that function's name and args cannot be changed, this is what will run when users run your java code (likely using a jar file). Currently running this will print "Hello world!" to the console, let's say we want to do something different though, how do you store a variable? Well depending on the use of this variable, it can be in many places. Let's make the variable global to this class so other functions can use it.

```java
package net.example;

public class Main {
    private static final String myVariable = "My String Variable!";
    
    public static void main(String[] args) {
        System.out.println("Hello world!");
    }
}
```

Ok ok, let's break down what we just did. We added the line `private final String myVariable = "My String Variable!";`, but what does that mean?

Setting the variable as `private` is used to make sure that no other classes can use this variable, only your class can use this variable. Let's go through the meaning of public and protected now:

`public` means anything can access the variable (or function!) while `protected` means anything in your package path can use it. For example the current file we have is `net.example.Main`, so if we had `net.example.Something`, that "Something" class can access the variable/function. However if `net.example2.Main` tried to access this variable/function, it would not work, they are in to different package paths.

Now what does the static mean? Well in this context it's not actually useful but it means we can talk about it. If the variable was `public`, the static means they can just import `net.example.Main.myVariable`, if there is no static then the class must find a way to get an instance of class, no instance no variable.

We're nearly done, `final` means this variable cannot be changed, so a constant. See how the type is `String`. That's important as this can be many things. One thing you may want to understand is that everything in java is a class (almost), so the String is just a String class, your variables can be a class of your own if you wanted! Let's say we had `net.example.Something`, we would then have the variable as:

```java
package net.example;

import net.example.Something;

public class Main {
    private static final Something myVariable = new Something();
    
    public static void main(String[] args) {
        System.out.println("Hello world!");
    }
}
```

We just imported that other class so we can use it, imports aren't needed per say, but your code will get pretty ugly as you can do this.

```java
package net.example;

public class Main {
    private static final net.example.Something myVariable = new net.example.Something();
    
    public static void main(String[] args) {
        System.out.println("Hello world!");
    }
}
```

It's not the greatest is it? Imports are better for sure, use imports.

Now let's make a function in our main class!

```java
package net.example;

public class Main {
    private static final String myVariable = "My String Variable!";

    public static void main(String[] args) {
        System.out.println("Hello world!");
        myFunction(myVariable);
    }
    
    public static void myFunction(String input) {
        System.out.println(input);
    }
}
```

Now we have a function that runs after printing "Hello world!", also a little note, to print something to the console you use `System.out.println();`

You can see the function is `public` and is `static` but what does `void` mean? Well void means this function returns nothing. Let's make a function that does return something to show how that works!

```java
package net.example;

public class Main {
    private static final String myVariable = "My String Variable!";

    public static void main(String[] args) {
        System.out.println("Hello world!");
        myFunction(getMyVariable());
    }

    public static void myFunction(String input) {
        System.out.println(input);
    }
    
    public static String getMyVariable() {
        return myVariable;
    }
}
```

See that class `String` again? That's the key, put the class of the thing you are going to return, simple right?

But let's explain the parameter for a second, it's simple, class name then the variable you want to assign the parameter to, for this example the variable `input` is used.

Now let's shake things up a little bit!

```java
package net.example;

public class Main {
    private static final String myVariable = "My String Variable!";
    private static final Boolean shouldRun = true;

    public static void main(String[] args) {
        System.out.println("Hello world!");
        if (shouldRun) {
            myFunction(getMyVariable());
        }
    }

    public static void myFunction(String input) {
        System.out.println(input);
    }

    public static String getMyVariable() {
        return myVariable;
    }
}
```

Now we have a `Boolean` class! Note: for the purposes of this guide I have used the `Boolean` class and not the primative type, the `Boolean` class has some extra things a new java developer can use.

We also have an if statement! The Java compiler will calculate the conditions in the if statement, if it's true it will run. However since we put in `true` as the input, we know the code will always run. Here is an example where the `myFunction` will never run:

```java
package net.example;

public class Main {
    private static final String myVariable = "My String Variable!";
    private static final Boolean shouldRun = false;

    public static void main(String[] args) {
        System.out.println("Hello world!");
        if (shouldRun) {
            myFunction(getMyVariable());
        }
    }

    public static void myFunction(String input) {
        System.out.println(input);
    }

    public static String getMyVariable() {
        return myVariable;
    }
}
```

Let's tell the user if we aren't running the function

```java
package net.example;

public class Main {
    private static final String myVariable = "My String Variable!";
    private static final Boolean shouldRun = false;

    public static void main(String[] args) {
        System.out.println("Hello world!");
        if (shouldRun) {
            myFunction(getMyVariable());
        } else {
            System.out.println("Not running myFunction!");
        }
    }

    public static void myFunction(String input) {
        System.out.println(input);
    }

    public static String getMyVariable() {
        return myVariable;
    }
}
```

We can see an `else` now, this will run if the if statement did not run. But what if I want to chain these if statements? `else if`!

```java
package net.example;

public class Main {
    private static final String myVariable = "My String Variable!";
    private static final Boolean shouldRun = false;

    public static void main(String[] args) {
        System.out.println("Hello world!");
        if (shouldRun) {
            myFunction(getMyVariable());
        } else if (myVariable.equalsIgnoreCase("")) {
            System.out.println("myVariable contains data!");
        } else {
            System.out.println("Not running myFunction!");
        }
    }

    public static void myFunction(String input) {
        System.out.println(input);
    }

    public static String getMyVariable() {
        return myVariable;
    }
}
```

Now if the `myVariable` is not an empty string it will print "myVariable contains data!"

For now that's the end of the guide, I'll add to this more and more as time passes, enjoy Java!