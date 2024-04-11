# UI 库

## 默认使用 wot-ui 库

`unibest` 经过几次更迭，先后使用 `uni-ui`、`uv-ui`、`wot-ui` 库作为默认 UI 库，目前最新的模版使用 `wot-ui` 为默认 UI 库。

`wot-ui` 是 `vue3+ts` 编写的全端支持的 UI 库，编码体验比 `uv-ui` 更好；而官方维护的 `uni-ui` 则样式略丑，组件较少，故弃之。

具体 UI 库选型过程，请看我的掘金文章：[【unibest】 uniapp + vue3 模板 UI 框架选型](https://juejin.cn/post/7337513012393607207).

::: tip
`wot-ui` 全称 `wot-design-uni`，是 `wot-design` 的 `uniapp` 版本，文档地址：[https://wot-design-uni.gitee.io/](https://wot-design-uni.gitee.io/).
:::

## 卸载 wot-ui 库

如果不喜欢 `wot-ui`，可以卸载掉 `wot-ui` 库，使用其他 UI 库。

卸载过程如下：

- 1. 删除 `wot-ui` 库：
  ```sh
  pnpm un wot-design-uni
  ```
- 2. `pages.config.ts` 文件 `easycom.custom` 删除相关配置：

  ```diff
  easycom: {
      autoscan: true,
      custom: {
  -     '^wd-(.*)': 'wot-design-uni/components/wd-$1/wd-$1.vue',
      },
  },
  ```

- 3. ` tsconfig.json` 文件 `compilerOptions.types` 删除相关配置：

  ```diff
  "types": [
      "vite-env.d.ts",
      "@dcloudio/types",
      "@types/wechat-miniprogram",
      "@uni-helper/uni-app-types",
      "@uni-helper/uni-ui-types",
  -   "wot-design-uni/global.d.ts"
  ]
  ```

## 安装其他 UI 库

这里以 `uv-ui` 为例，其他 UI 库安装过程类似。

- 1. 安装 `uv-ui` 库：
  ```sh
  pnpm add @climblee/uv-ui
  ```
- 2. `pages.config.ts` 文件 `easycom.custom` 添加相关配置：
  ```diff
  easycom: {
    autoscan: true,
    custom: {
  +   '^uv-(.*)': '@climblee/uv-ui/components/uv-$1/uv-$1.vue',
    },
  },
  ```
- 3. ` tsconfig.json` 文件 `compilerOptions.types` 添加相关配置：
  ```diff
  "types": [
    "vite-env.d.ts",
    "@dcloudio/types",
    "@types/wechat-miniprogram",
    "@uni-helper/uni-app-types",
    "@uni-helper/uni-ui-types",
  + "@ttou/uv-typings/shim",
  + "@ttou/uv-typings/v2"
  ]
  ```
  :::tip
  注意：`@ttou/uv-typings/v2` 是 `v2` 不是 `v3`。
  :::
