---
theme: apple-basic
layout: intro
---

# Portfolio Optimization

Using the D-Wave Hybrid Solver

<div class="absolute bottom-10">
  <span class="font-700">
    José Ossorio - March 24th 2023
  </span>
</div>


<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: image-right
image: '/stocks.png'
---

# Understanding the problem
## What's portfolio optimization?

Finding the best distribution of assets to maximize or minimize a desired metric

<br>

<div v-click="1">
  Examples:
  <ul>
    <li>Maximizing the return while limiting the risk</li>
    <li>Minimizing the risk while maintaining a minimum return</li>
  </ul>
</div>

<div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 443px;
  }
</style>

---
layout: image-right
image: '/hpc.jpg'
---

<div class="container">
  <div>
    <h1>Classical Approaches</h1>
    <ul>
      <li v-click="">Linear Programming</li>
      <li v-click="">Quadratic Programming</li>
      <li v-click="">Genetic Algorithms</li>
    </ul>
    <h2 v-click>In general, heuristic methods</h2>
  </div>
</div>

<div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  li {
    font-size: 23px;
  }
  .container {
    display: flex;
  }
  img {
    position: absolute;
    left: 550px;
    top: 200px;
  }
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 443px;
  }
</style>

---
layout: statement
---

# Why take a hybrid approach?


<!-- <div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 47.7%;
  }
</style> -->

<!-- Notes: -->

---

# Why take a hybrid approach?

<div>
  <ul>
    <li v-click="1">Limited quantum resources</li>
    <li v-click="2">Suboptimal results in classical methods</li>
    <li v-click="3">Long runtimes in classical methods</li>
    <li v-click="4">Using the best of both worlds</li>
  </ul>
</div>

<div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  li {
    font-size: 23px;
  }
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 47.7%;
  }
</style>

---

# Current Quantum Solutions

<div>
  <ul>
    <li v-click="1">VQE</li>
    <li v-click="2">QAOA</li>
    <li v-click="3">Quantum Annealing <span v-click="4">👈</span></li>
  </ul>
</div>
<img v-click src="d-wave-advantage.jpg" class="d-wave-img"/>
<div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  li {
    font-size: 23px;
  }
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 47.7%;
  }
  .d-wave-img {
    height: 320px;
    width: 300px;
    position: absolute;
    left: 500px;
    bottom: 120px;
  }
</style>

---

<img src="hybrid-solvers.png" />
<p>Source: D-Wave</p>
<div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 47.7%;
  }
  p{
    font-size: 12px;
  }
</style>

---
layout: section
---

# Modeling the problem
## A QUBO formulation

<!-- <div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 47.7%;
  }
</style> -->

<!-- Notes: -->

---

# Things to consider

<div>
  <ul>
    <li v-click="1">The expected return</li>
    <li v-click="2">Cost of the portfolio</li>
    <li v-click="3">The interactions between stocks</li>
  </ul>
</div>

<div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  li {
    font-size: 23px;
  }
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 47.7%;
  }
</style>

---

# The expected return
## Our linear terms and objective function

$$Obj = \sum_{i=1}^{n}{r_ip_ix_i}$$

$r_i$ is the expected monthly return

$p_i$ is the price per share

$x_i$ how many shares to buy

<div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  .katex { font-size: 40px; }
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 47.7%;
  }
</style>

---

# The cost of the portfolio
## First constraint

$$C \le B$$

<div class="legend">

  $C$ is the total cost

  $B$ is the maximum budget

</div>

<div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  .katex { font-size: 40px; }
  .legend .katex {
    font-size: 28px;
  }
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 47.7%;
  }
</style>

---

# The cost of the portfolio
## First constraint

$$C \le B$$

$$\sum_{i=1}^n{p_ix_i} \le B$$

$p_i$ is the price per share

$x_i$ how many shares to buy

<div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  .katex { font-size: 40px; }
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 47.7%;
  }
</style>

---

# The interactions between stocks (Risk)
## Second constraint

$$R \le M$$

<div class="legend">

  $R$ is the risk

  $M$ is the maximum risk

</div>

<div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  .katex { font-size: 40px; }
  .legend .katex {
    font-size: 28px;
  }
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 47.7%;
  }
</style>

---

# The interactions between stocks (Risk)
## Second constraint

$$R \le M$$

$$\sum_{i=1}^{n}\sum_{j=1}^{n}{\sigma_{ij}p_ix_ip_jx_j} \le M$$

<div class="legend">

  $\sigma_{ij}$ is the covariance between stocks

  $p_i$ is the price per share

  $x_i$ how many shares to buy

</div>

<div class="page-num">
  <SlideCurrentNo /> / <SlidesTotal />
</div>

<style>
  .katex { font-size: 40px; }
  .legend .katex {
    font-size: 28px;
  }
  .page-num {
    position: absolute;
    bottom: 12px;
    left: 47.7%;
  }
</style>

---
layout: section
---

# Implementing the solution
## Using QPLEX

---

# What is Slidev?

Slidev is a slides maker and presenter designed for developers, consist of the following features

- 📝 **Text-based** - focus on the content with Markdown, and then style them later
- 🎨 **Themable** - theme can be shared and used with npm packages
- 🧑‍💻 **Developer Friendly** - code highlighting, live coding with autocompletion
- 🤹 **Interactive** - embedding Vue components to enhance your expressions
- 🎥 **Recording** - built-in recording and camera view
- 📤 **Portable** - export into PDF, PNGs, or even a hostable SPA
- 🛠 **Hackable** - anything possible on a webpage

