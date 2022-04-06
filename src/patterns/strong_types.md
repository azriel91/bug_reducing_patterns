# Strong Types

> *in constrast to Stringly typed*

Instead of `String username, String password`, use `Username username, Password password`.

Switch from:

```java
public class Profile {
    private String username;
    private String password;

    public Profile(String username, String password) { .. }
    // ..
}
```

to:

```java
public class Profile {
    private Username username;
    private Password password;

    public Profile(Username username, Password password) { .. }
    // ..
}

public class Username {
    private String value;
    public boolean equals(..) { .. }
    // ..
}

public class Password {
    private String value;
    public void toString() { return "******"; }
    // ..
}
```

## Bug Variants Addressed

* **1:** Avoids argument swap by producing a compiler error.
* **5:** `Password.toString()` never returns the true value, so a wrapping class that calls `toString()` on all of its member fields will not inadvertently log the password.
