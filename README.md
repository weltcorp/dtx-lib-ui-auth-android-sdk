# dtx-lib-ui-auth-android-sdk

[![](https://jitpack.io/v/weltcorp/dtx-lib-ui-auth-android-sdk.svg)](https://jitpack.io/#weltcorp/dtx-lib-ui-auth-android-sdk)

dtx-lib-ui-auth-android-sdk is an Android UI-Learning library for DTx Application. This library is published on JitPack and can be easily integrated into your Android projects. It is written in Kotlin and is released under the MIT License.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [License](#license)

## Installation

To use dtx-lib-ui-auth-android-sdk in your project, add the following to your project-level build.gradle or setting.gradle file:

```gradle
allprojects {
    repositories {
        ...
        maven { url "https://jitpack.io" }
    }
}
```

Next, add the following dependency to your module-level build.gradle file:

```gradle
def UI_AUTH_SDK_VERSION = LATEST_JITPACK_VERSION_OF_SDK

dependencies {
    implementation "com.github.weltcorp:dtx-lib-ui-auth-android-sdk:$UI_AUTH_SDK_VERSION"
}
```

Make sure to replace YourUsername with your actual GitHub username.

## Usage

### - Initialize

After adding the library to your project, you have to initialize first in your Application before use the SDK.

```kotlin
class YourCustomApplication: Application() {
    override fun onCreate() {
        super.onCreate()

        try {
            // Initialize the Auth SDK
            WeltDtxAuth.init(
                application = this,
                env = BuildConfig.BUILD_ENV,
                projectId = PROJECT_ID,  // Set in build.gradle(:app)
                appToken = APP_TOKEN,
                serviceName = SERVICE_NAME
            )
        } catch (e: Exception) {
            e.printStackTrace()
        }
    }
}
```

### - Login

```kotlin
fun login() {
    WeltDtxAuth.login(
        YOUR_ACTIVITY as ComponentActivity,
        object : LoginListener {
            override fun onSuccess(user: LoginUser) {
                // Do something on success with user
            }
            override fun onError(error: WeltDtxAuthError) {
                // Do something on error
            }
            override fun onCancel() {
                // Do something on cancel
            }
        }
    )
}
```

## License

dtx-lib-ui-auth-android-sdk is released under the MIT License. See the LICENSE file for more details.