<br>
<br>

Read more about [Why Slidev?](https://sli.dev/guide/why)

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->

---
transition: slide-up
---

# Navigation

Hover on the bottom-left corner to see the navigation's controls panel, [learn more](https://sli.dev/guide/navigation.html)

### Keyboard Shortcuts

|     |     |
| --- | --- |
| <kbd>right</kbd> / <kbd>space</kbd>| next animation or slide |
| <kbd>left</kbd>  / <kbd>shift</kbd><kbd>space</kbd> | previous animation or slide |
| <kbd>up</kbd> | previous slide |
| <kbd>down</kbd> | next slide |

<!-- https://sli.dev/guide/animations.html#click-animations -->
<img
  v-click
  class="absolute -bottom-9 -left-7 w-80 opacity-50"
  src="https://sli.dev/assets/arrow-bottom-left.svg"
/>
<p v-after class="absolute bottom-23 left-45 opacity-30 transform -rotate-10">Here!</p>

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# Code

Use code snippets and get the highlighting directly![^1]

```ts {all|2|1-6|9|all}
interface User {
  id: number
  firstName: string
  lastName: string
  role: string
}

function updateUser(id: number, update: User) {
  const user = getUser(id)
  const newUser = { ...user, ...update }
  saveUser(id, newUser)
}
```

<arrow v-click="3" x1="400" y1="420" x2="230" y2="330" color="#564" width="3" arrowSize="1" />

[^1]: [Learn More](https://sli.dev/guide/syntax.html#line-highlighting)

<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---

# Components

<div grid="~ cols-2 gap-4">
<div>

You can use Vue components directly inside your slides.

We have provided a few built-in components like `<Tweet/>` and `<Youtube/>` that you can use directly. And adding your custom components is also super easy.

```html
<Counter :count="10" />
```

<!-- ./components/Counter.vue -->
<Counter :count="10" m="t-4" />

Check out [the guides](https://sli.dev/builtin/components.html) for more.

</div>
<div>

```html
<Tweet id="1390115482657726468" />
```

<Tweet id="1390115482657726468" scale="0.65" />

</div>
</div>

<!--
Presenter note with **bold**, *italic*, and ~~striked~~ text.

Also, HTML elements are valid:
<div class="flex w-full">
  <span style="flex-grow: 1;">Left content</span>
  <span>Right content</span>
</div>
-->


---
class: px-20
---

# Themes

Slidev comes with powerful theming support. Themes can provide styles, layouts, components, or even configurations for tools. Switching between themes by just **one edit** in your frontmatter:

<div grid="~ cols-2 gap-2" m="-t-2">

```yaml
---
theme: default
---
```

```yaml
---
theme: seriph
---
```

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true">

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-seriph/01.png?raw=true">

</div>

Read more about [How to use a theme](https://sli.dev/themes/use.html) and
check out the [Awesome Themes Gallery](https://sli.dev/themes/gallery.html).

---
preload: false
---

# Animations

Animations are powered by [@vueuse/motion](https://motion.vueuse.org/).

```html
<div
  v-motion
  :initial="{ x: -80 }"
  :enter="{ x: 0 }">
  Slidev
</div>
```

<div class="w-60 relative mt-6">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-square.png"
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-circle.png"
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-triangle.png"
    />
  </div>

  <div
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 2000, duration: 1000 } }">
    Slidev
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 2
  }
}
</script>

<div
  v-motion
  :initial="{ x:35, y: 40, opacity: 0}"
  :enter="{ y: 0, opacity: 1, transition: { delay: 3500 } }">

[Learn More](https://sli.dev/guide/animations.html#motion)

</div>

---

# LaTeX

LaTeX is supported out-of-box powered by [KaTeX](https://katex.org/).

<br>

Inline $\sqrt{3x-1}+(1+x)^2$

Block
$$
\begin{array}{c}

\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &
= \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\

\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\

\nabla \cdot \vec{\mathbf{B}} & = 0

\end{array}
$$

<br>

[Learn more](https://sli.dev/guide/syntax#latex)

---

# Diagrams

You can create diagrams / graphs from textual descriptions, directly in your Markdown.

<div class="grid grid-cols-3 gap-10 pt-4 -mb-6">

```mermaid {scale: 0.5}
sequenceDiagram
    Alice->John: Hello John, how are you?
    Note over Alice,John: A typical interaction
```

```mermaid {theme: 'neutral', scale: 0.8}
graph TD
B[Text] --> C{Decision}
C -->|One| D[Result 1]
C -->|Two| E[Result 2]
```

```plantuml {scale: 0.7}
@startuml

package "Some Group" {
  HTTP - [First Component]
  [Another Component]
}

node "Other Groups" {
  FTP - [Second Component]
  [First Component] --> FTP
}

cloud {
  [Example 1]
}


database "MySql" {
  folder "This is my folder" {
    [Folder 3]
  }
  frame "Foo" {
    [Frame 4]
  }
}


[Another Component] --> [Example 1]
[Example 1] --> [Folder 3]
[Folder 3] --> [Frame 4]

@enduml
```

</div>

[Learn More](https://sli.dev/guide/syntax.html#diagrams)

---
src: ./pages/multiple-entries.md
hide: false
---

---
layout: center
class: text-center
---

# Learn More

[Documentations](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/showcases.html)