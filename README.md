## Quick Start
**ProGuard is integrated in Google's Android SDK. If you have an Android Gradle project you can enable ProGuard instead of the default R8 compiler:**

**1.Disable R8 in your gradle.properties:**

  - *android.enableR8=false*
  - *android.enableR8.libraries=false*
  
**2.Override the default version of ProGuard with the most recent one in your main build.gradle:**

`buildscript {
    //...
    configurations.all {
        resolutionStrategy {
            dependencySubstitution {
                substitute module('net.sf.proguard:proguard-gradle') with module('com.guardsquare:proguard-gradle:7.0.1')
            }
        }
    }
}
`

**3.Enable minification as usual in your build.gradle:**

`android {
    //...
    buildTypes {
        release {
            minifyEnabled   true
            shrinkResources true
            proguardFile getDefaultProguardFile('proguard-android-optimize.txt')
            proguardFile 'proguard-project.txt'
        }
    }
}
`
**4.Add any necessary configuration to your proguard-project.txt.**

