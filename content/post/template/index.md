---
title: Title of the Blog
summary: Blog summary in a sentance
date: 2024-07-18

#Featured image
image:
    caption: 'Image credit: [**Unsplash**](https://unsplash.com)'

authors:
    - admin
    # add additional authors if present to the list

tags:
    - Academic
    - Hugo Blox
    - Markdown
---

Welcome 👋

{{< toc mobile_only=true is_open=true >}}

## Basics
Types of List:
1. Item1
2. Item2
3. Item3

- Item1
- Item2
- Item3

Links:
[**Create a new site**](https://hugoblox.com/templates/)
### Section 1

#### Subsection 1

#### Subsection 2

## Ideation
Hugo Blox supports a Markdown extension for mindmaps.

### Simple Mindmap
```markmap {height="200px"}
- Hugo Modules
  - Hugo Blox
  - blox-plugins-netlify
  - blox-plugins-netlify-cms
  - blox-plugins-reveal
```
### Advanced Mindmap
```markmap
- Mindmaps
  - Links
    - [Hugo Blox Docs](https://docs.hugoblox.com/)
    - [Discord Community](https://discord.gg/z8wNYzb)
    - [GitHub](https://github.com/HugoBlox/hugo-blox-builder)
  - Features
    - Markdown formatting
    - **inline** ~~text~~ *styles*
    - multiline
      text
    - `inline code`
    -
      ```js
      console.log('hello');
      console.log('code block');
      ```
    - Math: $x = {-b \pm \sqrt{b^2-4ac} \over 2a}$
```
## Hilighting
<mark>Highlight</mark> important text with `mark`:

## Callouts
By wrapping a paragraph in `{{%/* callout note */%}} ... {{%/* /callout */%}}`, it will render as an aside.

{{% callout note %}}
A Markdown aside is useful for displaying notices, hints, or definitions to your readers.
{{% /callout %}}

## Warning
Or use the `warning` callout type so your readers don't miss critical details:

{{% callout warning %}}
A Markdown aside is useful for displaying notices, hints, or definitions to your readers.
{{% /callout %}}

## Todo lists
- [x] Write math example
  - [x] Write diagram example
- [ ] Do something else

## Video
{{< youtube D2vj0WcvH5c >}}

## Quiz
{{< spoiler text="👉 Click to view the solution" >}} You found me 🎉 {{< /spoiler >}}

## Math
### Inline Math
Example for an inline math is this - $\nabla F(\mathbf{x}_{n})$

$$\gamma_{n} = \frac{ \left | \left (\mathbf x_{n} - \mathbf x_{n-1} \right )^T \left [\nabla F (\mathbf x_{n}) - \nabla F (\mathbf x_{n-1}) \right ] \right |}{\left \|\nabla F(\mathbf{x}_{n}) - \nabla F(\mathbf{x}_{n-1}) \right \|^2}$$

## Multiline math
$$
f(k;p_{0}^{*}) = \begin{cases}p_{0}^{*} & \text{if }k=1, \\
1-p_{0}^{*} & \text{if }k=0.\end{cases}
$$

## Code
```python
import pandas as pd
data = pd.read_csv("data.csv")
data.head()
```

## Inline Image
{{< icon name="python" >}} Python