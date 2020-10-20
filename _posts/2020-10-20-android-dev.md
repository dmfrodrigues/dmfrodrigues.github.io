---
layout: post
title: "Developing for Android in 2020"
date: 2020-10-20 01:20:00 +0100
---

## Installing

### Java

Android SDK manager has [known issues with Java 11](https://stackoverflow.com/questions/47150410/failed-to-run-sdkmanager-list-with-java-9/57732921#57732921). If you have Java 11 installed, you have two not-too-complicated alternatives under Ubuntu: downgrade to Java 8, or upgrade to Java 14 (I chose the latter). They are available through `apt` as packages `openjdk-8-jdk` and `openjdk-14-jdk` (and you should absolutely be running the JDK, not the JRE as gradle will complain about that on building, which can be a pain in the ass).

To choose the right version of Java, run
```sh
sudo update-alternatives --config java
```
and pick your preferred version. Then run `java -version` just to double-check the version.

### Flutter

You can always follow the [official guidelines](https://flutter.dev/docs/get-started/install/linux); either way, here are the commands you need to run:

```sh
sudo snap install --classic flutter
```

To check if everything is working properly, run
```sh
flutter doctor
```
to diagnose possible problems, and try to fix them.

### Android Studio

Run

```sh
sudo snap install --classic android-studio
```

Then, open it, select all default options, and [install the Flutter and Dart plugins](https://flutter.dev/docs/get-started/editor?tab=androidstudio). Now, restart Android Studio, and create a new Flutter project.

### Project

It is possible that you might have to [change the gradle version](https://stackoverflow.com/questions/61289461/java-lang-noclassdeffounderror-could-not-initialize-class-org-codehaus-groovy-v). After doing that, try to compile by selecting "Run" in the upper right corner (you have to select a VM first). If it complains about not having accepted some licenses, open the shell, go to `~/Android/Sdk/tools/bin`, run `./sdkmanager --licenses` and accept all licenses. Now try to recompile, and it should hopefully (and finally!) work.
