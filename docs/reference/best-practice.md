# 最佳实践

## 1.删除不用的 `ui` 库

如下图，`uni-ui` 和 `uv-ui` 分别占用了 `69kb` 和 `93kb`，如果没有用到可以删了，另外看业务需要使用哪一个。

![best-practice-1](./screenshots/best-practice-1.png)

## 2.不要随意在 `src/components` 里面写组件

因为 `src/components` 里面的组件会自动加载为全局组件，不是全局组件请不要随意写到这里，否则会增加 `vendor.js` 的体积。

![best-practice-2](./screenshots/best-practice-2.png)
