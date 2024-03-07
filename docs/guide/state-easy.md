# 简单状态管理

你可以直接使用 `Vue` 提供的 `ref` 或 `reactive` 方法来做简单状态管理。

## ref

::: code-group

```ts [src/pages/demo/useCount.ts]
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

```vue [src/pages/demo/index.vue]
<script setup lang="ts">
import useCount from './useCount.ts'
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

## reactive

::: code-group

```ts [src/pages/demo/count.ts]
export const countStore = reactive({
  count: 0,
  increment() {
    this.count++
  },
})
```

```vue [src/pages/demo.vue]
<script setup lang="ts">
import { countStore } from './count.ts'
</script>

<template>
  <button @click="countStore.increment()">
    {{ countStore.count }}
  </button>
</template>
```

:::

::: tip
灵活使用 `ref` 和 `reactive` 处理本模块内部的状态。
:::
