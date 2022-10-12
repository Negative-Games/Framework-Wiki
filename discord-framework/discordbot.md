---
description: >-
  To make this library work to its fullest potential, you must extend your main
  class with DiscordBot
---

# DiscordBot

The DiscordBot class contains implementation code for the features of this library. To allow the library to properly initialize you must extend your main class with DiscordBot!

{% code title="Code Example" lineNumbers="true" %}
```java
public class Bot extends DiscordBot {

    @SneakyThrows
    public Bot() {
        JDABuilder builder = createDefault("MY-TOKEN");
        builder.setActivity(Activity.playing("your mom"));
        
        registerServerCommand("DEV-SERVER", new CommandExample());

        JDA jda = builder.build().awaitReady();
        initializeCommands(jda);
    }
}
```
{% endcode %}
