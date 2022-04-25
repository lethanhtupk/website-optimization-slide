---
# try also 'default' to start simple
theme: unicorn
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
handle: 'tult'
website: 'https://rikkeisoft.com'
layout: 'intro'
introImage: '/intro.jpg'
---

# Website optimization

How to improve the performance of a website

<img src="/intro.jpg" class="absolute top-20 left-20 rounded-full w-80 h-80 object-cover p-2 bg-gradient-to-r from-fuchsia-700 to-purple-800 dark:from-white dark:to-purple-50">


<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: table-contents
gradientColors: ['#8EC5FC', '#E0C3FC']
handle: 'tult'
website: 'https://rikkeisoft.com'
---

<style>
  figure img.rounded-full {
    @apply w-10 h-10
  }
</style>

# Table of contents

1. Why speed matters? 
2. What factors affect website load time?
3. How the browser renders a webpage?

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

---
layout: new-section
handle: 'tult'
website: 'https://rikkeisoft.com'
sectionImage: '/section-illustration.svg'
---

# Why speed matters? 
Website load time affects the number of visitors.

---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

# Why speed matters?

<cil-hand-point-right class="text-green-600" />
The longger a webpage takes to load, the more it bounce rate will skyrocket 
<mdi-rocket-launch class="text-red-600" /><br>
<cil-hand-point-right class="text-green-600" />
The high bounce rate tells search engines that this page is useless, so its ranking will slip
<lucide-trending-down class="text-red-600" />
<br>
<div class="flex flex-row relative">
  <img class="w-3/5 object-contain" src="/did-you-know.webp" />
  <img class="absolute -right-36 -bottom-32 w-3/5 object-contain" src="/bounce-rate-statistics.webp" />
</div>

---
layour: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
--- 

# What factor affect website load time?

- User's internet connection
- Web hoisting and user's computer
- The size of the resources that needed


---
layout: new-section
handle: 'tult'
website: 'https://rikkeisoft.com'
---

# How the browser render a webpage

Deep dive into the rendering process and figure out where can be optimized.

---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

# DOM

<div class="flex flex-row">
  <div class="w-2/3">
    - DOM stands for document object model <br>
    - When browser encounters a HTML element, it creates a JavaScript object called a node. <br>
    - After create a node, the browser has to create a <span class="font-bold">tree-like structure</span> of created nodes.
  </div>
  <div class="w-1/3 pl-4">
    <img class="object-contain" src="/DOM.png">
  </div>
</div>

---
layout: cover
andle: 'tult'
website: 'https://rikkeisoft.com'
---

# CSSOM

<div class="flex flex-row">
  <div class="w-2/3">
    - CSSOM stands for CSS object model <br>
    - After the browser has done constructing the DOM, it'll read CSS from all the sources (external, embedded, inline, user-agent, etc.) to construct CSSOM. <br>
    - Each node in CSSOM tree contains the style information that will be applied to DOM elements that it target. 
  </div>
  <div class="w-1/3 pl-4">
    <img class="object-contain" src="/CSSOM.png">
  </div>
</div>


---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

# Render tree

- This is **tree-like structure** constructed by combining DOM and CSSOM trees together. 
- The browser calculate the layout for each **visible elements** and paint them on the screen.

<div class="w-full flex justify-center mt-8">
  <img src="/render-tree.png" class="object-contain">
</div>

---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

# Parsing and external resources

- **Parsing** the the process of reading HTML and constructing the DOM tree from it. <br> Hence this process is call **DOM parsing** and the program that does it is called **DOM parser**.
- When the browser requests for a webpage and the server response with some HTML text. <br> It starts the parsing process as soon as few characters are available.