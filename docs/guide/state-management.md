# 状态管理

得益于组合式方法（Composition API），管理状态非常简单。

## Pinia

[Pinia](https://pinia.vuejs.org/zh/) 是 `Vue` 官方最新推荐的状态管理库。

```shell
pnpm install pinia@2.0.36
```

::: warning
你可以在 [dcloudio/uni-app#4350](https://github.com/dcloudio/uni-app/issues/4350) 了解为什么要固定 pinia 版本号。
:::

安装依赖后，需要做基本设置。

:::code-group

```ts [src/main.ts]
import { createSSRApp } from 'vue'
import { createPinia } from 'pinia'
import App from './App.vue'

const pinia = createPinia()

export function createApp() {
  const app = createSSRApp(App).use(pinia)
  return {
    app,
  }
}
```

```ts [src/stores/counter.ts]
import { defineStore } from 'pinia'

export const useCounterStore = defineStore('counter', () => {
  const count = ref(0)
  function increment() {
    count.value++
  }
  return { count, increment }
})
```

```vue [src/pages/index/index.vue]
<script setup lang="ts">
import { useCounterStore } from '../../stores/counter'

const counterStore = useCounterStore()
counterStore.count // 0
counterStore.increment()
counterStore.count // 1
</script>
```

:::

:::tip
`unibest` 里面安装了 `pinia-plugin-persistedstate` 数据持久化，并进行了 `uniapp` 的适配，上面的部分代码有更新，这里不再贴代码。
:::

## 简单状态管理

你可以直接使用 `Vue` 提供的 `ref` 或 `reactive` 方法来做简单状态管理。

### ref

::: code-group

```ts [src/composables/useCount.ts]
// 全局状态
const globalCount = ref(1)
export function useCount() {
  // 本地状态
  const localCount = ref(1)
  function increment() {
    globalCount.value++
    localCount.value++
  }
  return {
    globalCount,
    localCount,
    increment,
  }
}
```

```vue [src/pages/index.vue]
<script setup lang="ts">
// 自动导入
const { globalCount, localCount, increment } = useCount()
</script>

<template>
  <button @click="increment()">
    {{ globalCount }}
    {{ localCount }}
  </button>
</template>
```

:::

### reactive

::: code-group

```ts [src/stores/count.ts]
export const countStore = reactive({
  count: 0,
  increment() {
    this.count++
  },
})
```

```vue [src/pages/index.vue]
<template>
  <!-- 自动导入 -->
  <button @click="countStore.increment()">
    {{ countStore.count }}
  </button>
</template>
```

:::

::: tip
以上例子修改自 Vue 文档的 [用响应式 API 做简单状态管理](https://cn.vuejs.org/guide/scaling-up/state-management.html#simple-state-management-with-reactivity-api)。
:::
