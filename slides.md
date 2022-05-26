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
introImage: '/intro1.png'
---

# Website optimization

How to improve the performance of a website

<img src="/intro1.png" class="absolute top-20 left-20 rounded-full w-80 h-80 object-cover p-2 bg-gradient-to-r from-fuchsia-700 to-purple-800 dark:from-white dark:to-purple-50">


<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: table-contents
gradientColors:
  - '#8EC5FC'
  - '#E0C3FC'
handle: tult
website: https://rikkeisoft.com
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

<div v-click>
  <cil-hand-point-right class="text-green-600" />
  The longger a webpage takes to load, the more it bounce rate will skyrocket 
The longger a webpage takes to load, the more it bounce rate will skyrocket 
  The longger a webpage takes to load, the more it bounce rate will skyrocket 
  <mdi-rocket-launch class="text-red-600" /><br>
</div>
<div v-click>
  <cil-hand-point-right class="text-green-600" />
  The high bounce rate tells search engines that this page is useless, so its ranking will slip
  <lucide-trending-down class="text-red-600" />
</div>
<div v-click>
  <br>
  <div class="flex flex-row relative">
    <img class="w-3/5 object-contain" src="/did-you-know.webp" />
    <img class="absolute -right-36 -bottom-32 w-3/5 object-contain" src="/bounce-rate-statistics.webp" />
  </div>
</div>


---
layour: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
--- 

# What factor affect website load time?

- User's internet connection
- Web hoisting and user's computer
- The size of the resources that needed <fluent-target-arrow-24-regular class="text-red-600" v-click />


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
  <ul>
    <li>DOM stands for document object model.</li>
    <li>When browser encounters a HTML element, it creates a JavaScript object called a node.</li>
    <li>After create a node, the browser has to create a <span class="font-bold">tree-like structure</span> of created nodes.</li>
  </ul>
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
  <ul>
    <li>CSSOM stands for CSS object model.</li>
    <li>After the browser has done constructing the DOM, it'll read CSS from all the sources (external, embedded, inline, user-agent, etc.) to construct CSSOM.</li>
    <li>Each node in CSSOM tree contains the style information that will be applied to DOM elements that it target.</li>
  </ul>
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

# Parsing

- **Parsing** the the process of reading HTML and constructing the DOM tree from it.
- The browser starts the parsing process as soon as it recevices few bytes of HTML document.
- Because of that, the browser can build the DOM tree **incrementally**.

<div class="w-full flex justify-center">
  <img class="object-contain" src="/Parsing.png">
</div>
<p class="text-center text-xs">Parse raw HTML codes into a DOM tree</p>

<!-- 
- Quá trình parsing và xây dựng DOM tree gọi là DOM parsing 
- Chương trình thực hiện quá trình trên gọi là DOM parser
- Chạy demo trang web ở địa chỉ /html/incremental.html chứng minh incremental. Bật throttling để giảm tốc độ mạng
1. Chú ý thanh cuộn càng ngàng càng ngắn
2. Tích chọn capture screenshoots trong dev tools -> screenshoot ở sau có nhiều nội dung hơn screenshoot ở trước
 -->

---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

# External resources & parser-blocking script


- Whenever the browser encounters a external resouces, it'll start download that file <br> in background **except** for script files. Hence script files are called **parser-blocking**.
- DOM parsing is executed on the main thread and will not progress if that thread is busy.

<br>

<div class="flex flex-column justify-between items-center">
  <div>
    <cil-hand-point-right class="text-green-400" /> A script (JavaScript)
  </div>
  <div class="leading-10">
  <div v-click="1">
    <arrow x1="220" y1="290" x2="400" y2="260" color="#564" width="3" arrowSize="1"  />
    <p>Embedded scripts <ic-baseline-arrow-forward /> Executing the embedded codes on the main thread.</p>
  </div>
  <div v-click="2">
    <arrow x1="220" y1="300" x2="400" y2="310" color="#564" width="3" arrowSize="1"  />
    <p>External script file <ic-baseline-arrow-forward /> Halt the execution of the main thread <br> until that file is downloaded and executed</p>
  </div>
  </div>
</div>

<div v-click="3">
  <ic-baseline-question-mark class="text-red-400 text-2xl mt-8" /> Halting the DOM parsing while the script file is being downloaded is unnecessary (in most cases). What is the solution ?
</div>

<!-- 
- Tại sao phải halt the main thread cho đến khi file script được download và thực thi xong ? 
- Vì Browser cung cấp DOM API cho JavaScript runtime (React hoạt động bằng cách này) -> nếu DOM parsing và script được thực thi đồng thời 
thì sẽ có thể gây ra tình trạng race conditions 
-->

---
layout: cover
handle: tult
website: https://rikkeisoft.com
---

# Async & defer attributes

- HTML5 provides us `async` and `defer` attribute for `script` tag.
- With `async`, the parsing process won't be blocked while the file is being downloaded. And will be block right after the script file is ready to be executed.
- With `defer`, the script doesn't execute even when the file is fully downloaded. All `defer` scripts are executed once the DOM is fully constructed.

<!--
Chạy demo cho blocking script ở địa chỉ http://localhost:8088/html/parser-blocking.html
- Lưu ý: throttling network 
- 1 script thường đc chèn vào sau 30 thẻ h1 -> in đc 30 thẻ h1 thì bị block
- 1 defer script đc chèn sau 40 thẻ h1 -> in bình thường toàn bộ các thẻ h1 sau đó ms thực hiện script
- thời điểm thực thi code có thể check bằng console.log

- Note: 
+ Vì async sẽ thực thi ngay khi tải xong file nên các file scripts ko thực thi theo thứ tự như trong file html 
+ defer thì sẽ thực thi theo thứ tự vì nó đợi đến khi pars
-->

