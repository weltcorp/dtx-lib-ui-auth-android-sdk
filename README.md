# dtx-lib-ui-learning-android-sdk

[![](https://jitpack.io/v/weltcorp/dtx-lib-ui-learning-android-sdk.svg)](https://jitpack.io/#weltcorp/dtx-lib-ui-learning-android-sdk)

dtx-lib-ui-learning-android-sdk is an Android UI-Learning library for DTx Application. This library is published on JitPack and can be easily integrated into your Android projects. It is written in Kotlin and is released under the MIT License.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Installation

To use dtx-lib-ui-learning-android-sdk in your project, add the following to your project-level build.gradle or setting.gradle file:

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
def UI_LEARNING_SDK_VERSION = LATEST_JITPACK_VERSION_OF_SDK

dependencies {
    implementation "com.github.weltcorp:dtx-lib-ui-learning-android-sdk:$UI_LEARNING_SDK_VERSION"
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
            // Initialize the Learning SDK
            WeltDtxLearning.init(
                application = this,
                env = BuildConfig.BUILD_ENV, // Set in build.gradle(:app)
                projectId = PROJECT_ID
            )
        } catch (e: Exception) {
            e.printStackTrace()
        }
    }
}
```

### - Open LearningLesson

Open learning contents page with lesson_id.

```kotlin
{
    // Open the Learning contents page
    WeltDtxLearning.openLearningLesson(
        YOUR_ACTIVITY as ComponentActivity,
        routeName = "learning-pages",
        lessonId = LESSON_ID
        userId = USER_ID
        token = ACCESS_TOKEN_API_HEADER
    )
}
```

## License

dtx-lib-ui-learning-android-sdk is released under the MIT License. See the LICENSE file for more details.
