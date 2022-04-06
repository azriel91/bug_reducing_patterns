# Either Type

> Buy one get one free.

Avoid writing two classes in one class, separate concepts by type.

Switch from:

```java
// Example of two classes in one
public class InputOptions {
    private InputDevice inputDevice;

    // Using keyboard controls
    // Only relevant if InputDevice is Keyboard
    private KeyCode keyAttack;
    private KeyCode keyJump;
    private KeyCode keyUp;
    private KeyCode keyDown;
    private KeyCode keyLeft;
    private KeyCode keyRight;

    // Using Game Controller controls
    // Only relevant if InputDevice is GameController
    private ButtonCode buttonAttack;
    private ButtonCode buttonJump;
    private DirectionPad directionInput;

    // ..
}

public enum InputDevice {
    Keyboard,
    GameController;
}

// Usage
switch (inputOptions.getInputDevice()) {
    case InputDevice.Keyboard:
        if (inputOptions.getKeyAttack()) { /* .. */ }
        break;
    case InputDevice.GameController:
        if (inputOptions.getButtonAttack()) { /* .. */ }
        break;
}
```

to:

```java
public class Keyboard {
    private KeyCode keyAttack;
    private KeyCode keyJump;
    private KeyCode keyUp;
    private KeyCode keyDown;
    private KeyCode keyLeft;
    private KeyCode keyRight;

    // ..
}

public class GameController {
    private ButtonCode buttonAttack;
    private ButtonCode buttonJump;
    private DirectionPad directionInput;

    // ..
}

// Strong type alias.
public class InputOptions extends Either<Keyboard, GameController> { /* .. */ }

// Usage
inputOptions
    // Impossible to use game controller fields in keyboard logic
    .ifKeyboard(keyboard -> {
        if (keyboard.getKeyAttack()) { /* .. */ }
    })
    // Impossible to use keyboard fields in game controller logic
    .ifGameController(gameController -> {
        if (gameController.getButtonAttack()) { /* .. */ }
    });
```

Doesn't exist in the JDK, but exists in [`functionaljava`]: [`fj.data.Either`] \([docs]\)

## Bug Variants Addressed

* **1:** Use `Either<A, B>` to allow passing in an `A` or a `B`.
* **3:** Use `Either<A, B>` to return either an `A` or a `B`.

[`functionaljava`]: http://www.functionaljava.org/
[`fj.data.Either`]: https://github.com/functionaljava/functionaljava/blob/v5.0/core/src/main/java/fj/data/Either.java
[docs]: http://www.functionaljava.org/javadoc/5.0/functionaljava/index.html
