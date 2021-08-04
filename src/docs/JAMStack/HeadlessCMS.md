---
status: private
title: Headless CMS
date: 2021-08-04T06:59:37.306Z
description: Intro to HCMS and how to use Netlify-CMS in your static site
---
## Headless CMS
传统 CMS（wordpress、Sitecore）会将文本内容、图片、HTML、CSS 等资源混杂在一起管理，这样生成的掺杂着代码的内容很难去复用在不同平台上。为了迎合越来越多的跨平台、高度个性化的建站需求，Headless CMS 诞生了  
无头 CMS 相对于传统 CMS 的不同在于 HCMS 更纯粹地专注于内容管理，把内容（body）和展示层（head）解耦了，并通过 API 来提供内容给各个端
<br />
## Netlify CMS
基于 React 的开源的内容管理系统，跟很多静态网站生成器都能适配。使用 Git 仓库管理资源，保存文件后自动提交到 Git 仓库（GitHub、Gitlab、Bitbucket）
<br />
### Netlify CMS 搭配 Gatsby
为 Gatsby 站点增加 Netlify CMS 的操作分为三个步骤：
1. 安装插件 netlify-cms-app 和 gatsby-plugin-netlify-cms
2. 在 Gatsby 配置文件 gatsby-config.js 的 plugins 中增加‘gatsby-plugin-netlify-cms’
3. 在 Gatsby 工程目录的 static/admin 下增加 Netlify CMS 配置文件 config.yml
```
# config.yml
backend:
  name: git-gateway # backend protocol
  branch: develop # publication git branch

media_folder: static/image # upload images folder path (relative to the project root)
public_folder: /image # upload images public path

collections: # content structure
  - name: "jamstack" # used in routes
    label: "JAMStack" # used in the UI
    folder: "src/docs/JAMStack" # content folder
    create: true # allow user to create new documents
    slug: "{{year}}-{{month}}-{{day}}-{{slug}}" # file name template
    fields: # fields in the content editor
      - {label: "Template Key", name: "templateKey", widget: "hidden", default: "blog-post"}
      - {label: "Status", name: "status", widget: "string"}
      - {label: "Title", name: "title", widget: "string"}
      - {label: "Publish Date", name: "date", widget: "datetime"}
      - {label: "Description", name: "description", widget: "text"}
      - {label: "Body", name: "body", widget: "markdown"}
```

#### 相关连接
[Headless CMS explained in 1 minute | Contentful](https://www.contentful.com/r/knowledgebase/what-is-headless-cms/)  
[Overview | Netlify CMS | Open-Source Content Management System](https://www.netlifycms.org/docs/intro/)  
[gatsby-plugin-netlify-cms | GatsbyJS 中文网](https://www.gatsbyjs.cn/packages/gatsby-plugin-netlify-cms/?=netlify)  
[Add to Your Site | Netlify CMS | Open-Source Content Management System](https://www.netlifycms.org/docs/add-to-your-site/#app-file-structure)
