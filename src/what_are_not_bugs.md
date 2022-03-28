# What Are Not (Application) Bugs

1. Error returned because the input cannot be parsed.

    User input does not match the software enforced constraints.

    - It is not a bug to return an error.
    - It is a bug not to return an error.
    - How good the error is is a different thing.

2. Error returned because the input is out of the capability of the software.

    1. I have 2 billion dollars. <span class="comment">            # not a bug</span>
    2. My friend gives me 1 billion dollars. <span class="comment">  # not a bug</span>
    3. Now I have negative 1 billion dollars. <span class="comment"> # a bug</span>

    > ⚠️ To receive input is not a bug. To not reject it when you can't handle it, is.

3. Crash because the system ran out of memory.

    I'd classify this as a load issue, and is better handled by rate limiting, than logic at each code path that allocates memory.

4. Failure to load library dependency.

    It's a bug in the deployment, but not in the application.

<style type="text/css">
.comment {
    font-family: monospace;
    color: grey;
    white-space: pre;
}
</style>
