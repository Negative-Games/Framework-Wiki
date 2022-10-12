# JSON Configuration

This configuration system uses the Gson library to easily load json files to their class variants and vice versa. Please make sure you have it in your project!

<details>

<summary>Adding Gson to your Project</summary>

### Github

[https://github.com/google/gson](https://github.com/google/gson)

### Maven

```xml
<dependency>
    <groupId>com.google.code.gson</groupId>
    </artifactId>
    <version>2.9.1</version>
</dependency>
```

### Gradle

```groovy
dependencies {
  implementation 'com.google.code.gson:gson:2.9.1'
}
```

</details>



### Loading a JSON file to a class

You can load a JSON file to its class representation by using one method!

{% code title="Code Example" lineNumbers="true" %}
```java
MyConfigClass config = jsonConfigManager.loadOrCreate("configs", "config.json", MyConfigClass.class, new MyConfigClass());
```
{% endcode %}

This method essentially loads the json file or creates it if it doesnt exist and loads it right into a class format so you do not have to do any form of parsing on your end to make `json -> class` or `class -> json` work.



### Saving a class to a JSON file

{% code title="Code Example" lineNumbers="true" %}
```java
jsonConfigManager.save("configs", "config.json", config);
```
{% endcode %}

This method essentially saves the provided `config` instance to `configs/config.json`!

