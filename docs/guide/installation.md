# 起步

## 前置依赖

- **Node.js** - `>=v18`
- **pnpm** - `>=7.30`（推荐使用 `8.15`）
- **文本编辑器** - 推荐使用 [VS Code](https://code.visualstudio.com/)
- **终端** - 为了运行 `uni` 命令，Windows 推荐 Git Bash，Linux 和 macOS 推荐 zsh

## 创建项目

通过下面的命令可以快速生成项目模版，`pnpm create unibest <项目名称>` ，如果不写 `<项目名称>` 会进入命令行交互模式。

```sh
pnpm create unibest my-project
```

支持 `-t` 参数选择模板，目前已有 `3` 个模板，分别是 `base`、`demo`、`i18n`。

```sh
pnpm create unibest my-project # 默认用 base 模板
pnpm create unibest my-project -t base # 基础模板
pnpm create unibest my-project -t demo # 所有demo的模板(包括i18n)
pnpm create unibest my-project -t i18n # 多语言模板
```

## 安装依赖

::: code-group

```bash [pnpm]
pnpm i
```

:::

## 运行

::: code-group

```bash [pnpm]
pnpm dev
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

`v3` 代码块 [传送门](./code-snippets)。
