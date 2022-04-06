# Patterns

Largely designed for statically typed languages. These patterns are designed or intended to:

* Communicate input and output expectations through API.

    Documentation is important, code is authoritative.

* Favour compile errors over testing through type safety.

    By making it impossible to compile incorrect code, quality is maintained with less tests.

* Guarantee assumptions through type safety.

    By encoding proofs of correctness through types, one no longer has to be defensive.


## Disclaimer

As with most patterns, pragmaticism applies.

Applying the concepts excessively may:

* Negatively affect compile time or runtime performance depending on your language.
* Increase the number of files needed to be maintained.
* Cause debate between colleagues, depending on each persons bias.
