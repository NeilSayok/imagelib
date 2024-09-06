Lambda function are nameless functions in kotlin which are surrounded by `{}` used for defining block of codes that can be passed as parameters or stored in a variable.

```kotlin
val printName : () -> Unit = {println("My name is Sayok")}
```

We can also define lambdas to take in parameters and return some values.

```kotlin
val sum : (Int, Int) -> Int = {a : Int, b: Int -> a+b}
```

As variable has a return type which in Kotlin we define after `:`, we also define lambda type like below:

```
(<parameters>)-><return type>
```

We can send or not send parameters as per our needs and if the lambda function does not return any data then we can define the return type as `Unit`.

Now for example there is a lambda function as below :

```kotlin
val onlyPrintOneParam : (Int, Int) -> Unit = {a : Int, b: Int ->  print(a)}
```

As you see in the above expression we are only using the 1st variable `a` and `b` is not being used.

Here we can conver the function as below and use `_` instead of `b`. So the resulting function will look like below:

```kotlin
val onlyPrintOneParam : (Int, Int) -> Unit = {a : Int,_ ->  print(a)}
```

So what Kotlin will do is not allocate the 2nd variable in memory, thus saving some memory.

### Trailing Lambda 

So trailing lambda is a special function/lambda which takes another **lambda** as the last parameter.

```kotlin
val getFormattedSum : (Int, Int, (String)->Unit) -> Unit = {a, b, operation ->  operation("$a + $b = ${a+b}")}
getFormattedSum.invoke(10,3,{ out -> println(out) })
getFormattedSum.invoke(10,3) { out -> println(out) }
```

