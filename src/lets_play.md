# Let's Play

## 🐞 Where is the bug?

* **A**, **B**, and **C** are different entities.
* **A** produces invalid input.
* **B** takes that invalid input, and passes it to **C**.
* **C** doesn't like the input and drops it.

```dot process
digraph {
    rankdir = LR;

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

    a -> b -> c
}
```

## Perspectives

<details>
<summary>A</summary>

Correct &ndash; if **A** is software.

But ☝️! if **A** means people, you are insulting the entire class of users.

</details>


<details>
<summary>B</summary>

Correct &ndash; if **B** should be a gatekeeper.

But **B** could also just be a blind transport channel.

</details>


<details>
<summary>C</summary>

Correct &ndash; if **C** should communicate back that the value is invalid.

But dropping invalid values could be completely okay.

</details>


<details>
<summary>There is no bug.</summary>

Correct &ndash; if unreliability is an acceptable design, like streaming a video.

</details>
