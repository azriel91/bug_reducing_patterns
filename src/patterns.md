# Patterns

Largely designed for statically typed languages. These patterns are designed or intended to:

* Favour compile errors over testing.

    Make it impossible to do the wrong thing, so quality is maintained even without tests.

* Favour type safety over validation.

    Have compile time guarantees that any invalid data bug needs to only be fixed once.

* Reduce mental effort to understand the concept the code is fulfilling.


## Disclaimer

As with most patterns, pragmaticism applies.

Applying the concepts excessively may:

* Negatively affect compile time or runtime performance depending on your language.
* Increase the number of files needed to be maintained.
* Cause debate between colleagues, depending on each persons bias.
