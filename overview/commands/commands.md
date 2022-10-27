---
description: >-
  This page covers all you need to know about the Commands portion of the
  Framework Commands API
---

# Commands

### Creating a command

To create a command, you'll need to create a new class and extend the `Command` class. You can find an example below:

```java
import games.negative.framework.command.Command;
public class EpicCommand extends Command {}
```

Next, you need to specify some settings for the plugin to understand how your command should function. These settings help reduce boilerplate code. **You are required to annotate your class with** `@CommandInfo`

{% hint style="info" %}
There is also no need to register these commands into your `plugin.yml`!&#x20;

Just make sure you [#registering-commands](commands.md#registering-commands "mention")
{% endhint %}

```java
import games.negative.framework.command.Command;
import games.negative.framework.command.annotation.CommandInfo;

@CommandInfo(
    name = "ban",
    description = "Bans a user!",
    permission = "command.ban",
    aliases = {"b", "punishthatplayer"},
    playerOnly = true,
    disabled = false,
    args = {"name", "reason"}
)
public class EpicCommand extends Command {}
```

What do these parameters mean?

* Name: Represents the name of the command, such as `/ban` **REQUIRED**
* Description: Represents the description of the command.
* Permission: The permission required to run the command.
* Aliases: Other commands that will run the same thing. For example, if I type `/punishthatplayer`, it will execute the same as if I ran `/ban`
* Player Only: Determines if the command can only be used by players. There is also `consoleOnly`, which wont let a player run the command.
* Disabled: Allows you to disable a command. If a disabled command is ran, it will show an error message to the suer.
* Args: Allows you to specify the arguments of a command so you don't have to check the length of them yourself.

Great! Now that we've specified some info to setup the command, lets get onto where you actually place your logic.

You'll need to override a method, called "onCommand". Here's an example:

```java
import games.negative.framework.command.Command;
import games.negative.framework.command.annotation.CommandInfo;

@CommandInfo(
    name = "ban",
    description = "Bans a user!",
    permission = "command.ban",
    aliases = {"b", "punishthatplayer"},
    playerOnly = true,
    disabled = false,
    args = {"name", "reason"}
)
public class EpicCommand extends Command {

    @Override
    public void onCommand(CommandSender sender, String[] args) {
        System.out.println(sender.getName() + " executed the ban command!");
    }

}
```

Inside of that method you can place all the logic for your command!&#x20;

### Registering commands

We have made registering commands as simple as possible (is only uses on method!). In your Main class, insert this code:

<pre class="language-java"><code class="lang-java">public final class EpicPliugin extends BasePlugin {
<strong>        // Your plugin logic
</strong>            
        registerCommands(
                new EpicCommand(),
                new AnotherEpicCommand()
        );
}</code></pre>

It's as simple as that!&#x20;
