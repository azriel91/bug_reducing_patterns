# What Are Bugs

> "Unexpected Behaviour"

Seven kinds / classifications of bugs.

<details open>
<summary>1. Consumer Input Incorrect.</summary>

Input value doesn't comply with allowed specification.

* Syntax incorrect.
* Values out of allowed range.

</details>

<details open>
<summary>2. Provider Output Incorrect.</summary>

Output value doesn't comply with output specification.

* Syntax incorrect.
* Logic incorrect.

</details>

<details open>
<summary>3. Ambiguity / Misaligned Expectations.</summary>

* `null` can mean "it's not there", or "it's there, but it's empty."
* Provider expects consumer to opt-in, consumer expected opt-out.
* Provider expects consumer to opt-out, consumer expected opt-in.
* Type is able to hold values outside the range of valid business values, so consumer may assume whatever fits is okay.

</details>

<details open>
<summary>4. Detached Parameters Incorrect.</summary>

For the same input from the consumer, provider returns different output due to calculation using other state.

* Environmental variables
* Configuration

The bug may be outside of the source code. Configuration is deferred code.

</details>

<details open>
<summary>5. Undesired Side Effects.</summary>

Provider leaks information in the logs.

<!--   There are ways to restrict this at compile time, e.g. must implement loggable interface.   -->

</details>

<details open>
<summary>6. Input Restrictions Too Loose.</summary>

Provider unintentionally does more than it should. e.g. Remote code execution: Log4Shell.

Sometimes what sounds like a good idea at the time, may not be a good idea later on.

</details>

<details open>
<summary>7. Undefined Behaviour.</summary>

Software executes logic over invalid values.

* Didn't code for a particular case because didn't realize it is possible.
* Two data items which are valid independently are invalid together.
* Dereferencing a freed pointer.


</details>
