## Definitions

**Declarative solution** is the process where we/programmer declare *what* to do — the program does that.

**Imperative solution** is the process where we/programmer tell *how* to do a particular task, and the program does it for us.

---

## Comparison

| | Imperative | Declarative |
|---|---|---|
| **Power** | Programmer defines all the steps | The programmer tells the program how to do it without defining the underlying steps |
| **Amount of Code** | More | Less |
| **Control Flow** | Defined explicitly | Abstracted away |
| **State Management** | Managed by programmer | State manages the outcome |
| **Example** | Filter evens: `for (i in array) if (i % 2 == 0) print(i)` | `array.filter(i % 2 == 0)` |
| **Language** | C, C++, Java, Kotlin | SQL, HTML, CSS |
| **UI Framework** | XML + Java/Kotlin | Jetpack Compose |

---

## Even though Kotlin is Imperative, how is Jetpack Compose Declarative?

In reality, **DECLARATIVE** is just a wrapper written over **IMPERATIVE** code.

So in reality:

```kotlin
arr.filter { condition }
```

is equivalent to:

```kotlin
for (i in arr) {
    if (condition) {
        // ...
    }
}
```

---

## Jetpack Compose — Declarative Wrapper over Imperative Kotlin

Basically, Jetpack Compose is a **declarative wrapper** over imperative Kotlin.

Compose also uses **state**, which in turn decides how the UI is being shown.

### Example: Compose vs XML + Kotlin

#### Compose (Declarative)

```kotlin
@Composable
fun ShowText(isLoggedIn: Boolean) {
    if (isLoggedIn)
        Text("Logged In")
    else
        Text("Not Logged In")
}
```

> Here we are just passing the function the **state** and it decides what to show.
> Changing the state will cause **recomposition**.

#### XML + Kotlin (Imperative)

```kotlin
fun updateUI(isLoggedIn: Boolean) {
    if (isLoggedIn) {
        textView.text = "Logged In"
    } else {
        textView.text = "Not Logged In"
    }
}
```

> Here the UI is already declared. Then using the code we are setting the values using **getter/setter**.
> As the value passed is stateless, the developer needs to update it **manually**.

---

## Key Difference: When Decisions Are Made

| | Compose | XML + Kotlin |
|---|---|---|
| **When UI decisions are made** | During **runtime** — drawn and taken during runtime | During **compile time** — only properties of items can be changed at runtime |