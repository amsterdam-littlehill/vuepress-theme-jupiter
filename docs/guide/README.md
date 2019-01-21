---
toc: true
---
# Guide

Jupiter is a simple theme for VuePress. It uses bulma-jupiter CSS frameworks, supports LaTeX rendering, code syntax highlighting and many more features.

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

## Navbar
You can add items to navbar above by editing `.vuepress/config.js`:
```js
module.exports = {
  themeConfig: {
    nav: [
      { text: 'Guide', link: '/guide/' },
      // and more
    ]
  }
}
```

## Homepage hero
First, set your site's title and description in `.vuepress/config.js`:
```js
module.exports = {
  title: 'Vuepress theme Jupiter',
  description: 'A simple theme for VuePress'
}
```
Then, add frontmatter to the root `README.md` file to tell it's the homepage:
```yaml
---
layout: home
---

# Your homepage contents
```
Also, you can add introduction paragraphs in the hero part. You can give one:
```yaml
---
layout: home
intro: Jupiter is a simple theme for VuePress!
---
```
or more than one:
```yaml
---
layout: home
intro: 
  - <a href="https://www.npmjs.com/package/vuepress-theme-jupiter"><img src="https://img.shields.io/npm/v/vuepress-theme-jupiter.svg?style=flat-square"/></a>
  - Jupiter is a simple theme for VuePress!
  - Enjoy this!
---
```

## Homepage logo
You can put your logo at `.vuepress/public/path-to-yout-logo.png` and edit frontmatter of the root `README.md` file:
```yaml
---
layout: home
logo: path-to-yout-logo.png
---

# Your homepage contents
```

## Table of content support
Table of content can be add to a page. Edit frontmatter of the root `README.md` file:
```yaml
---
toc: true
---

# Your homepage contents
```
and TOC will appear. See [this page](/guide/toc-test.html) for example.
