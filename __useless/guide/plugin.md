# 插件篇

|                插件名                | 作用                                                                                                                                                                                  |
| :----------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|      @dcloudio/vite-plugin-uni       | **最核心的 `uni 插件`**，没有它就不能在 vite 项目跑 uniapp，其他所有的 `uni插件` 都需要经通过它的手来编译，所以写法上，都是先写 UniXXX，再写 Uni，见下文                              |
|  @uni-helper/vite-plugin-uni-pages   | `uni 插件`，也是 `unibest 灵魂插件`，`route-block` 就是它的功劳，让你可以直接在本文件就能设置页面的路元信息，无需跑去 `pages.json` 配置，同时支持 `pages.config.ts` 编写 `pages.json` |
| @uni-helper/vite-plugin-uni-manifest | `uni 插件`，支持 `manifest.config.ts` 编写 `manifest.json`                                                                                                                            |
| @uni-helper/vite-plugin-uni-layouts  | `uni 插件`，支多种 `layouts` 布局，群友脑洞大开，充分利用这个特性实现其他项目不容实现的写法或效果                                                                                     |
|             unocss/vite              | `通用插件`，`Unocss 插件`                                                                                                                                                             |
|           vite-svg-loader            | `通用插件`，自动导入 `svg`                                                                                                                                                            |
|      unplugin-auto-import/vite       | `通用插件`，自动导入 API                                                                                                                                                              |
|       rollup-plugin-visualizer       | `通用插件`，build 后生成可视化打包图，方便优化包                                                                                                                                      |
|         vite-plugin-restart          | `通用插件`，vite 配置更改后自动重启服务                                                                                                                                               |
