# Mock

有的时候需要模拟接口调用，但又不想搞真的后台服务，这个时候 `Mock` 就可以派上用场了。

这里介绍 `vite-plugin-mock`，它是一个基于 `vite` 开发的 `mock` 插件，同时支持本地环境和生产环境。关键是调用请求时浏览器看得到真正的请求发出，最大还原真实项目的效果，很方便调试。

## 安装

```sh
pnpm add
```

## vite.config.ts 配置

```ts
plugins: [
  // 省略其他代码
  viteMockServe({
    ignore: /^_/,
    mockPath: 'mock',
    // 根据项目配置，可以配置在.env文件
    enable: true,
  }),
]
```

## 编写 mock 文件

根目录下新建 `mock` 文件夹，然后新建一个 `foo.ts` 文件，内容如下：

```ts
// mock/foo.ts

import { MockMethod } from 'vite-plugin-mock'

export default [
  {
    url: '/api/get',
    method: 'get',
    response: ({ query }) => {
      return {
        code: 0,
        result: {
          name: '菲鸽',
        },
      }
    },
  },
  {
    url: '/api/post',
    method: 'post',
    timeout: 2000,
    response: {
      code: 0,
      result: {
        name: '菲鸽',
      },
    },
  },
  {
    url: '/api/text',
    method: 'post',
    rawResponse: async (req, res) => {
      let reqbody = ''
      await new Promise((resolve) => {
        req.on('data', (chunk) => {
          reqbody += chunk
        })
        req.on('end', () => resolve(undefined))
      })
      res.setHeader('Content-Type', 'text/plain')
      res.statusCode = 200
      res.end(`hello, ${reqbody}`)
    },
  },
] as MockMethod[]
```

## 编写 service 文件

`src/services/mock.ts` 编写如下代码：

```ts
import { http } from '@/utils/http'
import type { IFooItem } from './foo.d'

export { IFooItem }

/** get 请求 */
export const getMockAPI = (name: string) => {
  return http<IFooItem>({
    url: `/api/get`,
    method: 'GET',
    query: { name },
  })
}
```

## 页面请求

```vue
<route lang="json5" type="page">
{
  layout: 'demo',
  style: {
    navigationBarTitleText: 'mock',
  },
}
</route>

<template>
  <view class="mt-6">
    <button @click="getFoo" class="my-4" type="primary">测试 GET 请求</button>
    <view class="text-xl">请求数据如下</view>
    <view class="text-green h-10">{{ JSON.stringify(data) }}</view>
    <view class="text-xl">完整数据</view>
    <view class="text-green h-20">{{ JSON.stringify(originalData) }}</view>
    <button class="my-8" type="warn" @click="reset">一键清空数据</button>
  </view>
</template>

<script lang="ts" setup>
import { getMockAPI } from '@/service/mock'

onLoad(() => {
  getFoo()
})

const originalData = ref<IResData<any>>()
const data = ref()

const getFoo = async () => {
  const res = await getMockAPI('菲鸽')
  data.value = res.result
  originalData.value = res
}

const reset = () => {
  data.value = undefined
  originalData.value = undefined
}
</script>
```

## 线上使用

`src/mockProdServer.ts` 编写如下内容：

::: details

```ts
import { createProdMockServer } from 'vite-plugin-mock/dist/client'

// TODO: check mock 文件位置
const modules = import.meta.glob('../mock/**/*.ts', { eager: true })

const mockModules: any[] = []
Object.keys(modules).forEach((key) => {
  if (key.includes('/_')) {
    return
  }
  mockModules.push(...(modules as Recordable)[key].default)
})

/**
 * Used in a production environment. Need to manually import all modules
 */
export function setupProdMockServer() {
  createProdMockServer(mockModules)
}
```

:::

然后在 `src/main.ts` 中引入即可。

```ts
// production mock server
if (process.env.NODE_ENV === 'production') {
  import('./mockProdServer').then(({ setupProdMockServer }) => {
    setupProdMockServer()
  })
}
```
