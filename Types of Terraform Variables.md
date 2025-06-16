# Terraform Variables

In Terraform, **variables** are a fundamental concept used to make configurations more **dynamic and reusable**. They are a core feature that allows you to **parameterize** your Terraform configurations.

Variables are defined within a `variable` block in Terraform.

By using variables, you can make your code:
* More flexible
* More reusable
* Easier to manage

Variables enable you to **customize your Terraform deployments without hardcoding values directly** into your configuration files.

## Types of Terraform Variables

### Input Variables

These allow you to **pass values into Terraform configurations**. They are defined using the `variable` block.

---

### Output Variables

These are used to **return values from your Terraform configurations** after they have been applied. They are often used for sharing data between different configurations or modules.

---

### Local Variables

These are used to **assign values to an expression or value within a configuration for reuse**, improving readability and maintainability.

## Variable Types

Terraform supports several types of variables, allowing you to define different kinds of data:

* **`string`**: A sequence of characters (e.g., `"hello"`, `"world"`).
* **`number`**: Any numeric value (e.g., `10`, `3.14`, `-5`).
* **`bool`**: A boolean value (`true` or `false`).
* **`list(type)`**: An ordered list of elements of a specified type (e.g., `["a", "b", "c"]`).
* **`map(type)`**: A collection of key-value pairs, where all values are of a specified type (e.g., `{ key1 = "value1", key2 = "value2" }`).
* **`set(type)`**: A unique, unordered collection of elements of a specified type (e.g., `["a", "b", "c"]` where duplicates are automatically removed).
* **`object({...})`**: A structured object with named attributes, each having its own type (e.g., `{ name = string, age = number }`).
* **`tuple([types])`**: A fixed-length, ordered sequence of elements, where each element can have a different type (e.g., `[string, number, bool]`).