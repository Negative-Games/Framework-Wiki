---
description: This page shows you how you would add this library to your Maven Project!
---

# Using Maven

{% hint style="info" %}
Current version: `1.0.0-ALPHA-1`
{% endhint %}

### Repository

```xml
<repository>     
    <id>negative-games</id>
    <url>https://repo.negative.games/repository/maven-public/</url>
</repository>
```

### Dependency

{% code lineNumbers="true" %}
```markdown
<dependency>
  <groupId>games.negative.framework.discord</groupId>
  <artifactId>discord-framework</artifactId>
  <version>{VERSION}</version>
  <scope>compile</scope>
</dependency>
```
{% endcode %}

### Shading into your JAR

Add the following code to your pom.xml under `maven-shade-plugin`

{% code lineNumbers="true" %}
```markdown
<configuration>
  <relocations>
    <relocation>
      <pattern>games.negative.framework.discord</pattern>
      <shadedPattern>{YOUR PACKAGE NAME}</shadedPattern>
    </relocation>
  </relocations>
</configuration>
```
{% endcode %}
