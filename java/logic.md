# Operators

- ## Mathematical Operators

  - Example: `+` ,` -` , `*`(multiplication) ,` /` (division), `++`(increment) , `--`(decrement)

- ## Relational Operators

  - Example:`==`(equal to), `!=` (not equal to), `>`(greater than) ,` <`(less than), `>=`(greater to equal to), `<=`(less than or equal to)

- ## Logical Operators

  - Example: `&&`(and), `||`(or), `!`(not)

- ## Conditional Operator(`? :`)

  - Usage:

    ```java
    expression ? "value if true" : "value if false"
    ```

# Loop Logic

- ## While Loop(Kind Out-of Date)

  - Repeats a statement or group of statements while a given condition is true. It tests the condition before executing the loop body.

    ```java
    int i = 0;
    while(i < 10){
      //Do something 10 times in the while loop
      i++;
    }
    ```

- ## For Loop

  - "Upgrade Version" of while loop

    ```java
    for(int i = 1;i < 10;i++){
      //Do something 10 times in this for loop
    }
    ```

- ## Do...While Loop

  - Like while loop, but it test the condition at the end of the loop body.

    ```java
    do{
      i++;
      //Do something 10 times in thi do..While loop
    }while(i < 10);
    ```

# Decision Making

- ## If Statement


  ```java
  if(condition is true){
    //Execute this code
  }
  ```

- ## If...else statement

  ```java
  if(condition is true){
    //Execute this code
  }else{
    //Excute this code
  }
  ```

- ## Switch case statement

  ```java
  switch(expression){
      case 'a':
      //run code when exp. return 'a'
      break;
      case 'b':
      //run code when exp. return 'b'
      break;
      case 'c':
      //run code when exp. return 'c'
      break;
      default:
      //run code that are not in any case
  }
  ```