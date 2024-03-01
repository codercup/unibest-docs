# 常见问题

## 1.修改 `pages.json` 被覆盖问题

本项目引入了 `@uni-helper/vite-plugin-uni-pages`，`pages.json` 文件将会自动生成，手动修改 `pages.json` 将会被覆盖。

全局的东西请在 `pages.config.ts` 里面配置，页面的东西请在 `vue` 文件的 `route` 代码快配置。详情请看 [视图章节](./guide/views)。

## 2.修改 `manifest.json` 被覆盖问题

本项目引入了 `@uni-helper/vite-plugin-uni-manifest`，`manifest.json` 文件将会自动生成，手动修改 `manifest.json` 将会被覆盖。

需要修改的东西请在 `manifest.config.ts` 里面编写。


## 3.怎么分包？

`vite.config.ts` 里面有一个配置，如下：(其中 `subPackages` 就是用来分包的)

也可以查看 [过滤和分包 章节](./guide/views#过滤和分包)
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