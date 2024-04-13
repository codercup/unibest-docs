# pinia 全局状态管理

`unibest` 已经内置了 `Pinia` + `pinia-plugin-persistedstate`(数据持久化插件)，并提供了开箱即用的示例。

:::code-group

```ts [src/store/count.ts]{26}
import { defineStore } from 'pinia'
import { ref } from 'vue'

export const useCountStore = defineStore(
  'count',
  () => {
    const count = ref(0)
    const increment = () => {
      count.value++
    }
    const decrement = () => {
      count.value--
    }
    const reset = () => {
      count.value = 0
    }
    return {
      count,
      decrement,
      increment,
      reset,
    }
  },
  {
    // 如果需要持久化就写 true, 不需要持久化就写 false（或者去掉这个配置项）
    persist: true,
  },
)
```

```vue [src/pages/demo.vue]
<template>
  <view class="flex justify-center items-center text-blue-500 mt-4 mb-4">
    <view class="w-20">Count: {{ countStore.count }}</view>
    <button class="ml-2 mr-2" @click="countStore.decrement">-1</button>
    <button class="ml-2 mr-2" @click="countStore.increment">+1</button>
    <button class="ml-2 mr-2" @click="countStore.reset">重置</button>
  </view>
</template>

<script lang="ts" setup>
import { useCountStore } from '@/store'

const countStore = useCountStore()
</script>
```

:::

::: tip
请不要随意把数据丢到 `pinia`，如果是简单状态管理，尽量使用 `ref` 或者 `reactive`，详情见 [简单状态管理章节](/advanced/state-easy).
:::
