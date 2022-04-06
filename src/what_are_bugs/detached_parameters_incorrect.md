# Detached Parameters Incorrect

```dot process
digraph {
    node [
        shape     = circle
        style     = filled
        fontname  = "Monospace"
        fontsize  = 12
        color     = "#aaaabb"
        fillcolor = "#eeeef5"
        width     = 0.4
        height    = 0.4
    ]
    edge [
        fontname  = "Monospace"
        fontsize  = 10
    ]

    a [label = <<b>A</b>>]
    b [label = <<b>B</b>>]
    c [label = <<b>C</b>>]

    calculate [
        label = <<b>calculate(a)</b>>
        fontsize = 11
        shape = rectangle
        style = "rounded,filled"
    ]

    calculate_inner [
        label = <<b>doCalculate(a, b, c)</b>>
        fontsize = 11
        shape = rectangle
        style = "rounded,filled"
    ]

    result [label = <<b>..</b>>]

    a -> calculate
    b -> calculate_inner
    c -> calculate_inner
    calculate -> calculate_inner
    calculate_inner -> result
}
```

For the same input from the consumer, provider returns different output due to calculation using other state.

* Environmental variables
* Configuration

The bug may be outside of the source code. Configuration is deferred code.
