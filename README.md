# Couchbase-Lite-Android #

by Marty Schoch (marty@couchbase.com) + Traun Leyden (tleyden@couchbase.com)

**Couchbase-Lite-Android** is the Android port of [Couchbase Lite iOS](https://github.com/couchbase/couchbase-lite-ios).  

[Click here for the **official Couchbase Lite documentation**](http://docs.couchbase.com/couchbase-lite)

## Getting Started with Couchbase Lite

* Create your own Hello World Couchbase Lite by following the [tutorial](http://docs.couchbase.com/couchbase-lite/cbl-android/cbl-android-1.0b2/#tutorial) 
 
* Download and run the [Grocery-Sync](https://github.com/couchbaselabs/GrocerySync-Android) demo application

## Developing / Contributing to Couchbase Lite

If you are just building an application with Couchbase Lite, you can skip the rest of this document.  (see [Getting Started with Couchbase Lite](README.md#getting-started-with-couchbase-lite))

However, if you need to debug Couchbase Lite Android or otherwise hack on it, these instructions will help you do that.

## Prerequisites

* [Download Android Studio](http://developer.android.com/sdk/installing/studio.html) 

* Under Tools / Android / Android SDK Manager, install "Extras/Google Repository" and "Extras/Android Support Repository" (future versions of Android Studio may make this step unnecessary)


## Clone the repository

Use Git to clone the Couchbase Lite repository to your local disk: 

```
$ git clone git://github.com/couchbase/couchbase-lite-android.git
cd couchbase-lite-android
$ git submodule init && git submodule update
```

## Configure Android Studio SDK location

* `cp local.properties.example local.properties`
* Customize `local.properties` according to your SDK installation directory


## Importing Project into Android Studio

You should be able to import the project directly into Android Studio:

* Start Android Studio
* Choose File / Import and choose the couchbase-lite-android/CouchbaseLiteProject directory [screenshot](http://cl.ly/image/1d0w0J0H0x1u)
* Choose Import from External Model and make sure Gradle is selected [screenshot](http://cl.ly/image/2Y1m0O3U1Q2I)
* Check the *auto-import* and the *Use gradle wrapper (recommended)* checkboxes [screenshot](http://cl.ly/image/1I0r1x2J032i)
* Hit Finish and wait for all tasks to finish (may take a while)

After it's finished with the import, it should look [like this](http://cl.ly/image/3R3X0Q3o1H09)

## Working around Import bugs

At this point, unfortunately, if you open the `CBLServer` class, it will look like [this](http://cl.ly/image/2C1M0F1T330t).  Android Studio will say it cannot resolve some objects.  This seems to be due to a bug in the import process.  

To fix this:

* Go to File / Project Structure
* Choose Modules
* Choose the CBLite module
* Change the jackson-core-asl-1.9.2 and jackson-mapper-asl-1.9.2 dependencies from "test" to "compile" [screenshot](http://cl.ly/image/16113r0M2J2G)
* Hit Apply

_Note_: you may need to do this in other places for other libraries if you run into situations where Android Studio cannot resolve code.

_Note_: the above workarounds are only needed for Android Studio, and even without these the command line gradle builds should still work.

## Running tests

See the [Running the Test Suite](https://github.com/couchbase/couchbase-lite-android/wiki/Running-the-test-suite) wiki page.

## Building and deploying maven artifacts.

If you want to host and deploy your own maven artifacts, see the `upload_android_artifacts.sh` script.


## Example Apps

* [GrocerySync](https://github.com/couchbaselabs/GrocerySync-Android)
* [LiteServAndroid](https://github.com/couchbaselabs/LiteServAndroid)
* [CouchChatAndroid](https://github.com/couchbaselabs/CouchChatAndroid) -- just a stub at this point.

## Utilities

* [CBLiteConsole](https://github.com/couchbaselabs/CBLiteConsole)

## Current Status
- Beta

## Requirements
- Android 2.3 Gingerbread (API level 9) and above.


## License
- Apache License 2.0

[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/bc53967fe3191ba75b4a62c9372d9928 "githalytics.com")](http://githalytics.com/couchbase/couchbase-lite-android)
