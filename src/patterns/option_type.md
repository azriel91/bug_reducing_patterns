# Option Type

> `null` in different clothes.

Use `Optional<T>` to indicate when a value may not actually exist.

<details>
<summary><b>Example:</b> Max value from a list of values.</summary>

Switch from:

```java
Integer max = null;
for (int value: values) {
    if (max == null) {
        max = value;
    } else if (max < value) {
        max = value;
    }
}
return max;

// Usage
int max = getMax(new int[] {}); // NullPointerException
```

to:

```java
Optional<Integer> max = Optional.empty();
for (int value: values) {
    max = max
        .map(currentMax -> currentMax < value ? value : currentMax)
        .orElse(value);
}

return max;
```

</details>

<details>
<summary><b>Example:</b> Returning data from storage.</summary>

Switch from:

```java
public interface DataStorage {
    /**
     * @return the data for the given ID, or null if it doesn't exist.
     */
    public Data get(DataId dataId);
}

public class DataConsumer {
    public void doSomething(DataId dataId) {
        Data data = dataStorage.get(dataId);
        if (data != null) {
            // do something with it.
        }

        // `data` exists here, possible to use null reference.
    }
}
```

to:

```java
public interface DataStorage {
    /**
     * @return the data for the given ID if exists.
     */
    public Optional<Data> get(DataId dataId);
}

public class DataConsumer {
    public void doSomething(DataId dataId) {
        dataStorage
            .get(dataId)
            .ifPresent(data -> {
                // do something with it.
            });

        // `data` doesn't exist here, impossible to use null reference.
    }
}
```

We communicate across the API boundary that the value may not exist.

</details>

## Bug Variants Addressed

* **1:** Use `Optional` to indicate when it is valid to not provide a value.
* **3:** Use `Optional` in return types to indicate there may not be a return value.
