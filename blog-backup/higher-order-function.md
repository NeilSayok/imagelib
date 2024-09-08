Higher order functions are functions in kotlin which takes functions as parameters. 


```kotlin
//Example
fun doSomething(a: Int, b: Int, onClick : ()-> Unit){
    // Fuction Body
}
```
These functions helps to customize the behaviour of a function. 

```kotlin 

fun main(){

    doSometing(a = 10,b = 20, onClick = {println(a+b)} )
    doSometing(a = 10,b = 20, onClick = {println(a-b)} )

}

```

In the above example if we see the function calls of the above 2 functions one is printing the sum of 2 numbers and the other is printing the difference of the two numbers event though we are using the same functions.

### Benifits of using higher order functions:

**1. Abstraction:** These fuctions only tell about how we can to implemement without giving up the details of the real implementation. 

**2. Flexible:** As we can see in the above, we can impliment addition feature and substraction feature.


We use higher order functions in kotlin to make the code more readable and maintainable. We can use higher order functions along with lambdas and write much more clean and efficient codes.