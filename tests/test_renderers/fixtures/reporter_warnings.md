Duplicate Reference definitions:
.
[a]: b
[a]: c
.
<string>:2: (WARNING/2) Duplicate reference definition: A [myst.ref]
.

Missing Reference:
.
[a](b)
.
<string>:1: (ERROR/3) Unknown target name: "b".
.

Unknown role:
.
abc

{xyz}`a`
.
<string>:3: (ERROR/3) Unknown interpreted text role "xyz".
.

Unknown directive:
.

```{xyz}
```
.
<string>:2: (ERROR/3) Unknown directive type "xyz".
.

Bad Front Matter:
.
---
a: {
---
.
<string>:1: (ERROR/3) Front matter block:
while parsing a flow node
expected the node content, but found '<stream end>'
  in "<unicode string>", line 1, column 5:
    a: {
        ^
.

Bad HTML Meta
.
---
html_meta:
  empty:
  name noequals: value

---
.
<string>:: (ERROR/3) Error parsing meta tag attribute "empty": No content.
<string>:: (ERROR/3) Error parsing meta tag attribute "name noequals": no '=' in noequals.
.

Directive parsing error:
.

```{class}
```
.
<string>:2: (ERROR/3) Directive 'class': 1 argument(s) required, 0 supplied
.

Directive run error:
.

```{date}
x
```
.
<string>:2: (ERROR/3) Invalid context: the "date" directive can only be used within a substitution definition.
.

Do not start headings at H1:
.
## title 1
.
<string>:1: (WARNING/2) Document headings start at H2, not H1 [myst.header]
.

Non-consecutive headings:
.
# title 1
### title 3
.
<string>:2: (WARNING/2) Non-consecutive header level increase; H1 to H3 [myst.header]
.

multiple footnote definitions
.
[^a]

[^a]: definition 1
[^a]: definition 2
.
<string>:: (WARNING/2) Multiple footnote definitions found for label: 'a' [myst.footnote]
.

Warnings in eval-rst
.
some external

lines

```{eval-rst}
some internal

lines

.. unknown:: some text

:unknown:`a`
```
.
<string>:10: (ERROR/3) Unknown directive type "unknown".

.. unknown:: some text

<string>:12: (ERROR/3) Unknown interpreted text role "unknown".
.

bad-option-value
.
```{note}
:class: [1]
```
.
<string>:1: (ERROR/3) Directive 'note': option "class" value not string (enclose with ""): [1]

:class: [1]

.

header nested in admonition
.
```{note}
# Header
```
.
<string>:2: (WARNING/2) Disallowed nested header found, converting to rubric [myst.nested_header]
.

nested parse warning
.
Paragraph

```{note}
:class: abc
:name: xyz

{unknown}`a`
```
.
<string>:7: (ERROR/3) Unknown interpreted text role "unknown".
.
