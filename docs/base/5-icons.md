# 图标篇

本文主要介绍了 `图标` 的使用方式，通常有以下几种方式使用图标：

- `UI 库 Icons`
- `UnoCSS Icons`
- `iconfont`

下面笔者一一介绍

## UI 库 Icons

如果您已经引入了 `UI库`，并且正好该 `UI库` 已经有你想要的 `Icons`，那直接用最方便了，无需额外引入其他库，代码也是最少的。

这里介绍几个常用 `UI库` 的图标使用。

### `uni-ui Icons`

> 注意：`uni-ui Icons` 颜色只能通过 `color` 属性设置；使用 `UnoCSS` 设置无效。

```html
<uni-icons type="contact" size="30"></uni-icons>
<uni-icons type="contact" size="30" color="red"></uni-icons>
<uni-icons type="contact" size="30" class="text-green"></uni-icons>
<uni-icons type="contact" size="30" color="red" class="text-green"></uni-icons>
```

![](https://files.mdnice.com/user/23743/e51dfd4f-7232-41dd-8350-cc557116471f.png)

### `wot-ui Icons`

> 注意：`wot-ui icons` 颜色可以通过 `color` 属性设置，也可以通过 `UnoCSS` 设置；同时设置时，`color` 属性优先级高。

```html
<wd-icon name="add-circle"></wd-icon>
<wd-icon name="add-circle" color="red"></wd-icon>
<wd-icon name="add-circle" class="text-green"></wd-icon>
<wd-icon name="add-circle" class="text-green" color="red"></wd-icon>
```

![](https://files.mdnice.com/user/23743/b94eebd9-dfc3-409f-b605-d27f30484e4d.png)

### `uv-ui Icons`

> 注意：跟 `uni-ui Icons` 一样，`uv-ui Icons` 的颜色只能通过 `color` 属性设置；使用 `UnoCSS` 设置无效。

```html
<uv-icon name="home"></uv-icon>
<uv-icon name="home" color="red"></uv-icon>
<uv-icon name="home" class="text-green"></uv-icon>
<uv-icon name="home" color="red" class="text-green"></uv-icon>
```

![](https://files.mdnice.com/user/23743/78415f7b-9757-40e7-9655-963d6e068efe.png)

> 注意，经过检测这 `3个UI库Icons` 都不支持使用 `UnoCSS` 改变大小（优先级低被覆盖），必须使用 `size` 属性来设置大小才有效果（行内样式优先于 css 样式）。
>
> 另外，经过检测，都支持动态 `iconName`和动态 `color` ! 即下面这样的写法是生效的：

```ts
const iconName = ref<string>('contact')
const colorName = ref<string>('red')
onLoad(() => {
  setTimeout(() => {
    iconName.value = 'chat'
    colorName.value = 'green'
  }, 1000)
})
```

```html
<uni-icons :type="iconName" :color="colorName" class="text-green w-8"></uni-icons>
<!-- 其他2个UI库同样生效 -->
```

## `UnoCSS Icons`

`UnoCSS Icons` 可以方便接入 `iconfiy` 图标库，后者拥有 `10万+` 的海量图标，总能找到你想要的。

### 1. 安装 iconify

在使用 `iconify` 之前需要安装对应的图标库，安装格式如下：

`pnpm i -D @iconify-json/[the-collection-you-want]`

以安装 `carbon` 为例，执行 `pnpm i -D @iconify-json/carbon` 即可。

> `unibest` 已经装好了 `carbon` 图标库，可以直接使用。

### 2. 找到 iconify 想要的图标名

打开网址：<https://icones.js.org/>

- 在里面找到某个库，如 `carbon`。

![](https://files.mdnice.com/user/23743/08593566-332f-495b-bd22-73e686d43152.png)

- 搜索想要的图表，如 `avatar`，出现的搜索结果，查看类名，也可以点击图标，会出现详情（ `details` 里面）。

![](https://files.mdnice.com/user/23743/46cf38db-5f04-4fe8-9c1b-6bfc9b755888.png)

![](https://files.mdnice.com/user/23743/2a3fe893-8789-46e6-8b1e-c12cdf3e44e8.png)

- 如上图（ `details` 里面），拿到 `carbon:user-avatar`。

### 3. 编写代码

- 代码里面 `class` 填写 `i-carbon-user-avatar`（所有的单词用中划线连接即可）并且支持改颜色。

```html
<view class="i-carbon-user-avatar text-red" />
```

![](https://files.mdnice.com/user/23743/ade8146d-1b28-4ef2-b0c4-66d5c212975c.png)

> 如果图标没有预览效果，请安装 `VSCode` 插件 `antfu.iconify`。

预览效果：

![](https://files.mdnice.com/user/23743/7e30d7e1-39f8-4232-8edd-cc1a2bfb930c.png)

### 4. 动态图标名

昨天有网友反馈，`UnoCSS Icons` 无法使用动态类名，我来试试：（我先说结论：是支持的！）

```ts
const iconName = ref<string>('i-carbon-car')
onLoad(() => {
  setTimeout(() => {
    iconName.value = 'i-carbon-user-avatar'
  }, 1000)
})
```

```html
<view :class="iconName" />
```

一秒后会由 `i-carbon-car`（一辆车） 变成 `i-carbon-user-avatar`（一个头像），一切都是 OK 的。

## iconfont 图标库

`iconfont` 同样有海量免费的图标，同时支持上传自己的图标。公司项目通常会有自己的图标，由专业的 `UI设计师` 设计，这时通常会使用 `iconfont` 方式使用图标。

- 1. 打开`阿里巴巴矢量图标库 iconfont`，地址：https://www.iconfont.cn/，并登录。
- 2. 寻找需要的图标，加入项目，也可以上传自己的图标。

![](https://files.mdnice.com/user/23743/47d62886-83bf-4c8d-8f6d-2f5e52a57e3a.png)

![](https://files.mdnice.com/user/23743/f123a962-d542-4a7c-b366-7d5861918fd3.png)

![](https://files.mdnice.com/user/23743/0125727b-0562-43eb-88b7-f76337c2bf5e.png)

> 初次接触 `iconfont` 的同学，可能会找不到自己的项目，如下图：资源管理 -- 我的项目

![](https://files.mdnice.com/user/23743/9e556eb9-a0b9-4ce8-b30b-72cde6520d46.png)

- 3.图标方式选择，如下图有 `Unicode` `Font class` `Symbol` 三种方式，分别预览和使用如下：

![](https://files.mdnice.com/user/23743/db8e499a-24e3-4a82-928e-5c05ca7ff240.png)

![](https://files.mdnice.com/user/23743/f73445e5-7895-470e-bd68-cf7990efa911.png)

![](https://files.mdnice.com/user/23743/35344181-fdea-4600-938c-df9b65d263ec.png)

- `Unicode` 的方式太落后，语义化不明显，不推荐；
- `Symbol` 的方式太先进（背后原理是生成了 `SVG` 雪碧图），先进到 `小程序` 和 `APP` 都不支持，只能无奈放弃。

> `Symbol` 的方式生成 `svg` 雪碧图，如下所示：
>
> ![](https://files.mdnice.com/user/23743/e39b722f-352f-492e-8e83-de6fbfbd94e1.png)

- `Font class` 则是我们最合适的选择，有 `Symbol` 一样的语义化（都是`icon-xxx`方式），引入和使用也方便（ `Symbol` 是一个 `js` 文件，`Font class` 是一个 `css` 文件）。

- 3. 点击选中 `Font class` 后再点击 `查看在线连接` 按钮，可以拿到一个 `css` 的链接，如 [//at.alicdn.com/t/c/font_4032028_mbcuy517h6.css](//at.alicdn.com/t/c/font_4032028_mbcuy517h6.css) ，如果期间新加入了图标，记得点击更新链接，会重新生成一个链接，只有最后面一串 hash 有改变，并且旧的链接依然可以访问。

![](https://files.mdnice.com/user/23743/1dab9270-c4d5-4493-b0ad-1ccbccfda7aa.png)

我们使用的是 `Font class` 的方式，只需要这一个 `css` 链接就行，无需 `下载至本地`，想要本地预览的话才需要 `下载至本地`。

> `iconfont` 有默认的前缀 `icon-`，可以设置为其他的，如我的一个项目设置为 `bap-icon-`，以防跟其他的冲突。

![](https://files.mdnice.com/user/23743/38d49801-e636-48da-ade1-7b703fd222b4.png)

> 注意 `uniapp` 项目拿到 `css` 链接放到 `index.html` 是不对的，这样做只在 `h5` 中生效，`小程序` 和 `APP` 都不生效，正确的做法是放到代码里面显示引入。下面会讲：

- 4.在 `style/index.scss` 中写上上面的 `css` 链接里面的内容（`style/index.scss` 已经在 `main.ts` 引入了，`unibest` 模板已经内置），如下

```css
@font-face {
  font-family: iconfont; /* Project id 4032028 */
  src: url('//at.alicdn.com/t/c/font_4032028_mbcuy517h6.woff2?t=1713685013355') format('woff2'), url('//at.alicdn.com/t/c/font_4032028_mbcuy517h6.woff?t=1713685013355')
      format('woff'),
    url('//at.alicdn.com/t/c/font_4032028_mbcuy517h6.ttf?t=1713685013355') format('truetype');
}

.iconfont {
  font-family: iconfont !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.icon-facebook::before {
  content: '\e87d';
}

.icon-twitter::before {
  content: '\e646';
}

.icon-telegram::before {
  content: '\f245';
}
```

- 5. 编写代码，`<i class="iconfont icon-facebook"></i>`

![](https://files.mdnice.com/user/23743/eccab9f6-37c4-45c5-afeb-b6919a375f0e.png)

- 6. 预览，`h5 `端正常，APP 端不正常，小程序端看着正常，控制台也会报错，如下图：

![](https://files.mdnice.com/user/23743/4f9abe05-620c-4696-adf8-3ec166966621.png)

- 7. 这个怎么处理呢？转成 `base64` 是最快捷的，`iconfont` 本身就支持， `3`步搞定：

  - 7.1 如下图，勾选 `Base64`

![](https://files.mdnice.com/user/23743/4236ee49-d150-416a-b1d5-291feed82c2d.png)

    - 7.2 生成新链接，并得到新的 `css` 代码

![](https://files.mdnice.com/user/23743/bb00e709-ae67-4d42-8614-0d714d46d396.png)

    - 7.3 引入新代码，刷新界面，小程序不报错了，APP也正常了！

![](https://files.mdnice.com/user/23743/99c6e911-41b6-4a27-ac1a-62e208ddd464.png)

## 其它图标库

其他优秀的可以免费商用的图标库：

- 字节跳动的 `IconPark`，链接 [https://iconpark.oceanengine.com](https://iconpark.oceanengine.com/)。
- 不知道谁家的 `yesicon`，链接 [https://yesicon.app](https://yesicon.app/)。

## 总结

本文介绍了 `3` 种使用图标的方式，分别是 `UI 库 Icons`、`UnoCSS Icons`、`iconfont`。

- `UI 库 Icons` 颜色和大小属性都主要由 `UI 库` 本身控制，且都支持动态图标名和动态颜色。

- `UnoCSS Icons` 最省心，强烈推荐使用。

- `iconfont` 需要勾选 `Base64` 才能兼容多端。

全文完~
