---
description: This page will show you how to set up your main class to support Framework
---

# Setting up your main class

In order for your plugin to use all of our features, you need to make sure you setup your main class.&#x20;

To get your plugin to use Framework, you need to `extends BasePlugin` in your main class. This allows your plugin to run with Framework loaded at the same time.&#x20;

Here's an example:

```java
import games.negative.framework.BasePlugin;

public final class EpicPlugin extends BasePlugin {} 
```

{% hint style="warning" %}
If you do not extend `BasePlugin`, your plugin will not work with any Framework features.&#x20;
{% endhint %}