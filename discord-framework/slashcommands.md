---
description: >-
  An abstract SlashCommand API to expand on JDA's SlashCommand system with a few
  extra features
---

# SlashCommands

### Command Information Annotation

The command system is based off of an annotation which holds information such as the command name, command aliases, and the command description.

{% code title="Code Example" lineNumbers="true" %}
```java
@SlashInfo(
        name = "ping", 
        args = {"pong", "dong"}, 
        description = "Simply a test command!"
)
```
{% endcode %}

### SlashCommand Abstract Class

How you make a command is quite simple, you make a standalone class which should extend SlashCommand, when done it will prompt you to implement an abstract method which will be your event logic when the command runs.

{% code title="Code Example" lineNumbers="true" %}
```java
@SlashInfo(name = "example", description = "This is an example command")
public class CommandExample extends SlashCommand {
    @Override
    public void onCommand(SlashCommandInteractionEvent event) {
        event.reply("This is an example command").setEphemeral(true).queue();
    }
}
```
{% endcode %}

### Registering your SlashCommand

You can use two different methods to register your SlashCommand depending on what you want to do. You can use registerServerCommand and registerGlobalCommand in your main class which extends DiscordBot ([see DiscordBot](setting-up-your-main-bot-class.md))!

{% hint style="info" %}
When attempting to register Global Commands, it may take up to an hour or more for Discord's API to register it!
{% endhint %}

{% code title="Code Example" lineNumbers="true" %}
```java
registerServerCommand("DEV-SERVER", new CommandExample());
registerGlobalCommand(new MyGlobalCommand());
```
{% endcode %}

