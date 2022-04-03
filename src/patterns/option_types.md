# Option Types

> Don't use sentinel values, use `Option` types.

Sentinel values are values with special meaning within the set of valid values for a type.

For example:

* Using `-1` to indicate something went wrong.
* Using `-1` to indicate a variable has not been initialized.
* Using `null` to indicate non-existence.

For the first case, raise an error. For the latter two, use `Option` types.

<details>
<summary><b>Example:</b> Max value from a list of values.</summary>

Switch from:

```java
Integer max = Integer.MIN_VALUE;
for (value: values) {
    if (max < value) {
        max = value;
    }
}

// May incorrectly return `Integer.MIN_VALUE` as the max value.
```

to:

```java
Option<Integer> max = Optional.empty();
for (value: values) {
    if (max.isEmpty()) {
        max = Optional.of(value);
    } else {
        Integer currentMax = max.get()
        if (currentMax < value) {
            max = Optional.of(value);
        }
    }
}

// `max` was never initialized to an invalid state.
// When `max` is empty, then we know the list was empty.
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

* **1, 7:** Use `Optional` to indicate when it is valid to not provide a value.
* **2, 7:** Use `Optional` in return types to indicate there may not be a return value.

