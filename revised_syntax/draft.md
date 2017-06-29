# Revised DocOnce syntax -- Draft

DocOnce's syntax is influenced primarily by Markdown and LaTeX, but also has some examples of HTML

## Aims
DocOnce should be fast and easy to read and write without the need for setting up macros in the text editor used.

The syntax should be unified in style instead of borrowing extensively from so many different languages. It would be natural to converge towards Markdown, since LaTeX syntax is quite verbose.

## Proposition
### Headings

* Legacy DocOnce
    * Headings are written on a single line, with 9, 7, 5, 3 and 2 `=` on either side, separated from the heading by a single space
    * More `=` signs for the bigger headings
        * Chapter: 9, 7, 5, 3 and 2
    * Example
    ```
    ========= This is a chapter =========
    ======= This is a section =======
    ===== This is a subsection =====
    === This is a subsubsection ===
    ```

* LaTeX
    * Commands for each heading type
    * Example
    ```
    \chapter{This is a chapter}
    \section{This is a section}
    \subsection{This is a subsection}
    \subsubsection{This is a subsubsection}
    ```
* Markdown
    * Headings are written with a positive number of `#` on the start of the line
    * More `#` signs for the smaller headings
    * Example
    ```
    # This is a chapter
    ## This is a section
    ### This is a subsection
    #### This is a subsubsection
    ```

The current heading syntax is a bit verbose. There are a few decisions that need to be made:
- What symbol(s) to use for headings
- Assuming a style where the heading size is a function of the number of symbols: Do the headings get larger or smaller with more symbols
    - Larger:
        - Pro: Faster to write smaller headings (which are typically more numerous)
        - Pro: Large headings also appear larger
    - Smaller:
        - Pro: Markdown uses this style, so it is more common

Preprocess will process lines starting with `# #`, and legacy DocOnce comments are written Python style with a leading `#`, so using Markdown style headings in DocOnce does not seem like a viable option.



### Links and URLs

* Legacy DocOnce:
    * __Plain URL:__

    `URL: "http://github.com"`
    * __Link with description:__

    `"GitHub": "http://github.com"`

* Markdown
    * __Plain URL:__
        * Two styles:
        * `http://github.com`
        * `<http://github.com>`

    * __Link with description:__

    `[GitHub](http://github.com)`

Suggestion: Adopt Markdown's link syntax and a new URL syntax:
* `[!url](http://github.com)`


### References and citations
* Legacy DocOnce:
    * `ref{fig:sine_curve}`
    * `cite{knuth97}`
* LaTeX:
    * `\ref{fig:sine_curve}`
    * `\cite{knuth97}`

The exact LaTeX syntax would be a poor choice since `\` will function as an escape character for writing a literal asterisk as `\*` etc.
References are in a way a link, so it doesn't seem unnatural to apply a variation on the link syntax:
* `[!ref](fig:sine_curve)`
* `[!cite](knuth97)`

Alternatively, it would be possible to do
* `!ref{fig:sine_curve}`
* `!cite{knuth97}`

But `{` and `}` isn't used much elsewhere in DocOnce (except for `label{}` and in LaTeX mathematics).

### LaTeX mathematics
Keep inline syntax.

Add new short-hand syntax for blocks. Instead of writing out
```
!bt
\begin{align}
a = 2
\end{align}
!et
```

the short-hand syntax could additionally allow for
```
!bt align
a = 2
!et
```

and likewise for `equation`. Typically there is one LaTeX environment enclosing all of the text block, so this would save two lines.