---
layout: cover
handle: tult
website: https://rikkeisoft.com
---

# Render-Blocking CSS

- Render tree is getting built incrementally as the DOM tree is getting constructed.
- The browser constructs the CSSOM tree from the stylesheet content
- The CSSOM tree construction is **not incremental**

<!--
- Khi browser gặp thẻ style, browser sẽ parser toàn bộ CSS và update CSSOM tree. Sau đó nó tiếp tục quá trình DOM parsing. Tương tự cho inline style
  
- Đối với external stylesheet files. Không như HTML file, nó phải đợi cho toàn bộ file stylesheet được tải về rồi mới thực hiện parsing.(g)

- Khi toàn bộ CSS rules đc process và CSSOM tree được update thì render tree ms đc update và render giao diện ra màn hình. Trong thời gian đó thì render tree bị halt.

- Demo ở trang http://localhost:8088/html/render-blocking.html
-->

---
layout: cover
handle: tult
website: https://rikkeisoft.com
---

# Script-Blocking CSS

<uiw-question-circle class="text-red-500 mt-8" /> Scenario where the browser start downloading the stylesheet file, then it encounter an external script file and start downloading it. 
The script file is downloaded before the stylesheet file ? In this case, should the browser start executing the script?

<div v-click class="mt-12">
  <ic-baseline-anchor class="text-green-600" /> In conclusion, the browser may fully downloaded the script but will not execute it unless all the stylesheets before it are parsed. Those stylesheets are called script-blocking.
</div>

---
layout: cover
handle: tult
website: https://rikkeisoft.com
---

# General rules

1. Injecting stylesheet or required script files in the `<head>` tag of the HTML document. 
2. Use `rel="preload"` to instruct the browser to download key resources as soon as possible.
3. The best place to inject script files is the end of `<body>` tag.

<!--
- Vì HTML file được parse lần lượt và việc download script file ko block DOM construction. Nên càng tải sớm các file stylesheet thì giao điện được render càng sớm
-->

---
layout: new-section
handle: 'tult'
website: 'https://rikkeisoft.com'
sectionImage: '/section-illustration.svg'
---

# Core web vitals

The metrics to evaluate the user's experiences 

---
layout: cover
handle: tult
website: https://rikkeisoft.com
---


# Core web vitals 

<div>
  <img src="/core-web-vitals.png" />
</div>

<!-- Core web vitals là các metrics sử dụng để đánh giá 3 khía cạnh khi load một website đó là ....
Tương ứng với mỗi khía cạnh là một metrics để đánh giá chungs đó là  -->


---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

# Cumulative Layout Shift (CLS)

CLS is the metrics to evaluate how much the page's content jumps around.

<div v-click class="flex flex-row justity-center">
  <video controls width="400" class="self-center">
      <source src="/CLS.webm"
              type="video/webm">
  </video>
</div>

<!-- for a better web app performance, a minimal CLS score is the best  -->

---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

# What causes poor CLS ? 

<div class="relative">
  <img v-click-hide src="/poor-CLS.png" />
  <div v-after class="flex flex-row absolute top-1/2 left-1/4">
    <h1 class="ml-1">How to improve CLS ?</h1>
    <noto-thinking-face class="text-3xl mb-4 ml-2" />
  </div>
</div>

<!-- 
FOUT: flash of unstyled text 
FOIT: flash of invisible text
-->

---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---


# Always include width and height size attributes on images and video elemnts.

---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

<div class="relative">
  <video controls="controls" width="400" height="auto" name="Demo cls">
    <source src="/demo-cls.mov">
  </video>
  <img src="/CLS-score.png" alt="cls score" class="absolute right-0 w-1/2 h-auto bottom-22">
</div>

---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

```html
<!-- old best practice -->
<img src="avatar.png" width="640" height="360" alt="avatar">

<!-- response -->
<img src="avatar.png" alt="avatar">

<style>
  img {
    width: 100%;
    height: aut;
  }
</style>
```

<!-- 
Trước đây người ta dùng width / height property để set thuộc tính độ dài và độ rộng cho ảnh -> browser có thể preserve space cho ảnh trước cả khi chúng đc tải xong 
-->

---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

<div class="relative">
  <video controls="controls" width="400" height="auto" name="Demo cls">
    <source src="/demo-cls-after.mov">
  </video>
  <img src="/CLS-score-after.png" alt="cls score" class="absolute right-0 w-1/2 h-auto bottom-22">
</div>

<!-- - Làm thế nào để biết đc element nào khiến điểm CLS bị tăng lên ?  -->

---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

# Find large layout shift elements

<img src="/find-cls-elements.png" alt="find-cls-element" width="480" height="auto">

---
layout: cover
handle: 'tult'
website: 'https://rikkeisoft.com'
---

# Approach to image loading

<ic-sharp-report-problem class="text-red-600" /> <span class="text-red-600 font-bold">Problem:</span> <span>Creating empty space in the site and users don't know what things will come out from there</span> <fxemoji-ghost class="text-xl" />

<div v-click>
<el-idea-alt class="text-green-600" /> <span class="text-green-600 font-bold">Solution:</span>
<iframe class="mt-2" width="560" height="315" src="https://www.youtube.com/embed/CPmNHj9a0JI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<!--
Thực hiện lazy loading cho image. Ý tưởng chung là sẽ sử dụng 1 container bao lấy image. 
Trong thời gian image được load hoặc ở ngoài viewport -> sẽ hiển thị nội dung của container (background image, low quality image, ...)
- Layzy loading có thể được implement bằng rất nhiều cách.
-->