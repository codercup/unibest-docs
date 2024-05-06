# hbx 模板

为了方便使用 `HBuilderX` 的开发者，`unibest` 也提供 `hbx` 模板。

`hbx 模板` 适用于 `2 类用户`

- 使用 `uniCloud` 云开发的用户，必须使用 `hbx 版本`，因为 `uniCloud` 跟 `HBuilderX` 是绑定的。
- 开发 `App` 的用户，可选使用 `hbx 版本`。

## 仓库地址

- gitee: [https://gitee.com/codercup/unibest-hbx.git](https://gitee.com/codercup/unibest-hbx.git)
- github: [https://github.com/codercup/unibest-hbx.git](https://github.com/codercup/unibest-hbx.git)

没有梯子的用户优先推荐使用 `gitee` 仓库，速度更快。（两个仓库会实时同步，无差别。）

## 导入项目

有 2 种方式导入项目：

- 从 `Git` 导入...
- 从本地目录导入...

## 运行项目

此时运行菜单会提示 `本项目类型无法运行`，如下图

![](https://files.mdnice.com/user/23743/f404c38a-8c9e-4f58-ae23-cae39a06513c.png)

![](https://files.mdnice.com/user/23743/90a4465f-6a56-4f72-92c3-79d74961b7ae.png)

需要执行如下 2 步：

- 项目下执行 `pnpm i`
- 右键项目，选择 `重新识别项目类型`

![](https://files.mdnice.com/user/23743/161268af-253a-45d4-b562-c7180a53cf3c.png)

## 运行效果

经过上面的操作后，就可以正常运行了。

- ios 模拟器运行效果如下：

![](https://files.mdnice.com/user/23743/deda7b82-1c3d-4837-8c70-37051e56a621.png)

![](https://files.mdnice.com/user/23743/ae70460e-4ae2-49b4-922b-d5d58d4976fe.png)

![](https://files.mdnice.com/user/23743/ce1148b8-2167-4135-94a5-2bf32d14af18.png)

- 微信小程序运行效果如下：

![](https://files.mdnice.com/user/23743/b9c2c20f-af3f-4133-a77d-f05ea4d84bf5.png)

> 目前微信小程序静态资源还有点问题，如下图 `logo 不见了`，后续会修复。

![](https://files.mdnice.com/user/23743/4a971ae9-f453-419f-8bba-4a69ed3c1ebf.png)

> 另外还发现 `UnoCSS Icon` 不生效，原因未知。

## 总结

本文描述了 `hbx` 模板的由来，使用方式。

有需要的可以试试，但是不太建议使用。另外精力有限，该模板不再维护。

全文完~
