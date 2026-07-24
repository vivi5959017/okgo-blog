---
title: Astro 入门指南
description: 这篇文章介绍如何使用 Astro 快速构建一个博客网站。
pubDate: 2024-06-21
tags: ["教程", "Astro"]
---

# Astro 快速入门指南 🚀

这篇文章将带你快速入门 Astro！

## 前置要求

在开始之前，你需要：

- **Node.js** 18 或更高版本
- **npm / yarn / pnpm** 任意包管理器
- **Git**（可选，但推荐）

## 第一步：创建项目

```bash
# 创建一个新的 Astro 项目
npm create astro@latest my-blog

# 进入项目目录
cd my-blog

# 安装依赖
npm install
```

## 第二步：本地开发

```bash
# 启动开发服务器
npm run dev
```

然后打开浏览器访问 **http://localhost:4321**

## 第三步：写文章

在 `src/content/blog/` 目录下创建 Markdown 文件，就像这篇文章一样！

## 第四步：构建和部署

```bash
# 构建生产版本
npm run build

# 预览构建结果
npm run preview
```

## 部署到 Vercel

1. 将代码上传到 GitHub
2. 登录 [Vercel](https://vercel.com)
3. 导入你的仓库
4. 等待部署完成

就这么简单！你的博客现在已经在线了！

## 总结

- ✅ 创建 Astro 项目
- ✅ 本地开发
- ✅ 写文章
- ✅ 部署上线

快去创建你自己的博客吧！
