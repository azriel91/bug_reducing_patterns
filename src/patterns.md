# Patterns

Largely designed for statically typed languages &ndash; they rely on having a compiler.

These patterns are designed or intended to:

* Communicate input and output expectations through API.
* Ensure correctness through type safety.

    Only allow an instance of a type to exist, if it meets certain criteria.

* Favour compile time errors over runtime errors.

    By making it impossible to compile incorrect code, correctness and quality is maintained, with fewer tests.


## Disclaimer

As with most patterns, pragmaticism applies.

Applying the concepts excessively may:

* Negatively affect compile time or runtime performance depending on your language.
* Increase the number of files needed to be maintained.
* Cause debate between colleagues, depending on each persons bias.
