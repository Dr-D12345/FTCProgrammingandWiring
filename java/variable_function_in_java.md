# Declare a Variable

```java
int myNumber;
myNumber = 5;
```

OR

```java
int myNumber = 5;
```

# Declare a Function Method

In Java, all function definitions must be inside classes. We also call functions methods. 

```java
public class Main {
    public static void myFunc(int x,int y) {       
        //Do something here
    }
}
```

`myFunc` is a method we defined in class `Main`. Notice a few things about `myFunc`.

- `static` means this method belongs to the class `Main` and not to a specific instance of `Main`. Which means we can call the method from a different class like that `Main.foo()`.
- `void` means this method doesn't return a value. Methods can return a single value in Java and it has to be defined in the method declaration. However, you can use `return` by itself to exit the method.
- This method two arguments,`int x` and`int y`
  - The `int` tell us what data type of those two arguments
  - The `x` and `y`is the argument passed in to the function method.