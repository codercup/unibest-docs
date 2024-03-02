# 数据获取

你可以使用你喜欢的第三方请求库来获取数据。一般情况下，直接使用 `uni-app` 内置方法即可。

## `uni-app` 内置方法

`uni-app` 提供了 [uni.request](https://uniapp.dcloud.net.cn/api/request/request.html)、[uni.uploadFile](https://uniapp.dcloud.net.cn/api/request/network-file.html#uploadfile)、[uni.downloadFile](https://uniapp.dcloud.net.cn/api/request/network-file.html#downloadfile)、[WebSocket](https://uniapp.dcloud.net.cn/api/request/websocket.html) 等支持。一般情况下，你可以直接使用它们。

## request 请求封装+使用示例

::: code-group

```ts [src/utils/request.ts]
/* eslint-disable no-param-reassign */
import qs from 'qs'
import { useUserStore } from '@/store'
import { IResData, IUserInfo } from '@/typings'

type CustomRequestOptions = UniApp.RequestOptions & { query?: Record<string, any> }

// 请求基地址
const baseURL = import.meta.env.VITE_SERVER_BASEURL
// console.log(import.meta.env)

// 拦截器配置
const httpInterceptor = {
  // 拦截前触发
  invoke(options: CustomRequestOptions) {
    // 接口请求支持通过 query 参数配置 queryString
    if (options.query) {
      const queryStr = qs.stringify(options.query)
      if (options.url.includes('?')) {
        options.url += `&${queryStr}`
      } else {
        options.url += `?${queryStr}`
      }
    }

    // 1. 非 http 开头需拼接地址
    if (!options.url.startsWith('http')) {
      options.url = baseURL + options.url
    }
    // 2. 请求超时
    options.timeout = 10000 // 10s
    // 3. 添加小程序端请求头标识
    options.header = {
      platform: 'mp-weixin', // 可选值与 uniapp 定义的平台一致，告诉后台来源
      ...options.header,
    }
    // 4. 添加 token 请求头标识
    const userStore = useUserStore()
    const { token } = userStore.userInfo as unknown as IUserInfo
    if (token) {
      options.header.Authorization = `Bearer ${token}`
    }
  },
}

// 拦截 request 请求
uni.addInterceptor('request', httpInterceptor)
// 拦截 uploadFile 文件上传
uni.addInterceptor('uploadFile', httpInterceptor)

export const http = <T>(options: CustomRequestOptions) => {
  // 1. 返回 Promise 对象
  return new Promise<IResData<T>>((resolve, reject) => {
    uni.request({
      ...options,
      dataType: 'json',
      responseType: 'json',
      // 响应成功
      success(res) {
        // 状态码 2xx，参考 axios 的设计
        if (res.statusCode >= 200 && res.statusCode < 300) {
          // 2.1 提取核心数据 res.data
          resolve(res.data as IResData<T>)
        } else if (res.statusCode === 401) {
          // 401错误  -> 清理用户信息，跳转到登录页
          // userStore.clearUserInfo()
          // uni.navigateTo({ url: '/pages/login/login' })
          reject(res)
        } else {
          // 其他错误 -> 根据后端错误信息轻提示
          uni.showToast({
            icon: 'none',
            title: (res.data as IResData<T>).msg || '请求错误',
          })
          reject(res)
        }
      },
      // 响应失败
      fail(err) {
        uni.showToast({
          icon: 'none',
          title: '网络错误，换个网络试试',
        })
        reject(err)
      },
    })
  })
}

export default http
```

```ts [src/service/foot.ts]
import { http } from '@/utils/http'
import type { IFooItem } from './foo.d'

export { IFooItem }

/** get 请求 */
export const getFooAPI = (name: string) => {
  return http<IFooItem>({
    url: `/foo`,
    method: 'GET',
    query: { name },
  })
}

/** get 请求 */
export const postFooAPI = (name: string) => {
  return http<IFooItem>({
    url: `/foo`,
    method: 'POST',
    query: { name }, // post 请求也支持 query
    data: { name },
  })
}
```

```vue [src/demo.vue]
<script lang="ts" setup>
import { getFooAPI, postFooAPI, IFooItem } from '@/service/foo'
import { IResData } from '@/typings'

// 原始数据
const originalData = ref<IResData<IFooItem>>()
// 只包含真正的data数据
const data = ref<IFooItem>()
const getFoo = async () => {
  const res = await getFooAPI('菲鸽')
  data.value = res.result
  originalData.value = res
}

// 数据重置示例
const reset = () => {
  data.value = undefined
  originalData.value = undefined
}
</script>
```

:::

## request 使用示例截图

![Alt text](./screenshots/request.png)

<div style='opacity:0;'>
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
