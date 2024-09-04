String interpolation in Kotlin is a powerful feature that allows developers to easily incorporate variables, expressions, and even complex calculations directly within string literals. This feature simplifies the process of creating dynamic strings and can make the code more readable and maintainable.

The syntax for interpolation is to put `$` symbol follwed by variable name. If you are using a complex data type/ operations you can use (`${}`). 

Example: 

```kotlin
val name = "Sayok"
val age = 30

print("My name is $name and age is ${age-5}.")
```

Output of the above code will be:

```
My name is Sayok and age is 25.
```


If we have a complex data type like a data class:

```kotlin
data class Person(val name: Sting, val age: Int)

fun main(){
  val user = Person(name="Neil", age=26)
  print("My name is ${user.name} and age is ${person.age}.")
}
```
Output of the above code will be:

```
My name is Neil and age is 26.
```

So we have learnt how to write the code in Kotlin, but now we will see what happens under the hood. 

To understand it we need to decompile the below code:

```kotlin
val name = "Sayok"
val age = 30
val finalString = "My name is $name and my age is ${age-5}"    
```

Decompiled:

```java
String name = "Sayok";
int age = 30;
String finalString = (new StringBuilder()).append("My name is ").append(name).append(" and my age is ").append(age - 5).toString();
```

So Kotlin compiler will use String builder to concatenate the string.This is done to avoid creating multiple string objects, which would happen if simple concatenation (like "Hello, " + name + "!") were used.

But sometime to optimize the code Kotlin Compiler will decompile the code to:

```java
String name = "Sayok";
int age = 30;
String finalString = "My name is " + name + " and my age is " + age-5"    
```

This would happen to make the code use less memory space and do the concatenation in place.



