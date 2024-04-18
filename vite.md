## 1、什么是vitepress

### `vitepress` 使用场景

简单的说 ，只要 **会用** `markdown` **语法**，就能构建自己的 **「****博客、笔记、使用文档****」**等系统 ；

### `vitepress` 优势

| 优势               | 介绍                                                         |
| ------------------ | ------------------------------------------------------------ |
| **傻瓜式操作**     | 只需要配置 菜单 和 对应的 `markdown` 就能实现博客、笔记等系统 自由 |
| **性能优势**       | 基于 vue3 和 vite 超快的启动速度，和更小的打包体积 **「**相比vue2 的 vuepress 更具有优势**」** |
| **写的少，做的多** | 专注于编写并以最少的配置进行部署，真正的 SSG + SPA 架构疯狂  |

## 2、安装和搭建 vitepress

### 安装

① 初始化一个文件夹

```
mkdir vitepress-project      // 创建文件夹
cd  vitepress-project        // 进入文件夹
npm init                     // 初始文件夹
```

② 安装 `vitepress` 和 相关依赖 `vue`

```
npm install -D vitepress vue
```

③ 在生成的 `package.json` 中，修改 `scripts` 脚本命令

```
"scripts": {
    "docs:dev":"vitepress dev docs",
    "docs:build":"vitepress build docs",
    "docs:serve":"vitepress serve docs"
  },
```

④ 运行 vitepress

```
npm run docs:dev
```

##### 配置 👇

###### ⑤ 启动后，将自动生成 `docs` 文件夹

![在这里插入图片描述](https://img-blog.csdnimg.cn/99b7867f1e754efd8f7a309c7618d41a.jpeg#)

###### ⑥ 创建和配置 主页文件

- 在 `docs` 文件夹下创建 index.md 文件 ：用于填充主页内容 👇
  `index.md` 参考 👇 ，（根据个人，自由修改）

```
---
  layout: home
  hero:
    image: 
      src: /logo.png
      alt: 前端吧
    name: 前端吧
    text: 关注web前端开发为主的博客网站和网址导航
    tagline: 收集有一大批前端相关的技术网站，包括Vue、React等技术资料的生态网站，方便快速访问。
    actions:
    - theme: brand
      text: 开始使用
      link: /guide/start
    - theme: alt
      text: 前端吧官网
      link: http://qianduan8.com/
  features:
  - title: UnoCSS
    details: Unocss是一种基于PurgeCSS的CSS框架,它可以帮助你更简洁、更高效地编写CSS。 Unocss的语法非常简单,它采用了类似于Tailwind CSS的类名方式。
    link: https://unocss.dev/
    linkText: 了解更多
  - title: Vue3
    details: 渐进式JavaScript框架.
    link: https://cn.vuejs.org/
    linkText: 了解更多
  - title: vitePress
    details: Vite & Vue Powered Static Site Generator.
    link: https://vitepress.dev/
  - title: Pinia
    details: 符合直觉的Vue.js 状态管理库.
    link: https://pinia.vuejs.org/zh/
  - title: Vuex
    details: 是一个专为 Vue.js 应用程序开发的状态管理模式.
    link: https://vuex.vuejs.org/zh/
  - title: Vue Router
    details: Vue.js 的官方路由,为 Vue.js 提供富有表现力、可配置的、方便的路由.
    link: https://router.vuejs.org/zh/
---
```

效果如下 👇

![img](https://img2023.cnblogs.com/blog/573390/202310/573390-20231013224422778-493809612.png)

###### ⑦创建页面 和 目录的配置

![在这里插入图片描述](https://img-blog.csdnimg.cn/1c9d80b0875b40539c8f2e3d81a409bd.jpeg#)

- 在 `docs` 下创建 `page` 文件夹 ：用于存放 每个 子文档
- （创建 2 个 `markdown` 文件，后面用于测试）
- 在`.vitepress`下创建 `config.js` 文件：用于配置目录 (路由) ， 参考如下👇 

```
module.exports = {
    title: '标题',
    base: '/home',
    description: 'Just playing around.',
    themeConfig: {
        nav: [
            {
                text: '导航',
                items: [
                    { text: '页面1', link: '/page/page1' },
                    { text: '页面2', link: '/page/page2' }
                ]
            }
        ],
        sidebar: {
            '/page/': [
                {
                    text: '关于侧边栏',
                    items: [
                        { text: '关于1', link: '/page/page1' },
                        { text: '关于2', link: '/page/page2' }
                    ]
                },
 
            ]
        }
    }
}

```

官方文档：https://vitejs.cn/vitepress/   https://vitepress.qzxdp.cn/