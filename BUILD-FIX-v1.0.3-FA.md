# اصلاح Build نسخه 1.0.3

خطای GitHub Actions:

```text
Using 'jvmTarget: String' is an error. Please migrate to the compilerOptions DSL.
```

در `app/build.gradle.kts` بلوک قدیمی زیر حذف شد:

```kotlin
kotlinOptions { jvmTarget = "17" }
```

و با DSL جدید Kotlin جایگزین شد:

```kotlin
import org.jetbrains.kotlin.gradle.dsl.JvmTarget

kotlin {
    compilerOptions {
        jvmTarget.set(JvmTarget.JVM_17)
    }
}
```

این تغییر با Kotlin 2.4.21 و AGP 8.13.2 سازگار است.
