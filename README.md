ForgeGradle
===========

Minecraft mod development framework used by Forge and FML for the gradle build system

This fork is intended for use for the GregTech: Community Edition team and its addons. Feel free to use it yourself, but we cannot guarantee any support or issue handling if we are not having issues ourselves with this fork.

## Instructions for 1.12.2:

In the `buildscript` section of `build.gradle`, add the Jitpack repository and update to the new Forge Maven:
\
Groovy:
```groovy
buildscript {
    repositories {
        mavenCentral()
        maven {
            url = "https://jitpack.io"
        }
        maven {
            url = "https://maven.minecraftforge.net/"
        }
    }
    dependencies {
        classpath("com.github.GregTechCE:ForgeGradle:FG_2.3-SNAPSHOT") {
            changing = true
        }
    }
}
```

Kotlin DSL:
```kotlin
buildscript {
    repositories {
        mavenCentral()
        maven {
            name = "jitpack"
            setUrl("https://jitpack.io")
        }
        maven {
            name = "forge"
            setUrl("https://maven.minecraftforge.net/")
        }
    }
    dependencies {
        classpath("com.github.GregTechCE:ForgeGradle:FG_2.3-SNAPSHOT") {
            isChanging = true
        }
    }
}
```
\
*: Note that the `changing`/`isChanging` is optional, and causes Gradle to refresh the dependency on each task execution. This is optional, and can sometimes even cause issues. If you have issues or do not want this feature, make sure to run:
```
./gradlew --refresh-dependencies
```
once you update your `build.gradle` or `build.gradle.kts`.
