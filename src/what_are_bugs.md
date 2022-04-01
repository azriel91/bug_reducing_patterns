# What Are Bugs

> "Unexpected Behaviour"

Seven kinds / classifications of bugs.

1. Consumer got the input wrong.

    Input value doesn't comply with allowed specification.

    - Incorrect syntax.
    - Values out of allowed range.

2. Provider got the output wrong.

    Output value doesn't comply with output specification.

    - Incorrect syntax.
    - Miscalculation.

3. Consumer and provider expectations not aligned.

    Misinterpretation / ambiguous meaning of input / output / side effects.

    - `null` can mean "it's not there", or "it's there, but it's empty."
    - Provider expects consumer to opt-in, consumer expected opt-out.
    - Provider expects consumer to opt-out, consumer expected opt-in.

4. Provider contains state that can differ, but consumer is not aware.

    For the same input from the consumer, provider returns different output due to calculation using internal state.

    - Environmental variables
    - Configuration
    - Time
    - Load (physical limits)

5. Provider does things in the wrong way. e.g. log sensitive information.

    Unintended / undesired side effects.

    <!--   There are ways to restrict this at compile time, e.g. must implement loggable interface.   -->

6. Provider does not enforce restrictions on input.

    Unintentionally doing more things than one should.

    - Remote code execution: Log4Shell.
    - Data leakage: Heartbleed.

    Sometimes what sounds like a good idea at the time, may not be a good idea later on.

7. Undefined behaviour.

    Software executes logic over invalid data.

    - Didn't code for a particular case because didn't realize it is possible.
    - Two data items which are valid independently are invalid together.
    - Dereferencing a freed pointer.
