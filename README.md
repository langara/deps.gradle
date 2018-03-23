# deps.gradle

This repo allows to easily share current versions of well known libraries for Kotlin/Java/Android between projects.

## This project is deprecated. Use [github:deps.kt](https://github.com/langara/deps.kt) instead.

Example:

Main `build.gradle` file:
```groovy
buildscript {
    apply from: 'deps.gradle'
    //...
}

```

Subproject `build.gradle` file:
```groovy
apply plugin: 'com.android.application'
apply plugin: 'kotlin-android'
apply plugin: 'kotlin-android-extensions'

android {
    compileSdkVersion vers.androidCompileSdk
    buildToolsVersion vers.androidBuildTools


    defaultConfig {
        applicationId "pl.elpassion.iot.commander"
        minSdkVersion vers.androidMinSdk
        targetSdkVersion vers.androidTargetSdk
        versionCode 1
        versionName "1.0"

        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"

    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}

dependencies {
    implementation project(':loggers')
    implementation project(':iot-api')
    implementation deps.kotlinStdlib
    implementation deps.rxbindingKotlin
    implementation deps.rxrelay
    implementation deps.rxlifecycleComponents
    implementation deps.rxlifecycleKotlin
    implementation deps.androidSupportAppcompat
    testImplementation deps.junit
    testImplementation deps.mockitoKotlin
}
```
    
