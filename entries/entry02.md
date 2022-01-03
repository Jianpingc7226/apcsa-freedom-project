# Entry 2
##### 12/20/21

## What I had done so far

  Me and my partner are starting to set up android studios and firebase within it. During the break, I watch the video [tutorial](https://www.youtube.com/watch?v=dRYnm_k3w1w) and the [document description](https://firebase.google.com/docs/android/setup). After spend a couple hours of reading and try out, I had understand the concept of setting up firebase on android studio.
    
## What I learned so far

  Android Studios have a plugin named Gradle, a build automation tool that will help process the setup of firebase in android studio with just few line of code.
  
##### **First step-**
  First, we will need to add rules to include the Google Services Gradle to the build.gradle in the project-level of android studio. 
```Java
buildscript {

  repositories {
    // Check that you have the following line (if not, add it):
    google()  // Google's Maven repository
  }

  dependencies {
    // ...

    // Add the following line:
    classpath 'com.google.gms:google-services:4.3.10'  // Google Services plugin
  }
}

allprojects {
  // ...

  repositories {
    // Check that you have the following line (if not, add it):
    google()  // Google's Maven repository
    // ...
  }
}
```

###### **Second step-**
  On another build.gradle document apply the Google Service Gradle plugin that has just been added in the previous step.
  
```Java
apply plugin: 'com.android.application'
// Add the following line:
apply plugin: 'com.google.gms.google-services'  // Google Services plugin

android {
  // ...
}
```
  and then add the SDKs of the Gradle file (app/build.gradle). Based on the [Available libararies](https://firebase.google.com/docs/android/setup#available-libraries), I add the Authentication, Cloud Firestore, and firebase real-time database to my app.
  
```Java
...
dependencies {
    implementation platform('com.google.firebase:firebase-bom:29.0.0') //Automatically update existing firebase components
    implementation 'com.google.firebase:firebase-auth'//firebase authentication
    implementation 'com.google.firebase:firebase-firestore'//firebase cloud firestore
    implementation 'com.google.firebase:firebase-database'//firebase realtime database
    implementation 'com.android.support.constraint:constraint-layout:2.0.4'
    implementation 'android.arch.navigation:navigation-fragment:1.0.0'
    implementation 'android.arch.navigation:navigation-ui:1.0.0'
    testImplementation 'junit:junit:4.+'
    androidTestImplementation 'com.android.support.test:runner:1.0.2'
    androidTestImplementation 'com.android.support.test.espresso:espresso-core:3.0.2'
}
```

## Process
  Now we are planning the most promising solution, discussing features of our project, and learning our tool. During our learning, the skills we use are **Communication** and **How to Google**. We created a discord channel for our freedom project and share the link to articles, tutorials, or websites we found that will help on google.


[Previous](entry01.md) | [Next](entry03.md)

[Home](../README.md)