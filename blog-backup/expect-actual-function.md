Compose Multiplatform allows you to write code that seamlessy run on Android,IOS,Desktop and Web. However there are scenarios where we need to write custom code for each and every platform.This is where the `expect` and `actual` pair comes into play.

### Understanding the `expect`/`actual` keywords:

- **expect** : This keyword is used in the common code and it tells Kotlin that while compiling the code this part of it is written in the platform specific folders. It tell us that a platform specific implimentation is required to be written.

- **actual** : This keyword is used in the platform specific code. `actual` functions or properties are written in the specific platform code base, which during the compilation of the code for that specific platform replaces the `expect` declaration.


### Lets learn through an example: 

In Compose Multiplatform when we use `Ktor` it comes with different engines for all different platforms.

| Platform  | Ktor Network Engine  |
|---|---|
| Android  | `OkHttp`  |
| IOS  |  `Darwin` |
|  Desktop | `CIO`  |
|  Web(WasmJs) |  `Js` |

So while creating the `HttpClient` for the network calls we will be required to send Platform specific engines. So the code will look something like below:

```kotlin
val httpClient : HttpClient = 
    HttpClient(<platform_specific_engine>) {
        //Do Other Stuff
    }
```

So to achieve this we will use the `expect`/`actual` pair:

In the `commonMain` directory we will write the `expect` function and the `actual` function will be written in the respective platform specific directories - `androidMain`,`iosMain`,`desktopMain`,`wasmJsMain`.

**So lets create the expect function in `commonMain`:**

- File :- _commonMain.HttpClient.kt_

    ```kotlin
    expect fun getHttpClient() : HttpClient
    ```

Now we will have to write its real implementations in the respective folders:

- File :- _androidMain.HttpClient.android.kt_

    ```kotlin
    import io.ktor.client.HttpClient
    import io.ktor.client.engine.okhttp.OkHttp

    actual fun getHttpClient(): HttpClient {
        return HttpClient(OkHttp) {
            //DO OTHER STUFF
        }
    }
    ```

- File :- _iosMain.HttpClient.ios.kt_

    ```kotlin
    import io.ktor.client.HttpClient
    import io.ktor.client.engine.darwin.Darwin

    actual fun getHttpClient(): HttpClient {
        return HttpClient(Darwin) {
            //DO OTHER STUFF
        }
    }
    ```
- File :- _desktopMain.HttpClient.desktop.kt_

    ```kotlin
    import io.ktor.client.HttpClient
    import io.ktor.client.engine.cio.CIO

    actual fun getHttpClient(): HttpClient {
        return HttpClient(CIO) {
            //DO OTHER STUFF
        }
    }
    ```
- File :- _wasmJsMain.HttpClient.wasmJs.kt_

    ```kotlin
    import io.ktor.client.HttpClient
    import io.ktor.client.engine.js.Js

    actual fun getHttpClient(): HttpClient {
        return HttpClient(Js) {
            //DO OTHER STUFF
        }
    }
    ```

We can also do the same with `var/val` the syntax will become something like `expect var baseUrl: String`

### Steps to do this using Android Studio



![Declaer Expect function](https://neilsayok.github.io/imagelib/images/blog/expect-actual-function/1-declare.png)

