# 起步

## 前置依赖

- **Node.js** - `>=v18`
- **pnpm** - `>=7.30`（推荐使用 `8.15`）
- **文本编辑器** - 推荐使用 [VS Code](https://code.visualstudio.com/)
- **终端** - 为了运行 `uni` 命令，Windows 推荐 Git Bash，Linux 和 macOS 推荐 zsh

## 下载项目

目前已经开发了 `create-unibest`，用户可以通过 `pnpm create unibest <项目名>` 命令生成项目模版：

::: code-group

```bash [pnpm]
# pnpm create unibest <项目名>
pnpm create unibest my-unibest
```

:::

目前还支持 `-t` 参数选择模板，命令如 `pnpm create unibest <项目名> -t <模板名>`，目前已经内置了 3 个模板，分别是 `base`、`i18n`、`demo`。

```sh
# pnpm create unibest <项目名> -t <模板名>
pnpm create unibest my-unibest -t base # 基础模板
pnpm create unibest my-unibest -t i18n # 多语言模板
pnpm create unibest my-unibest -t demo # 所有demo的模板，还包含了i18n
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
git commit -m "feat: init project"
```

:::

:::warning
切记！执行完 `pnpm dev` 之后，再开始第一次 `git commit`，否则报错！
:::

<div class='busuanzi_container'>
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
