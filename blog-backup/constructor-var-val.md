In Kotlin, while creating a class we can pass the parameters to its constructor in these 2 ways:

| Test(a : <Data Type>)| Test(var/val a: <Data Type>) |
|:-----|:--------:|
	
In this blog we will understand what is the difference between them.

So putting var/val will make the variable a property of the class and not putting it will make it a parameter of only the constructor function.

So what does it mean, to understand lets look into some code in Kotlin:

```kotlin
class Test(a: Int){}
```
Now Lets see the decompiled java code:

```java
public final class Test {
   public Test(int a) {
   }
}
```

So now if I try to access ```a``` using the object of ```Test()``` like the below code:
```java
Test t = new Test(10);
t.a //Error 
```

It will give me error. ```Unresolved reference: a```. Why because `a` is a parameter of the constructor only.

Now if we put var/val in the paramater like below:
```kotlin
class Test(var a: Int){}
```
The decompliked Java code will become:
```java
public final class Test {
   private int a;

   public final int getA() {
      return this.a;
   }

   public final void setA(int var1) {
      this.a = var1;
   }

   public Test(int a) {
      this.a = a;
   }
}
```

Thus it will not only give you a class property but also give you getter/setters for setting the values.

Now the next question arises if the field `a` is `private` how can it be accessed. Simple answer in Java you cannot, i.e. if you are calling the KT class from a Java you will not be able to assign value of `a` like ```Test(1).a = 10``` but will have to use ```Test(1).setA(5)```.
But as kotlin internally handles getters/setters Test(1).a = 5 will be ok.
