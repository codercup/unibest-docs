# 快速开始

## 前置依赖

- **Node.js** - `>=v18`
- **pnpm** - `>=7.30`（推荐使用 `8.15`）
- **文本编辑器** - 推荐使用 [VS Code](https://code.visualstudio.com/)
- **终端** - 为了运行 `uni` 命令，Windows 推荐 Git Bash，Linux 和 macOS 推荐 zsh

## 模板介绍

![](https://oss.laf.run/ukw0y1-site/unibest-templates-xmind.jpg)

## 创建项目

通过下面的命令可以快速生成项目模版，`pnpm create unibest <项目名称>` ，如果不写 `<项目名称>` 会进入命令行交互模式。

::: code-group

```bash [pnpm]
pnpm create unibest my-project
```

```bash [npm]
npm create unibest my-project
# 如果提示报错，请使用下面的命令
npm create unibest@latest my-project
```

:::

::: tip
强烈推荐是用 `pnpm`，性能更好，速度更快。

如果使用 `npm` 建议添加上标记名（@latest），否则 `npm` 可能会解析到缓存的过时软件包版本。
:::

`create unibest` 支持 `-t` 参数选择模板，目前已有两大类 `8` 个模板

- `普通` 模板( `6个` ）：分别是 `base`、`demo`、`ucharts`、`tabbar`、`i18n`、`js`
- `hbx` 模板( `2个` ）：分别是 `hbx-base`、`hbx-demo`。

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

> `uni-app x 模板` 还在开发中，4 月份会面世。 （update on 2024-04-05)

## 安装依赖

::: code-group

```bash [pnpm]
pnpm i
```

```bash [npm]
# npm i 会报错
npm i -g pnpm
pnpm i
```

:::

## 运行

::: code-group

```bash [pnpm]
pnpm dev
```

```bash [npm]
npm run dev
```

:::

`pnpm dev` 之后在浏览器打开 `http://localhost:9000/`。

## 第一次 `commit`

::: code-group

```bash
git add .
git commit -m "feat: init project"
```

:::

## `v3` 代码块

在 `vue` 文件中，输入 `v3` 按 `tab` 即可快速生成页面模板，可以大大加快页面生成。

## 相关链接

跨端开发专题请前往 [跨端开发](./run-build)

App 打包专题请前往 [App 打包](./app-build)
