---
description: This page shows you how you would add this library to your Maven Project!
---

# Using Maven

{% hint style="info" %}
Current version: `3.0.0-ALPHA-6`
{% endhint %}

### Repository

```xml
<repository>     
    <id>negative-games</id>
    <url>https://repo.negative.games/repository/maven-public/</url>
</repository>
```

### Dependency

```markdown
<dependency>
  <groupId>games.negative.framework</groupId>
  <artifactId>minecraft-framework</artifactId>
  <version>{VERSION}</version>
  <scope>compile</scope>
</dependency>
```

### Shading into your JAR

Add the following code to your pom.xml under `maven-shade-plugin`

```markdown
<configuration>
  <relocations>
    <relocation>
      <pattern>games.negative.framework</pattern>
      <shadedPattern>{YOUR PACKAGE NAME}</shadedPattern>
    </relocation>
  </relocations>
</configuration>
```
