# 视图

## App.vue

`App.vue` 是 uni-app 应用主组件和入口文件，所有页面都是在 `App.vue` 下进行切换的。

`App.vue` 本身不是页面，这里不能编写视图元素，也就是不能使用 `<template>`。

[应用生命周期](https://uniapp.dcloud.net.cn/collocation/App.html#applifecycle) 只能在 `App.vue` 中监听，在页面监听无效。

::: tip 了解 `uni-app` 关于 `App.vue` 的更多信息

<https://uniapp.dcloud.net.cn/collocation/App.html>

:::

## Pages 页面

得益于 [@uni-helper/vite-plugin-uni-pages](https://github.com/uni-helper/vite-plugin-uni-pages)，约定式路由（文件路由）的实现轻而易举。

`src/pages` 目录下的每个文件都代表着一个路由。要创建新页面，只需要在这个目录里新增 `.vue` 文件，插件会自动生成对应的 `pages.json` 文件。

`route` 代码块则可以配置页面相关信息，这些信息会自动同步到 `page.json`，无需切换到 `page.json` 进行配置。

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

如果需要 `过滤` 某些页面，可以在 `vite.config.ts` 中使用 `exclude` 进行配置。如下示例，可以过滤掉 `所有的components里面的页面`。

如果需要设置 `分包` 则可以通过 `subPackages` 进行配置，该配置项是个数组，可以配置多个 `分包`。如下示例，配置了一个 `pages-sub` 分包，最终会在 `pages.json` 里面生成对一个的分包信息。

:::code-group

```ts [vite.config.ts]{9,12}
import { defineConfig, loadEnv } from 'vite'
// @see https://uni-helper.js.org/vite-plugin-uni-pages
import UniPages from '@uni-helper/vite-plugin-uni-pages'
import Uni from '@dcloudio/vite-plugin-uni'

return defineConfig({
  plugins: [
    UniPages({
      exclude: ['**/components/**/**.*'],
      routeBlockLang: 'json5',
      homePage: 'pages/index/index',
      subPackages: ['src/pages-sub'], // 是个数组，可以配置多个
    }),
    // UniXXX 需要在 Uni 之前引入
    Uni(),
  ],
})
```

:::

## Layouts 布局

得益于 [@uni-helper/vite-plugin-uni-layouts](https://github.com/uni-helper/vite-plugin-uni-layouts)，你可以轻松地切换不同的布局。

布局可以用来创建通用界面（如页眉和页脚显示）的包装器，不同的页面可能需要不同的布局。

`src/layouts/default.vue` 文件将作为默认布局，在页面文件内设置 `route` 代码块可以指定 `layout` 布局。

:::code-group

```vue [src/pages/index.vue]{3}
<route lang="json5" type="home">
{
  layout: 'default',
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

```vue [src/pages/about.vue]{3}
<route lang="json5">
{
  layout: 'demo',
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

```vue [src/layouts/default.vue]
<template>
  <div>
    <AppHeader />
    <!-- src/pages/index.vue 和 src/pages/about.vue 内容展示 -->
    <slot />
    <AppFooter />
  </div>
</template>
```

```vue [src/layouts/demo.vue]
<template>
  <div>
    <slot />
  </div>
</template>
```

:::

## Components 组件

得益于 [@uni-helper/vite-plugin-uni-components](https://github.com/uni-helper/vite-plugin-uni-components)，组件将自动注册到全局，你不需要显式导入它们。只需要在 `src/components` 目录下创建组件，然后直接使用即可。

:::code-group

```vue [src/pages/index.vue]
<template>
  <div>
    <h1>欢迎使用 vitess-uni-app</h1>
    <FlyDemo> 这个组件会自动导入 </FlyDemo>
  </div>
</template>
```

```vue [src/components/FlyDemo.vue]
<template>
  <span>
    <slot />
  </span>
</template>
```

:::
