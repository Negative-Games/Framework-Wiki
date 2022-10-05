---
description: This page covers all you need to know about our Base64 Serializer
---

# Base64 Serializer

{% hint style="info" %}
Base64 encoding schemes are commonly used **when there is a need to encode binary data that needs to be stored and transferred over media that are designed to deal with ASCII**. This is to ensure that the data remain intact without modification during transport.

Source: [https://developer.mozilla.org/en-US/docs/Glossary/Base64](https://developer.mozilla.org/en-US/docs/Glossary/Base64)
{% endhint %}

<details>

<summary>Encoding to Base64 (Using ItemStacks)</summary>

You are able to convert ItemStacks to Base64 using this method. The String contains all the properties of the ItemStack along with any custom NBT values you add to it using external plugins like NBTAPI.

```java
// This is the base64 code that you can save wherever you want
String base64 = BukkitSerializer.itemStackArrayToBase64(new ItemStack[]{item})
```

</details>

<details>

<summary>Encoding to Base64 (Using Inventories)</summary>

You are able to convert Inventories to Base64 using this method. The String array you get has two sets of Strings, one being the armor contents, the second being the actual inventory contents. The Strings also contains where the items were previously located in your inventory along with all the properties of the ItemStacks.

```java
String[] inv = BukkitSerializer.playerInventoryToBase64(player.getInventory());
String contentsBase64 = inv[0]
String armorBase64 = inv[1]
```

</details>

<details>

<summary>Decoding from Base64 (Using ItemStacks)</summary>

You are able to convert Base64 to ItemStacks using this method. Using a proper ItemStack Base64 String, you will be able to get the Item you previously converted.

```java
String base64 = "YOUR BASE64 CODE"

// This is the item resulting from the base64 code you provided
ItemStack converted = BukkitSerializer.itemStackArrayFromBase64(base64)[0];
```

</details>

<details>

<summary>Decoding from Base64 (Using Inventories)</summary>

You are able to convert Base64 to Inventories using this method. Using a proper Inventory Base64 String, you will be able to get the Inventory you previously converted.

```java
String contentsBase64 = "THE BASE64 STRING OF YOUR INVENTORY CONTENTS"
String armorBase64 = "THE BASE64 STRING OF YOUR ARMOR"

Inventory inventory = BukkitSerializer.inventoryFromBase64(contentsBase64);
ItemStack[] armor = BukkitSerializer.itemStackArrayFromBase64(armorBase64);
```

</details>
