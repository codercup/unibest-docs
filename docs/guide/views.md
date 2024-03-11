# 视图

## App.vue

`App.vue` 是 uni-app 应用主组件和入口文件，所有页面都是在 `App.vue` 下进行切换的。

`App.vue` 本身不是页面，这里不能编写视图元素，也就是不能使用 `<template>`。

[应用生命周期](https://uniapp.dcloud.net.cn/collocation/App.html#applifecycle) 只能在 `App.vue` 中监听，在页面监听无效。

## Pages 页面

得益于 [@uni-helper/vite-plugin-uni-pages](https://github.com/uni-helper/vite-plugin-uni-pages)，约定式路由（文件路由）的实现轻而易举。

`src/pages` 目录下的每个文件都代表着一个路由。要创建新页面，只需要在这个目录里新增 `.vue` 文件，插件会自动生成对应的 `pages.json` 文件。

`route` 代码块则可以配置页面相关信息，这些信息会自动同步到 `page.json`，无需切换到 `page.json` 进行配置。

::: warning
`pages.json` 文件是自动生成的，请不要手动修改，全局的东西请在 `pages.config.ts` 里面配置，页面上的东西请在 `vue` 文件的 `route` 代码块配置，如下图。
:::

:::code-group

```vue [src/pages/index.vue]
<!-- 使用 type="home" 属性设置首页，其他页面不需要设置，默认为page -->
<!-- 推荐使用json5，更强大，且允许注释 -->
<route lang="json5" type="home">
{
  style: {
    navigationStyle: 'custom',
    navigationBarTitleText: '首页',
  },
}
</route>
<template>
  <div>
    <h1>欢迎使用 unibest</h1>
    <h4>unibest 是最好的 uniapp 开发模板</h4>
  </div>
</template>
```

```vue [src/pages/about.vue]
<route lang="json5">
{
  style: {
    navigationBarTitleText: '关于',
  },
}
</route>
<template>
  <view>
    <view>通过 `/pages/about` 来访问这个页面</view>
  </view>
</template>
```

:::

## Pages 过滤和分包

- 过滤

默认 `src/pages` 里面的 `vue` 文件都会生成一个页面，如果不需要生成页面可以对 `vite.config.ts` 中的 `UniPages` 进行 `exclude` 配置。如下示例，可以过滤掉 `所有的components里面的页面`。

:::code-group

```ts [vite.config.ts]{2}
UniPages({
  exclude: ['**/components/**/**.*'],
  routeBlockLang: 'json5',
  homePage: 'pages/index/index',
  subPackages: ['src/pages-sub'], // 是个数组，可以配置多个
})
```

:::

- 分包

如果需要设置 `分包` 则可以通过 `subPackages` 进行配置，该配置项是个数组，可以配置多个 `分包`。如下示例，配置了一个 `pages-sub` 分包，最终会在 `pages.json` 里面生成对一个的分包信息。

:::code-group

```ts [vite.config.ts]{5}
UniPages({
  exclude: ['**/components/**/**.*'],
  routeBlockLang: 'json5',
  homePage: 'pages/index/index',
  subPackages: ['src/pages-sub'], // 是个数组，可以配置多个
})
```

:::

## Layouts 布局

得益于 [@uni-helper/vite-plugin-uni-layouts](https://github.com/uni-helper/vite-plugin-uni-layouts)，你可以轻松地切换不同的布局。

`src/layouts` 文件夹下的 `vue` 文件都会自动生成一个布局，默认的布局文件名为 `default.vue` （ `unibest` 已经内置该文件）。

如果需要修改使用的布局，可以通过 `vue` 文件内 `route` 代码块指定需要的布局。

:::code-group

```vue [src/pages/demo.vue]{3}
<route lang="json5">
{
  layout: 'demo',
  style: {
    navigationBarTitleText: '关于',
  },
}
</route>
```

```vue [src/layouts/demo.vue]
<template>
  <view>
    <!-- 这里可以写通用的布局，比如导航栏，tabbar等 -->
    <!-- slot里面装的就是子页面的内容 -->
    <slot />
  </view>
</template>
```

:::

## Components 组件

得益于 [@uni-helper/vite-plugin-uni-components](https://github.com/uni-helper/vite-plugin-uni-components)，组件将自动注册到全局，你不需要显式导入它们。只需要在 `src/components` 目录下创建组件，然后直接使用即可。

:::tip
不可滥用自动导入，不是全局要用的组件不建议放到 `src/components` 里面，会增加包的体积。
:::

:::code-group

```vue [src/pages/index.vue]
<template>
  <div>
    <h1>欢迎使用 unibest</h1>
    <FgTest> 这个组件会自动导入 </FgTest>
  </div>
</template>
```

```vue [src/components/FgTest.vue]
<template>
  <span>
    <slot />
  </span>
</template>
```

:::

:::warning
如果包体积太大，可以考虑是否把全局组件移出 `src/components`，或者直接删除本插件。
:::
