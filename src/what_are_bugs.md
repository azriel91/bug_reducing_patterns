# What Are Bugs

> "Unexpected Behaviour"

Seven kinds / classifications of bugs.

1. Consumer Input Incorrect.

    Input value doesn't comply with allowed specification.

    - Syntax incorrect.
    - Values out of allowed range.

2. Provider Output Incorrect.

    Output value doesn't comply with output specification.

    - Syntax incorrect.
    - Logic incorrect.

3. Ambiguity / Misaligned Expectations.

    - `null` can mean "it's not there", or "it's there, but it's empty."
    - Provider expects consumer to opt-in, consumer expected opt-out.
    - Provider expects consumer to opt-out, consumer expected opt-in.

4. Detached Parameters Incorrect.

    For the same input from the consumer, provider returns different output due to calculation using other state.

    - Environmental variables
    - Configuration

    The bug may be outside of the source code. Configuration is deferred code.

5. Undesired Side Effects.

    Provider leaks information in the logs.

    <!--   There are ways to restrict this at compile time, e.g. must implement loggable interface.   -->

6. Input Restrictions Too Loose.

    Provider unintentionally does more than it should. e.g. Remote code execution: Log4Shell.

    Sometimes what sounds like a good idea at the time, may not be a good idea later on.

7. Undefined Behaviour.

    Software executes logic over invalid values.

    - Didn't code for a particular case because didn't realize it is possible.
    - Two data items which are valid independently are invalid together.
    - Dereferencing a freed pointer.
