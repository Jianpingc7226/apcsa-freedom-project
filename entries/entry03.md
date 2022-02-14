# Entry 3
##### 2/13/2022

### Progress
Thought the past few weeks, I been watching several videos on YouTube that helps to understand how Android Studio work and tools that the application needed be for running it. The video I watch is [Android Development for Beginners - Full Course](https://www.youtube.com/watch?v=fis26HvvDII&t=2094s) and [#1 Login and Registration Android App Tutorial Using Firebase Authentication - Create User](https://www.youtube.com/watch?v=Z-RE1QuUWPg&t=195s). I try to start building our minimum viable product start with building the user authanticaiton page. But I realize that before doing that I have to learn more about Android Studio applycation first, because before I start coding, just loading that empty page cause several bug. And so, I had spend another week start learning the small part of android studio and try to debug.
### Problem I encountered
#1 Before running and checking with code I learned, I first need a AVD (Android Vitual Device) system inorder to run our project on a virtual android app. Before we thought that we will need to set up the AVD by our self and needed to download an app call BlueStacks, but then we realized that Android Studio have it's own AVD that we need to set up with in it.
    
#2 After set up the AVD I tried to run the app without any code in it to make sure we set everything up correctly, but we first encounter bugs one after one. 

```'android.useAndroidX' property is not enabled```
 This is the first bug I encounter is when run the app to see the change I made, by searching up I know that this bug happen becasue my project uses AndroidX dependencies, but the 'android.useAndroidX' property is not enabled.
 >Solution - I added the following code into my Gradle.properties located in SDK file. 

``` java
android.useAndroidX=true
android.enableJetifier=true
```

![myimage-alt-tag](screenshot.png)

[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)