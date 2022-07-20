---
theme: apple-basic
class: ''
fonts:
  sans: DM Sans
  serif: DM Serif Display
  mono: DM Mono
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
layout: intro
title: Enjoying the Vue
---

<h1> Enjoying the <b text="green-500">Vue</b></h1>

How vue makes your life easier

<div opacity="70">
by Kaleb Ercanbrack
</div>

<img class="w-60 absolute right-25 top-50" src="/vue-logo.png" >

<!--
My name is Kaleb
-->

---

# About Vue
![GitHub stars](https://img.shields.io/github/stars/vuejs/vue.svg?style=social&label=Star&maxAge=2592000)
- Initial release in February 2014
- Created by Evan You. Previously at Google
- Not backed by any one company

## Companies using it
- Adobe (Behance)
- Gitlab
- Zoom
- [TikTok](https://www.tiktok.com/business/es)
- Several Chinese companies (Alibaba, Tencent, Baidu)

Very popular in the Laravel community
<!-- The github stars gap used to be much wider if I remember right. -->
---
layout: section
---

# Stats
[performance results](https://rawgit.com/krausest/js-framework-benchmark/master/webdriver-ts-results/table.html)
<img class="w-[600px]"  src="/npm-trends.png" >

<!--
Just pure rendering performance, may not be indicative of real world performance.

Honestly not sure how to interpret the performance stats
-->

---

# What is Vue?

Vue is a progressive JavaScript framework. It can easily be added into an existing site to make complex reactive user interfaces. No build step required.
<Counter :count="0" />

```html
<script src="https://unpkg.com/vue@3/dist/vue.global.prod.js"></script>

<!-- uses standard HTML -->
<div id="app">
  <button @click="count++" type="button">Count is: {{ count }}</button>
</div>

<script>
  //a global Vue object is created
  const { createApp } = Vue;
  createApp({
    data() {
      //defining our state in a data() method
      return {
        count: 0,
      };
    },
  }).mount("#app"); //mounting it on an element with a given ID. You could also pass in an HTMLElement
</script>
```

<!--
about the simplest vue app you can create
-->

---
layout: two-cols
---

# Single File Components (SFC)
Most of the time though you'll be using a build step. But that means we can use SFCs!

- HTML, JavaScript, and Styling all in one file
- can use different languages  `<style lang="scss">` `<script lang="ts">` `<template lang="pug">`
- allows for better tooling like `<script setup>`, using vue values in `<style>`, reactivity transform. 
  We'll cover these later
::right::
## `MyComponent.vue`
```vue
<template>
<div>
  <button @click="count++" class="btn" type="button"> 
    Count is: {{ count }} 
  </button>
  <button @click="reset" type="button"> reset </button>
</div>
</template>

<script>
export default {
  data(){
    return {
      count: 0
    }
  },
}
</script>

<style scoped>
.btn {
  background-color: #ffffff;
  border: 1px solid #dadfea;
  padding: 3rem;
  border-radius: 6px;
}
</style>

```

---
layout: section
---

# Working with data
data properties, methods, computed properties, and props are all accessible through `this` and are available in the template

[Stackblitz](https://stackblitz.com/edit/vitejs-vite-ysqzo2?file=src%2FApp.vue&terminal=dev)

<!--
Data() is the base of where your component state would be defined. 

Computed() properties are based off of some Data value.

Everything is accessible through "this". This refers to the Component Instance or "vm" as its commonly called in code.
-->

---
layout: section
---
# Vue Adapts
In a state of the vuenion presentation in june 2022, Evan You talked about a new experimental compilation strategy
that makes it much more like Svelte or Solid.js since it would have no virtual DOM and is compiler centric