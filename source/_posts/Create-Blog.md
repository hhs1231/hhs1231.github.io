---
title: hexo-matery版本
abbrlink: 56699
---

# hexo-matery版本

## 安装博客底层hexo

安装node.js和Git

```shell
node -v和npm -v检查是否安装好

npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```

## 下载hexo-theme-matery主题

```bash
git clone https://codeload.github.com/blinkfox/hexo-theme-matery/zip/master
```

将文件解压缩到hexo中的theme中

## 修改_config.yml

打开hexo根目录中的_config.yml

修改theme的值为hexo-theme-matery

url修改为网站的url

per_page分页数值建议修改为6的倍数

language修改为zh-CN

## 添加其他页面

### 分类categories页面

#### 新建

```shell
hexo new page "categories"
```

#### 页面内容设置

```yaml
---
title: categories
date: 2018-09-30 17:25:30
type: "categories"
layout: "categories"
---
```

### 标签tags页面

#### 新建

```shell
hexo new page "tages"
```

#### 页面内容设置

```yaml
---
title: tags
date: 2018-09-30 18:23:38
type: "tags"
layout: "tags"
---
```

### 关于我 about 页

#### 新建

```shell
hexo new page "about"
```

#### 页面内容设置

```yaml
---
title: about
date: 2018-09-30 17:25:30
type: "about"
layout: "about"
---
```

### 友情连接 friends 页（可选的）

#### 新建

```shell
hexo new page "friends"
```

#### 页面内容设置

```yaml
---
title: friends
date: 2018-12-12 21:25:30
type: "friends"
layout: "friends"
---
```

添加json文件

在source目录下新建_data目录，在 _data目录下新建friends.json，并填写类似内容

```json
[{
    "avatar": "http://image.luokangyuan.com/1_qq_27922023.jpg",
    "name": "码酱",
    "introduction": "我不是大佬，只是在追寻大佬的脚步",
    "url": "http://luokangyuan.com/",
    "title": "前去学习"
}, {
    "avatar": "http://image.luokangyuan.com/4027734.jpeg",
    "name": "闪烁之狐",
    "introduction": "编程界大佬，技术牛，人还特别好，不懂的都可以请教大佬",
    "url": "https://blinkfox.github.io/",
    "title": "前去学习"
}, {
    "avatar": "http://image.luokangyuan.com/avatar.jpg",
    "name": "ja_rome",
    "introduction": "平凡的脚步也可以走出伟大的行程",
    "url": "ttps://me.csdn.net/jlh912008548",
    "title": "前去学习"
}]
```

### 代码高亮

