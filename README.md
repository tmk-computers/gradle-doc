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
  
## Gradle commands

### Project Initialization

- Creating new Gradle builds : Use the built-in gradle init task to create a new Gradle builds, with new or existing projects.
  - > mkdir basic-demo
  - > cd basic-demo
  - > gradle init

  - **gradle init** command creates below files automatically
  
        ├── build.gradle  
        ├── gradle
        │   └── wrapper
        │       ├── gradle-wrapper.jar  
        │       └── gradle-wrapper.properties  
        ├── gradlew  
        ├── gradlew.bat  
        └── settings.gradle  
  
  
- You can also pass application type as a type parameter to specify project type like java-application, java-library, etc.
  - gradle init --type java-library
  
- The built-in gradle wrapper task generates a script, gradlew, that invokes a declared version of Gradle, downloading it beforehand if necessary.
  - gradle wrapper --gradle-version=4.4
  
### Create task

- Gradle provides APIs for creating and configuring tasks through a Groovy or Kotlin-based DSL. A Project includes a collection of Tasks, each of which performs some basic operation.
- Gradle comes with a library of tasks that you can configure in your own projects. For example, there is a core type called Copy, which copies files from one location to another. 
- Open build.gradle file and add below code to it.

      task copy(type: Copy, group: "Custom", description: "Copies sources to the dest directory") {
        from "src"
        into "dest"
      }
- Now execute your new copy task:
  - ./gradlew copy

- The tasks command lists Gradle tasks that you can invoke, including those added by the base plugin, and custom tasks you just added as well.
  - ./gradlew tasks
  
### Discover available properties
- The properties command tells you about a project’s attributes.
  - ./gradlew properties

  
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

## Create Java Project with gradle
- run below commands
  - gradle init --type java-application
  
  

The init task runs the wrapper task first, which generates the gradlew and gradlew.bat wrapper scripts. Then it creates the new project with the following structure:

        ├── build.gradle
        ├── gradle   
        │   └── wrapper
        │       ├── gradle-wrapper.jar
        │       └── gradle-wrapper.properties
        ├── gradlew
        ├── gradlew.bat
        ├── settings.gradle
        └── src
        ├── main
        │   └── java  
        │       └── App.java
        └── test      
        └── java
            └── AppTest.java

    - Generated folder for wrapper files
	  - Default Java source folder
	  - Default Java test folder

- Review the generated project files
- The **settings.gradle** file is heavily commented, but has only one active line:

      rootProject.name='java-demo'

- This assigns the name of the root project to java-demo, which is the default.

- The generated build.gradle file also has many comments. The active portion is reproduced here (note version numbers for the dependencies may be updated in later versions of Gradle):
**build.gradle**

      plugins {
        id 'java'
        id 'application'
      }

      repositories {
        jcenter()  
      }

      dependencies {
        compile 'com.google.guava:guava:21.0'  
        testCompile 'junit:junit:4.12'         
      }

      mainClassName = 'App'  

	  - public Bintray Artifactory repository
	  - Google Guava library
	  - JUnit testing library
	  - Class with "main" method (used by Application plugin)
    
#### Execute the build

- To build the project, run the build command. You can use the regular gradle command, but when a project includes a wrapper script, it is considered good form to use it instead.
  - ./gradlew build
- The run task tells Gradle to execute the main method in the class assigned to the mainClassName property.
  - ./gradlew run
