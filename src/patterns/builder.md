# Builder

> Never allow an object to be constructed unless it's correct.

```dot process
digraph {
    node [
        shape     = circle
        style     = filled
        fontname  = "Monospace"
        fontsize  = 12
        color     = "#aaaabb"
        fillcolor = "#eeeef5"
        width     = 0.4
        height    = 0.4
    ]
    edge [
        fontname  = "Monospace"
        fontsize  = 10
    ]

    a [label = <<b>A</b>>]
    b [label = <<b>B</b>>]
    c [label = <<b>C</b>>]
    d [label = <<b>D</b>>]

    builder [label = "Builder", shape = rectangle, style = "rounded, filled"]

    a -> builder [label = " builder.with_a(a)     "]
    b -> builder [label = " builder.with_b(b)     "]
    c -> builder [label = " builder.with_c(c)     "]
    builder -> d [label = " builder.build()"]
}
```

**Builder:**

* Collects multiple values, then maps them into a single validated value in a `build()` method.
* Avoids partial objects &ndash; don't allow yourself to have an instance of the target type unless it is correct.

**Example:** Data where `intValue` must be greater than `byteValue`.

Switch from:

```java
public class Data {
    private final byte byteValue;
    private final int intValue;
    private final Optional<String> stringValue;

    public Data(byte byteValue, int intValue, Optional<String> stringValue) {
        this.byteValue = byteValue;
        this.intValue = intValue;
        this.stringValue = stringValue;
    }

    // ..
}

// Usage
Data data = new Data(0, 1, Optional.empty());
```

to:

```java
public class Data {
    private final byte byteValue;
    private final int intValue;
    private final Optional<String> stringValue;

    // Package private to allow builder class access.
    Data(byte byteValue, int intValue, Optional<String> stringValue) {
        this.byteValue = byteValue;
        this.intValue = intValue;
        this.stringValue = stringValue;
    }

    // ..
}

public class DataBuilder {
    private final Optional<Byte> byteValue;
    private final Optional<Integer> intValue;
    private final Optional<String> stringValue;

    // Constructor
    // either:

    public DataBuilder() {
        this.byteValue = Optional.empty();
        this.integerValue = Optional.empty();
        this.stringValue = Optional.empty();
    }

    // or

    public DataBuilder(byte byteValue, int intValue) {
        this.byteValue = Optional.of((Byte) byteValue);
        this.integerValue = Optional.of((Integer) intValue);
        this.stringValue = Optional.empty();
    }

    // Append additional values.

    public DataBuilder withByteValue(byte byteValue) {
        this.byteValue = Optional.of(byteValue);
        return this;
    }

    public DataBuilder withIntValue(int intValue) {
        this.intValue = Optional.of((Integer) intValue);
        return this;
    }

    public DataBuilder withStringValue(String stringValue) {
        this.stringValue = Optional.of(stringValue);
        return this;
    }

    public Data build() throws IncompatibleValuesException {
        // Default the byteValue and intValue
        byte byteValue = this.byteValue
                .orElse(0)
                .byteValue();

        int intValue = this.intValue
                .orElse((int) byteValue + 1)
                .intValue();

        if (intValue < (int) byteValue) {
            throw new IncompatibleValuesException(
                    intValue,
                    byteValue,
                    "intValue must not be smaller than byteValue.");
        }

        return new Data(byteValue, intValue, this.stringValue());
    }

    // ..
}

// Usage
Data data = new DataBuilder()
    .withByteValue(123)       // allows method chaining
    .withIntValue(456)
    .withStringValue("abc")
    .build();                 // enforces constraints
                              // so any error is raised here
```

## Bug Variants Addressed

* **1:** Raises an error<sup>1</sup> at the point of building.
* **2:** Reduces provider code working with invalid input, because only valid input reaches the business logic.
* **4:** Only allow groupings of valid values in the constructed type.
* **6:** Constrains input to a range of safe values.

<sup>1</sup> It is not a bug to raise an error.
