# 请求转发

之前默认的后台地址只有一个，地址也是在 `.env` 里面进行配置的。但是如果后台地址有多个，那就不方便了。

多个后台地址时，通常有 `2` 个方案：

- 1. 编写多个 `http` 实例，每个实例传入不同的后台地址。
- 2. 使用代理，将请求转发到不同的后台地址。（推荐）

这里只介绍第二种方案。

## 本地代理

`vite.config.ts` 配置如下，其中转发的 `target` 可以改为通过 `.env` 获取。

```ts
 server: {
      proxy: {
        '/basic-api': {
          target: 'http://localhost:3000',
          changeOrigin: true,
          ws: true,
          rewrite: (path) => path.replace(new RegExp(`^/basic-api`), ''),
          // only https
          // secure: false
        },
        '/upload': {
          target: 'http://localhost:3300/upload',
          changeOrigin: true,
          ws: true,
          rewrite: (path) => path.replace(new RegExp(`^/upload`), ''),
        },
      },
      open: true, // 项目启动后，自动打开
      warmup: {
        clientFiles: ['./index.html', './src/{views,components}/*'],
      },
    },
```

## 线上代理

使用 `nginx` 配置代理即可。
