---
title: Installation Guide
---

# Installation Guide

This guide will walk you through the steps to install and set up Dawncord for your Discord bot development using either Maven or Gradle.

## Prerequisites

Before you begin, make sure you have the following prerequisites installed:

- Java Development Kit (JDK) version 17 or higher
- Maven (for Maven installation)
- Gradle (for Gradle installation)

## Installation with Maven

### Step 1: Create a new Maven project

If you haven't already, create a new Maven project for your Discord bot:

```bash
mvn archetype:generate -DgroupId=com.example -DartifactId=bot-example -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```

### Step 2: Add Dawncord dependency

Add the Dawncord dependency to your Maven pom.xml file:

```xml
<dependency>
    <groupId>io.github.dawncord</groupId>
    <artifactId>Dawncord</artifactId>
    <version>${dawncord.version}</version>
</dependency>
```

Replace ${dawncord.version} with the latest version of Dawncord.

### Step 3: Build your project

Build your Maven project to fetch the dependencies:

```bash
mvn clean install
```

## Installation with Gradle

### Step 1: Create a new Gradle project

If you haven't already, create a new Gradle project for your Discord bot:

```bash
mkdir bot-example
cd bot-example
gradle init --type java-application
```

### Step 2: Add Dawncord dependency

Add the Dawncord dependency to your Gradle build.gradle file:

```groovy
dependencies {
    implementation 'io.github.dawncord:Dawncord:$dawncordVersion'
}
```

Replace $dawncordVersion with the latest version of Dawncord.

### Step 3: Build your project
Build your Gradle project to fetch the dependencies:

```bash
gradle build
```

## Next Steps
Once you've installed Dawncord and set up your project, you can explore the library's features and begin developing your Discord bot.

For detailed information on all classes, methods, and configurations available in Dawncord, refer to the [Javadocs](https://javadoc.io/doc/io.github.dawncord/Dawncord/latest/index.html).

If you encounter any issues during the installation process, feel free to ask for help on [GitHub](https://github.com/dimas4ek) or 
[Discord](https://discordapp.com/users/305240921019121664).
<p>
Happy coding!
