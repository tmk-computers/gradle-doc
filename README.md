# gradle-doc
Gradle documentation for beginners

## What is gradle
- Gradle is an open-source build automation tool focused on flexibility and performance. 
- Gradle build scripts are written using a Groovy or Kotlin DSL

## Installation

- Install JDK for your operating system
- download binary gradle distribution from https://gradle.org/releases
- set **JAVA_HOME** environment variable which points to your JDK installation
- set **GRADLE_HOME** environment variable which points to your Gradle binary directory
- append JDK bin directory path and gradle bin directory path to PATH environment variable
- check JDK installed and configured correctly
  - javac -version
- check gradle configured correctly
  - gradle -v
  
## The Gradle Wrapper
- The Wrapper is a script that invokes a declared version of Gradle, downloading it beforehand if necessary. As a result, developers can get up and running with a Gradle project quickly without having to follow manual installation processes saving your company time and money.

- benefits:
  - Standardizes a project on a given Gradle version, leading to more reliable and robust builds.
  - Provisioning a new Gradle version to different users and execution environment (e.g. IDEs or Continuous Integration servers) is as simple as changing the Wrapper definition.
  
- Add the Gradle Wrapper with command
  - gradle wrapper
  
        ├── build.gradle
        ├── settings.gradle
        ├── gradle
        │   └── wrapper
        │       ├── gradle-wrapper.jar
        │       └── gradle-wrapper.properties
        ├── gradlew
        └── gradlew.bat



