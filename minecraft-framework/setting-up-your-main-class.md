---
description: >-
  To make this library work to its fullest potential, you must extend your main
  class with BasePlugin
---

# Setting up your main class

In order for your plugin to use all of our features, you need to make sure you setup your main class.&#x20;

To get your plugin to use Framework, you need to `extends BasePlugin` in your main class. This allows your plugin to run with Framework loaded at the same time.&#x20;

{% code title="Code Example" lineNumbers="true" %}
```java
import games.negative.framework.BasePlugin;

public final class EpicPlugin extends BasePlugin {


     @Override
     public void onEnable() {
         super.onEnable(); // this is required for features to work
     
     }
} 
```
{% endcode %}

{% hint style="warning" %}
If you do not extend `BasePlugin`, your plugin will not work with any Framework features.&#x20;
{% endhint %}
