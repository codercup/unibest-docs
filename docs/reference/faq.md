# 常见问题

## 1.修改 `pages.json` 被覆盖问题

本项目引入了 `@uni-helper/vite-plugin-uni-pages`，`pages.json` 文件将会自动生成，手动修改 `pages.json` 将会被覆盖。

全局的东西请在 `pages.config.ts` 里面配置，页面的东西请在 `vue` 文件的 `route` 代码快配置。详情请看 [视图章节](/guide/views)。

## 2.修改 `manifest.json` 被覆盖问题

本项目引入了 `@uni-helper/vite-plugin-uni-manifest`，`manifest.json` 文件将会自动生成，手动修改 `manifest.json` 将会被覆盖。

需要修改的东西请在 `manifest.config.ts` 里面编写。

## 3.怎么分包？

`vite.config.ts` 里面有一个配置，如下：(其中 `subPackages` 就是用来分包的)

也可以查看 [过滤和分包 章节](/guide/views#过滤和分包)
:::code-group

```ts [vite.config.ts]{5}
UniPages({
    exclude: ['**/components/**/**.*'],
    routeBlockLang: 'json5',
    homePage: 'pages/index/index',
    subPackages: ['src/pages-sub'], // 是个数组，可以配置多个
}),
```

:::

## 4.支持 `uni-app x` 吗？

不支持。但我们一直保持关注。[uni-app x 传送门](https://doc.dcloud.net.cn/uni-app-x/)

`uni-app x` 是官方宣称的下一代 `uni-app`，是一个跨平台应用开发引擎。`uni-app x` 没有使用 `js` 和 `webview`，它基于 `uts` 语言。在 `App端`，`uts` 在 `iOS `编译为 `swift`、在 `Android` 编译为 `kotlin`，完全达到了原生应用的功能、性能。

目前 `uni-app x` 可以生成 `Android(kotlin)`，其他端（`iOS(swift)`、`鸿蒙`、`H5`、`各种小程序`）还在适配中。

## 5.`git commit` 报错。

请看 `commitlint.config.ts` 里面的配置，需要满足对应的设定。根据自己的需要，可以修改 `commitlint.config.ts` 里面的配置。

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
