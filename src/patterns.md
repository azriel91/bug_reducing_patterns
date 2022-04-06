# Patterns

Largely designed for statically typed languages &ndash; they rely on having a compiler.

These patterns are designed or intended to:

* Communicate input and output expectations through API.

    Documentation is important, code is authoritative.

* Guarantee assumptions through type safety.

    By encoding proofs of correctness through types, one no longer has to write defensive code.

* Favour compile time errors over runtime errors through type safety.

    By making it impossible to compile incorrect code, correctness and quality is maintained with fewer tests.


## Disclaimer

As with most patterns, pragmaticism applies.

Applying the concepts excessively may:

* Negatively affect compile time or runtime performance depending on your language.
* Increase the number of files needed to be maintained.
* Cause debate between colleagues, depending on each persons bias.
