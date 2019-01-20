---
layout: home
logo: logo.png
intro: 
  - <a href="https://www.npmjs.com/package/vuepress-theme-jupiter"><img src="https://img.shields.io/npm/v/vuepress-theme-jupiter.svg?style=flat-square"/></a>
  - Jupiter is a simple theme for VuePress. It uses bulma-jupiter CSS frameworks, supports LaTeX rendering, code syntax highlighting and many more features!
  - <a href="/guide/"><button class="button is-dark">Guide →</button></a>
---

## Install
```bash
$ yarn add vuepress-theme-jupiter
```
**Note:** VuePress supports themes from v1.0, which is now an alpha version, so you must install `vuepress@next` to use this plugin.

## Usage
Configure your VuePress site at `.vuepress/config.js`:
```js
module.exports = {
  theme: 'jupiter' // or 'vuepress-theme-jupiter'
}
```

See the [documentation of VuePress](https://vuepress.vuejs.org/theme/using-a-theme.html) for more information.

## Features
- Built-in $\LaTeX$ support
- Code highlight by [octref/shiki](https://github.com/octref/shiki)

![photo](photo.jpg)
