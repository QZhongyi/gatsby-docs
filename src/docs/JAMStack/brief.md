---
title: JAMstack
date: 2021-07-29T15:04:10.000Z
description: A Brief Introduction To JAMStack
---

## JAMstack - JavaScript, API, Markup
是一种使用静态网站生成器，不依赖 web server 的前端架构

![image](/images/jamstack.png)

### JAMstack 的特点
- SSG 网站生成器预渲染整个网站
- Headless CMS 管理动态内容
- HTTP API 增强网站功能
- 全站托管于 CDN 上
- 原子化发布
- 灵活的文件缓存策略
- 基于 Git 的自动构建部署

### JAMstack 的优势
- 高性能 - 因为是静态网页没有额外的网络数据请求
- 易部署 - 无需在线的 web server，仅需将生成的静态网页部署到 CDN
- 强安全 - 通过 Headless CMS 提供内容、网站生成器预渲染，无需在线服务，减少运维成本和安全风险
- SEO友好 - 预渲染静态页面有利于 SEO

### JAMstack 的劣势
- 只适用于大部分内容更新不频繁的网站（如新闻、电商、文档）
- 大型网站使用 SSG 生成静态页面时，构建的时间会很长

<br />

## SSG
### CSR - SSR - SSG
**CSR** 存在的问题：首屏加载、SEO、HTTP 数据请求带来的性能问题

**SSR** 解决了 SEO 的问题，大幅减少了首屏加载时间，HTTP 请求替换为 API 内部调用在一定程度上加快了数据获取步骤。但是带来了新问题，需要一个在线的服务渲染页面。该服务所消耗的资源相比于静态资源服务要大很多，且无法像静态资源一样部署在 CDN 上。
重新审视页面：以提供内容为主的网站的页面内容可分为两块：
1. 变化不频繁甚至不会变化的内容：文章、榜单、商品信息、推荐列表等
2. 变化比较频繁或个性化的内容：用户信息、登录状态、实时评论等
对于以第一种内容为主的网页，使用 SSR 实时渲染是不值得的，因为每次渲染出来的大部分内容都是一样的

对于这种情况，**SSG** 是一种更优的前端架构。它通过生成器将大部分页面内容静态化，将动态化的 web 应用渲染为多个静态页面。这样既能解决 SEO 的问题，也消除了服务端渲染带来的问题。而且将大部分内容静态化以后，结合 CDN 部署可以大大提高网站的性能。剩余少量的动态内容可通过 Severless 服务结合 CSR 实现，免去服务器运维的工作。

相关产品：Gatsby、NextJS、VitePress

<br />

## Headless CMS
相对于传统的 CMS，HCMS 将内容和格式分离，让 CMS 回归到内容管理的本质。发布的内容会以 JSON 格式通过 HTTP API 提供给客户端。通过 HCMS 进行内容管理更便于我们搭建一个 severless 的内容提供站点。

相关产品：Ghost、Netlify-CMS、wordpress API

<br />

#### 相关链接：  
[What is the Jamstack? | Jamstack](https://jamstack.org/what-is-jamstack/)  
[Jamstack，下一代Web建站技术栈？ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/281085404)  
[Gatsby JS和Netlify CMS：完美的一对！_编程故事的地方-CSDN博客](https://blog.csdn.net/dfsgwe1231/article/details/105993175)  
[前端架构之 JAMStack - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/137809668)  
[CSR vs SSR vs SSG - 简书 (jianshu.com)](https://www.jianshu.com/p/5f0e7f5e6acd)  
[新一代Web技术栈的演进：SSR/SSG/ISR/DPR都在做什么？ - 云+社区 - 腾讯云 (tencent.com)](https://cloud.tencent.com/developer/article/1819396)  