# 快速开始

- 前置依赖

  - **Node.js** - `>=v18`
  - **pnpm** - `>=7.30`（推荐使用 `8.12+`）
  - **文本编辑器** - 推荐使用 `VSCode`，可选 `WebStrom`
  - **辅助运行工具** - `HBuilderX`，运行 `APP` 还是离不开 `HBuilderX`

## 创建项目

通过下面的命令可以快速生成项目模板，`pnpm create unibest <项目名称>` ，如果不写 `<项目名称>` 会进入命令行交互模式。

```bash
pnpm create unibest my-project
```

如果使用 `npm`，可能有缓存，需要加上 `@latest` 标识，如果创建失败，请使用 `pnpm` 安装。

```bash
npm create unibest my-project
# 如果提示报错，或者生成的项目版本太旧，请使用下面的命令，增加 @latest 标识
npm create unibest@latest my-project
```

实际操作截图如下：

![create project](./assets/2-1.png)

> 强烈推荐是用 `pnpm`，性能更好，速度更快，节省磁盘空间。
>
> 如果没有 `pnpm` 可以通过 `npm i -g pnpm` 安装。

![unibest templates](./assets/2-2.png)

`create unibest` 支持 `-t` 参数选择模板，目前已有两大类 `8` 个模板

- `普通` 模板( `6个` ）：分别是 `base`、`demo`、`ucharts`、`tabbar`、`i18n`、`js`
- `hbx` 模板( `2个` ）：分别是 `hbx-base`、`hbx-demo`。

> 不带 `-t` 参数时会默认生成 `base` 模板。
>
> `base` 模板是最基本的模板，更新最及时，推荐使用 `base` 模板创建新项目。其他几个模板也是基于 `base` 模板得到的。 `demo` 模板则作为参考用。
>
> `js` 模板不推荐使用，可以使用 `base` 模板替代，里面已经做了兼容配置，可以直接编写 `js`，原本的 `ts` 文件还能提供部分类型，何乐而不为？

```sh
# VS Code 模板
pnpm create unibest my-project # 默认用 base 模板
pnpm create unibest my-project -t base # 基础模板
pnpm create unibest my-project -t demo # 所有demo的模板(包括i18n)
pnpm create unibest my-project -t ucharts # 秋云图表模板
pnpm create unibest my-project -t tabbar # 自定义 tabbar 模板
pnpm create unibest my-project -t i18n # 多语言模板
pnpm create unibest my-project -t js # js 模板

# HBuilderX 模板，方便使用 uniCloud 云开发 (未来可以对接 uni-app x)
pnpm create unibest my-project -t hbx-base # hbx的base模板
pnpm create unibest my-project -t hbx-demo # hbx的demo模板，包含所有的demo
```

> 至于 `uni-app x 模板`，紧盯 `uni-app` 官方动向，等官方出来脚手架，`unibest` 将第一时间推出该模板。

## 安装、运行

```bash [pnpm]
pnpm i
pnpm dev
# dev默认运行的是h5，其他平台执行dev:<uni-platform>，如:
pnpm dev:mp-weixin
```

`pnpm dev` 之后在浏览器打开 `http://localhost:9000/`。

> 其他平台构建和发布，查看第十一章节：《十一、运行发布篇》。

## 第一次 `commit`

```bash
git add .
git commit -m "feat: init project"
```

## `v3` 代码块

在 `vue` 文件中，输入 `v3` 按 `tab` 即可快速生成页面模板，可以大大加快页面生成。

> 原理：基于 `VSCode` 代码块生成。

![alt text](./assets/2-3.gif)

## 注意事项

- 若代码里面自动引入的 `API` 报错，只需要 `pnpm dev` 即可。
- 若代码运行后，`H5端` 浏览器界面底部没有 `tabbar`， 刷新浏览器或者再次 `pnpm dev` 即可。
