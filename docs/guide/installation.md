# 起步

## 前置依赖

- **Node.js** - `>=v18`
- **pnpm** - `>=7.30`（推荐使用 `8.15`）
- **文本编辑器** - 推荐使用 [VS Code](https://code.visualstudio.com/)
- **终端** - 为了运行 `uni` 命令，Windows 推荐 Git Bash，Linux 和 macOS 推荐 zsh

## 下载项目

通过 `pnpm create unibest <项目名>` 命令生成项目模版：

::: code-group

```bash [pnpm]
pnpm create unibest <项目名称> # 默认用 base 模板
pnpm create unibest <项目名称> -t <模板名> # 支持自定义模板

```

:::

支持 `-t` 参数选择模板，目前已有 3 个模板，分别是 `base`、`i18n`、`demo`。

```sh
pnpm create unibest my-unibest -t base # 基础模板
pnpm create unibest my-unibest -t i18n # 多语言模板
pnpm create unibest my-unibest -t demo # 所有demo的模板，包含了i18n
```

<!-- - 如果想学习所有的 `demo`，可以通过 `pnpm create unibest my-unibest-demo -t demo` 生成。(包含了所有的 `demo` 和 `i18n` 代码)
- 如果是新开发一个项目，建议使用 `base` 模板，可以通过 `pnpm create unibest my-unibest -t base` 生成。（不含 `demo` 代码）
- 如果项目有多语言需求，建议使用 `i18n` 模板，可以通过 `pnpm create unibest my-unibest -t i18n` 生成。（不含 `demo` 代码） -->

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
