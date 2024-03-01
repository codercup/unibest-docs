# 常见问题

## 1.修改 `pages.json` 被覆盖问题

本项目引入了 `@uni-helper/vite-plugin-uni-pages`，`pages.json` 文件将会自动生成，手动修改 `pages.json` 将会被覆盖。

全局的东西请在 `pages.config.ts` 里面配置，页面的东西请在 `vue` 文件的 `route` 代码快配置。详情请看 [视图章节](./views) 或 [unibest 源码](https://github.com/codercup/unibest)。

## 2.修改 `manifest.json` 被覆盖问题

本项目引入了 `@uni-helper/vite-plugin-uni-manifest`，`manifest.json` 文件将会自动生成，手动修改 `manifest.json` 将会被覆盖。

需要修改的东西请在 `manifest.config.ts` 里面编写。
