---
description: >-
  This page covers the database utility found within the Framework, and how to
  use it effectively!
---

# Database Utils

### Connecting to your Database

<details>

<summary>MySQL</summary>

Here's how to connect to a database using MySQL:

```java
Database db = new Database(
                "INSERT IP",
                3306,
                "INSERT USERNAME",
                "INSERT PASSWORD",
                "INSERT DATABASE NAME"
                );
```

</details>

<details>

<summary>SQLLite</summary>

Here's how to connect to your database using SQLLite:

```java
Database db = new Database(file);
```

</details>

{% hint style="info" %}
You can debug errors with your code by adding a boolean "true" as the second parameter of those methods.
{% endhint %}



Once you've initialized your `Database` object, please make sure you connect using the method bellow:

```java
db.connect();
```

### Creating a Table

Here's how to create a table using the Database API.

First, you'll need to create a list of `Column` objects to define what columns you want in your table. Here's an example:

```java
List<Column> columns = new ArrayList<>();
Column column = new Column(ColumnType.VARCHAR, "Test");
columns.add(column);
```

Once you've done that, you can create a `TableBuilder` class to provide some more information to the API.

```java
TableBuilder tb = new TableBuilder("tablename", columns);
```

Great! Now we've got everything we need to create a table. Now all you have to do is run this method.

```java
db.createTable(tb);
```

### Reading and Inserting

#### Reading

```java
db.get("TABLE", "KEY", "VALUE", "COLUMN TO RETRIEVE")
```

Here's a more detailed explanation of what these parameters mean:

```
For example, if you wanted to get the details about a player,
the key parameter would be "name" or whatever it is within your table
and the value parameter would be the player's name of whom you wish to get the details.

The "column" parameter would be the specific detail you'd like to get. For example,
if my table contained an "age" column, and I wanted to get the player's age,
I'd set the column parameter to "age"
```

#### Inserting

To insert into your database, you need to make a HashMap of your keys and values:

```java
 HashMap<String, String> values = new HashMap<>();
        values.put("UUID", "epic uuid!");
        values.put("NAME", "SEAILZ");
```

Once you've done that, just let the API know:

```java
db.insert("TABLE", values);
```

### Interacting With Java Objects

This API offers a great feature in that it lets you insert and read Java Objects with just a couple lines of code, instead of having to do every value individually. Here's how you do it:

#### Reading Objects

You'll need to annotate the constructor in the object you wish to read with `@DatabaseConstructor`, and each parameter with `@Column (INSERT_COLUMN_NAME)`&#x20;

```java
@DatabaseConstructor
public TestObject(@Column("profileName") String profileName) {
    // DO SOMETHING
}
```

{% hint style="info" %}
If you have multiple constrcutors, annotate the one you want the Database to use.
{% endhint %}

Now, you can actually start reading the object:

```java
TestObject testObject = (TestObject) db.get("INSERT_TABLE", "INSERT_KEY", "INSERT_VALUE", TestObject.class);
// See the "Reading And Inserting" section for more information on what these parameters mean.
```

#### Writing Objects

```java
db.insert("TABLE", testObject);
```

{% hint style="danger" %}
Make sure that the table you are trying to insert in matches the columns listed in your constructor, or else this will not work!
{% endhint %}

### Deleting

```java
db.delete("INSERT_TABLE_NAME_HERE", "INSERT_KEY_HERE", "INSERT_VALUE_HERE");
```

### Checking if a row exists

```java
db.rowExists("INSERT_TABLE_HERE", "INSERT_KEY_HERE", "INSERT_VALUE_HERE");
```

### Sending your own queries

There's a custom class called "Statement" which can be used to send statements to your database with ease. All you need to do is this:

```java
Statement s = new Statement("INSERT_MYSQL_QUERY_HERE", db.getConnection();
```

Now to execute the command, you have two options:

<details>

<summary>With Results Set</summary>

This should be used if the command is supposed to return some results. Here's how:

```java
ResultSet res = s.executeWithResults();
```

</details>

<details>

<summary>Without Results Set</summary>

This should be used when the command is not expected to return results. For example, creating a new table.

```java
s.execute();
```

</details>

### Disconnecting

Once you are done interacting with your database, make sure you disconnect!

```java
db.disconnect();
```

{% hint style="warning" %}
If you don't disconnect, you could run into errors! Remember, you can always just connect later with db.connect();
{% endhint %}



> That's it! I encoruge you to look around the API as there are more features that aren't documented here! If you want to see the latest features, you can head to [https://github.com/seailz/Database4J](https://github.com/seailz/Database4J) as features there will eventually get added to the Framework.&#x20;
