# 起步

你可以直接使用在线编辑器快速试用，或者使用终端在本地开始使用。

## 在线试用

您可以使用在线编辑器在浏览器中开始试用：

- [StackBlitz](https://stackblitz.com/github/codercup/unibest)
- [GitHub Template](https://github.com/codercup/unibest/generate)

## 本地使用

### 前置依赖

- **Node.js** - `>=v16.20`（推荐使用 `v18`）
- **文本编辑器** - 推荐使用 [VS Code](https://code.visualstudio.com/)
- **终端** - 为了运行 `uni` 命令，Windows 推荐 Git Bash，Linux 和 macOS 推荐 zsh

::: details 最佳实践

- **Node.js**: 总是使用偶数版本 (即 [LTS 版本](https://nodejs.org/en/about/previous-releases)，例如 18, 20)
  :::

打开终端，然后使用以下命令：

::: code-group

```bash [degit]
pnpx degit codercup/unibest my-unibest
```

```bash [create-unibest(comming soon)]
# 还在开发中...
pnpm create unibest my-unibest
```

:::

在 VS Code 中打开项目文件夹：

```bash
code <project-name>
```

安装依赖：

::: code-group

```bash [pnpm]
pnpm i
```

:::

## 开发

你可以使用 `dev` 命令直接启动 `h5` 模式的开发服务器

::: code-group

```bash [pnpm]
pnpm dev
```

:::

### 跨端开发

同样使用 `dev` 命令，不同的是你需要使用冒号并跟着你要开发的平台标识。

::: code-group

```bash [pnpm]
pnpm dev:<platform>
```

:::

> `pnpm dev` === `pnpm dev:h5`，即运行 `pnpm dev` 即可运行 `h5`。
