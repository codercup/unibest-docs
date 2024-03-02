# 代码块

`VS Code` 的 `Code Snippets` 代码块可以大大加快 `vue` 文件的生成。

## `v3` 代码块

在新建的 `vue` 文件中输入 `v3` 即可触发代码块，操作 `gif` 如下:

![snippets3](./gifs/snippets3.gif)

## 代码块配置

除了 `v3` 代码块，我们还可以添加 `te` (template) 代码块，`sc` (script) 代码块，`st` (style) 代码块。

代码块完整配置如下：

:::code-group

```json [.vscode/vue3.code-snippets]
{
  "Print unibest Vue3 SFC": {
    "scope": "vue",
    "prefix": "v3",
    "body": [
      "<route lang=\"json5\" type=\"page\">",
      "{",
      "  style: { navigationBarTitleText: '$1' },",
      "}",
      "</route>\n",
      "<template>",
      "  <view class=\"\">$2</view>",
      "</template>\n",
      "<script lang=\"ts\" setup>",
      "//$3",
      "</script>\n",
      "<style lang=\"scss\" scoped>",
      "//",
      "</style>\n"
    ]
  },
  "Print unibest style": {
    "scope": "vue",
    "prefix": "st",
    "body": ["<style lang=\"scss\" scoped>", "//", "</style>\n"]
  },
  "Print unibest script": {
    "scope": "vue",
    "prefix": "sc",
    "body": ["<script lang=\"ts\" setup>", "//$3", "</script>\n"]
  },
  "Print unibest template": {
    "scope": "vue",
    "prefix": "te",
    "body": ["<template>", "  <view class=\"\">$1</view>", "</template>\n"]
  }
}
```

<div class='busuanzi_container'>
    <span id="busuanzi_container_site_pv">
    本站总访问量<span id="busuanzi_value_site_pv"></span>次
    </span>
    <span id="busuanzi_container_site_uv">
    本站访客数<span id="busuanzi_value_site_uv"></span>人次
    </span>
    <span id="busuanzi_container_page_pv">
    本文总阅读量<span id="busuanzi_value_page_pv"></span>次
  </span>
</div>
