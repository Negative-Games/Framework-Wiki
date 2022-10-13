---
description: This page shows you how you would add this library to your Gradle Project!
---

# Using Gradle

{% hint style="info" %}
Current version: `1.0.0-ALPHA-3`
{% endhint %}

### Repository

```groovy
repositories {
    maven { url 'https://repo.negative.games/repository/maven-public/' }
}
```

### Dependencies

```groovy
dependencies {
    implementation 'games.negative.framework.discord:discord-framework:{VERSION}'
}
```

### Shading into your JAR

You require the shadow gradle plugin

```groovy
plugins {
    id 'java'
    id "com.github.johnrengelman.shadow" version "7.1.2"
}
```

Next you should add this somewhere in your `build.gradle` file

```groovy
def id = "MyApplication" // Replace with the application name
def group = 'games.negative' // Replace with your group id
def version = '1.0-SNAPSHOT' // Replace with the version

shadowJar {
    archiveBaseName.set("${id}-${version}")
    archiveClassifier.set("")
    archiveVersion.set("")
    
    relocate "games.negative.framework.discord", "${group}.libs.discord"
}
```