由于 Hexo 自带的代码高亮主题显示不好看，所以主题中使用到了 [hexo-prism-plugin](https://github.com/ele828/hexo-prism-plugin) 的 Hexo 插件来做代码高亮，安装命令如下：

```bash
npm i -S hexo-prism-plugin
```

然后，修改 Hexo 根目录下 `_config.yml` 文件中 `highlight.enable` 的值为 `false`，并新增 `prism` 插件相关的配置，主要配置如下：

```yaml
highlight:
  enable: false

prism_plugin:
  mode: 'preprocess'    # realtime/preprocess
  theme: 'tomorrow'
  line_number: false    # default false
  custom_css:
```

### 搜索

本主题中还使用到了 [hexo-generator-search](https://github.com/wzpan/hexo-generator-search) 的 Hexo 插件来做内容搜索，安装命令如下：

```shell
npm install hexo-generator-search --save
```

在 Hexo 根目录下的 `_config.yml` 文件中，新增以下的配置项：

```yaml
search:
  path: search.xml
  field: post
```

### 中文链接转拼音（可选的）

如果你的文章名称是中文的，那么 Hexo 默认生成的永久链接也会有中文，这样不利于 `SEO`，且 `gitment` 评论对中文链接也不支持。我们可以用 [hexo-permalink-pinyin](https://github.com/viko16/hexo-permalink-pinyin) Hexo 插件使在生成文章时生成中文拼音的永久链接。

安装命令如下：

```bash
npm i hexo-permalink-pinyin --save
```

在 Hexo 根目录下的 `_config.yml` 文件中，新增以下的配置项：

```yaml
permalink_pinyin:
  enable: true
  separator: '-' # default: '-'
```

### 文章字数统计插件（可选的）

如果你想要在文章中显示文章字数、阅读时长信息，可以安装 [hexo-wordcount](https://github.com/willin/hexo-wordcount)插件。

安装命令如下：

```bash
npm i --save hexo-wordcount
```

然后只需在本主题下的 `_config.yml` 文件中，激活以下配置项即可：

```yaml
wordCount:
  enable: false # 将这个值设置为 true 即可.
  postWordCount: true
  min2read: true
  totalCount: true
```

### 添加 RSS 订阅支持（可选的）

本主题中还使用到了 [hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed) 的 Hexo 插件来做 `RSS`，安装命令如下：

```bash
npm install hexo-generator-feed --save
```

在 Hexo 根目录下的 `_config.yml` 文件中，新增以下的配置项：

```yaml
feed:
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
  order_by: -date
```

执行 `hexo clean && hexo g` 重新生成博客文件，然后在 `public` 文件夹中即可看到 `atom.xml` 文件，说明你已经安装成功了。

### 修改页脚

页脚信息可能需要做定制化修改，而且它不便于做成配置信息，所以可能需要你自己去再修改和加工。修改的地方在主题文件的 `/layout/_partial/footer.ejs` 文件中，包括站点、使用的主题、访问量等。

### 修改社交链接

在主题的 `_config.yml` 文件中，默认支持 `QQ`、`GitHub` 和邮箱的配置，你可以在主题文件的 `/layout/_partial/social-link.ejs` 文件中，新增、修改你需要的社交链接地址，增加链接可参考如下代码：

```html
<a href="https://github.com/blinkfox" class="tooltipped" target="_blank" data-tooltip="访问我的GitHub" data-position="top" data-delay="50">
    <i class="fa fa-github"></i>
</a>
```

其中，社交图标（如：`fa-github`）你可以在 [Font Awesome](https://fontawesome.com/icons) 中搜索找到。以下是常用社交图标的标识，供你参考：

- Facebook: `fa-facebook`
- Twitter: `fa-twitter`
- Google-plus: `fa-google-plus`
- Linkedin: `fa-linkedin`
- Tumblr: `fa-tumblr`
- Medium: `fa-medium`
- Slack: `fa-slack`
- 新浪微博: `fa-weibo`
- 微信: `fa-wechat`
- QQ: `fa-qq`

> **注意**: 本主题中使用的 `Font Awesome` 版本为 `4.7.0`。

### 修改打赏的二维码图片

在主题文件的 `source/medias/reward` 文件中，你可以替换成你的的微信和支付宝的打赏二维码图片。

### 配置音乐播放器（可选的）

要支持音乐播放，就必须开启音乐的播放配置和音乐数据的文件。

首先，在你的博客 `source` 目录下的 `_data` 目录（没有的话就新建一个）中新建 `musics.json` 文件，文件内容如下所示：

```json
[{
	"name": "五月雨变奏电音",
	"artist": "AnimeVibe",
	"url": "http://xxx.com/music1.mp3",
	"cover": "http://xxx.com/music-cover1.png"
}, {
	"name": "Take me hand",
	"artist": "DAISHI DANCE,Cecile Corbel",
	"url": "/medias/music/music2.mp3",
	"cover": "/medias/music/cover2.png"
}, {
	"name": "Shape of You",
	"artist": "J.Fla",
	"url": "http://xxx.com/music3.mp3",
	"cover": "http://xxx.com/music-cover3.png"
}]
```

> **注**：以上 JSON 中的属性：`name`、`artist`、`url`、`cover` 分别表示音乐的名称、作者、音乐文件地址、音乐封面。

然后，在主题的 `_config.yml` 配置文件中激活配置即可：

```yaml
# 是否在首页显示音乐.
music:
  enable: true
  showTitle: false
  title: 听听音乐
  fixed: false # 是否开启吸底模式
  autoplay: false # 是否自动播放
  theme: '#42b983'
  loop: 'all' # 音频循环播放, 可选值: 'all', 'one', 'none'
  order: 'list' # 音频循环顺序, 可选值: 'list', 'random'
  preload: 'auto' # 预加载，可选值: 'none', 'metadata', 'auto'
  volume: 0.7 # 默认音量，请注意播放器会记忆用户设置，用户手动设置音量后默认音量即失效
  listFolded: false # 列表默认折叠
  listMaxHeight: # 列表最大高度
```

## 文章 Front-matter 介绍

### Front-matter 选项详解

`Front-matter` 选项中的所有内容均为**非必填**的。但我仍然建议至少填写 `title` 和 `date` 的值。

| 配置选项   | 默认值                         | 描述                                                         |
| :--------- | :----------------------------- | :----------------------------------------------------------- |
| title      | `Markdown` 的文件标题          | 文章标题，强烈建议填写此选项                                 |
| date       | 文件创建时的日期时间           | 发布时间，强烈建议填写此选项，且最好保证全局唯一             |
| author     | 根 `_config.yml` 中的 `author` | 文章作者                                                     |
| img        | `featureImages` 中的某个值     | 文章特征图，推荐使用图床(腾讯云、七牛云、又拍云等)来做图片的路径.如: `http://xxx.com/xxx.jpg` |
| top        | `true`                         | 推荐文章（文章是否置顶），如果 `top` 值为 `true`，则会作为首页推荐文章 |
| cover      | `false`                        | `v1.0.2`版本新增，表示该文章是否需要加入到首页轮播封面中     |
| coverImg   | 无                             | `v1.0.2`版本新增，表示该文章在首页轮播封面需要显示的图片路径，如果没有，则默认使用文章的特色图片 |
| password   | 无                             | 文章阅读密码，如果要对文章设置阅读验证密码的话，就可以设置 `password` 的值，该值必须是用 `SHA256` 加密后的密码，防止被他人识破。前提是在主题的 `config.yml` 中激活了 `verifyPassword` 选项 |
| toc        | `true`                         | 是否开启 TOC，可以针对某篇文章单独关闭 TOC 的功能。前提是在主题的 `config.yml` 中激活了 `toc` 选项 |
| mathjax    | `false`                        | 是否开启数学公式支持 ，本文章是否开启 `mathjax`，且需要在主题的 `_config.yml` 文件中也需要开启才行 |
| summary    | 无                             | 文章摘要，自定义的文章摘要内容，如果这个属性有值，文章卡片摘要就显示这段文字，否则程序会自动截取文章的部分内容作为摘要 |
| categories | 无                             | 文章分类，本主题的分类表示宏观上大的分类，只建议一篇文章一个分类 |
| tags       | 无                             | 文章标签，一篇文章可以多个标签                               |

> **注意**:
>
> 1. 如果 `img` 属性不填写的话，文章特色图会根据文章标题的 `hashcode` 的值取余，然后选取主题中对应的特色图片，从而达到让所有文章都的特色图**各有特色**。
> 2. `date` 的值尽量保证每篇文章是唯一的，因为本主题中 `Gitalk` 和 `Gitment` 识别 `id` 是通过 `date` 的值来作为唯一标识的。
> 3. 如果要对文章设置阅读验证密码的功能，不仅要在 Front-matter 中设置采用了 SHA256 加密的 password 的值，还需要在主题的 `_config.yml` 中激活了配置。有些在线的 SHA256 加密的地址，可供你使用：[开源中国在线工具](http://tool.oschina.net/encrypt?type=2)、[chahuo](http://encode.chahuo.com/)、[站长工具](http://tool.chinaz.com/tools/hash.aspx)。

以下为文章的 `Front-matter` 示例。

### 最简示例

```yaml
---
title: typora-vue-theme主题介绍
date: 2018-09-07 09:25:00
---
```

### 最全示例

```yaml
---
title: typora-vue-theme主题介绍
date: 2018-09-07 09:25:00
author: 赵奇
img: /source/images/xxx.jpg
top: true
cover: true
coverImg: /images/1.jpg
password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: false
mathjax: false
summary: 这是你自定义的文章摘要内容，如果这个属性有值，文章卡片摘要就显示这段文字，否则程序会自动截取文章的部分内容作为摘要
categories: Markdown
tags:
  - Typora
  - Markdown
---
```

## 效果截图



![首页](https://statics.sh1a.qingstor.com/2018/12/02/matery-20181202-1.png)

**首页**





![首页推荐文章](https://statics.sh1a.qingstor.com/2018/12/02/matery-20181202-2.png)

**首页推荐文章**





![首页文章列表](https://statics.sh1a.qingstor.com/2018/12/02/matery-20181202-3.png)

**首页文章列表**





![首页文章列表](https://statics.sh1a.qingstor.com/2018/12/02/matery-20181202-7.png)

**首页文章列表**





![首页文章列表](https://statics.sh1a.qingstor.com/2018/12/02/matery-20181202-8.png)

**首页文章列表**



## 自定制修改

在本主题的 `_config.yml` 中可以修改部分自定义信息，有以下几个部分：

- 菜单
- 我的梦想
- 首页的音乐播放器和视频播放器配置
- 是否显示推荐文章名称和按钮配置
- `favicon` 和 `Logo`
- 个人信息
- TOC 目录
- 文章打赏信息
- 复制文章内容时追加版权信息
- MathJax
- 文章字数统计、阅读时长
- 点击页面的’爱心’效果
- 我的项目
- 我的技能
- 我的相册
- `Gitalk`、`Gitment`、`Valine` 和 `disqus` 评论配置
- [不蒜子统计](http://busuanzi.ibruce.info/)和谷歌分析（`Google Analytics`）
- 默认特色图的集合。当文章没有设置特色图时，本主题会根据文章标题的 `hashcode` 值取余，来选择展示对应的特色图

**我认为个人博客应该都有自己的风格和特色**。如果本主题中的诸多功能和主题色彩你不满意，可以在主题中自定义修改，很多更自由的功能和细节点的修改难以在主题的 `_config.yml` 中完成，需要修改源代码才来完成。以下列出了可能对你有用的地方：

### 修改主题颜色

在主题文件的 `/source/css/matery.css` 文件中，搜索 `.bg-color` 来修改背景颜色：

```css
/* 整体背景颜色，包括导航、移动端的导航、页尾、标签页等的背景颜色. */
.bg-color {
    background-image: linear-gradient(to right, #4cbf30 0%, #0f9d58 100%);
}

@-webkit-keyframes rainbow {
   /* 动态切换背景颜色. */
}

@keyframes rainbow {
    /* 动态切换背景颜色. */
}
```

### 修改 banner 图和文章特色图

你可以直接在 `/source/medias/banner` 文件夹中更换你喜欢的 `banner` 图片，主题代码中是每天动态切换一张，只需 `7` 张即可。如果你会 `JavaScript` 代码，可以修改成你自己喜欢切换逻辑，如：随机切换等，`banner` 切换的代码位置在 `/layout/_partial/bg-cover-content.ejs` 文件的 `<script></script>` 代码中：

```javascript
$('.bg-cover').css('background-image', 'url(/medias/banner/' + new Date().getDay() + '.jpg)');
```

在 `/source/medias/featureimages` 文件夹中默认有 24 张特色图片，你可以再增加或者减少，并需要在 `_config.yml` 做同步修改。