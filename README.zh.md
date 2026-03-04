# NoSignal

*[English](README.md) | [中文](README.zh.md)*

一个基于 [Astro](https://astro.build) 构建的个人博客，使用 [Keystatic](https://keystatic.com) 作为内容管理系统。

## 特性

- **Astro** - 性能出色的静态站点生成器
- **Keystatic** - 基于 Git 的内容管理系统
- **Markdoc** - 支持自定义组件的内容格式
- **Tailwind CSS** - 实用优先的 CSS 框架
- **Vercel** - 部署平台
- **Pagefind** - 静态搜索功能

## 快速开始

### 前置要求

- Node.js 18+
- npm

### 安装

```bash
# 克隆仓库
git clone https://github.com/OtavioLeonardo/NoSignal-Blog.git
cd NoSignal-Blog

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

### 构建生产版本

```bash
npm run build
```

### 部署

本项目已配置为在 [Vercel](https://vercel.com) 上部署。只需将更改推送到 GitHub，Vercel 会自动部署。

## 网站配置

### 基础设置

编辑 `src/utils/AppConfig.ts`：

```typescript
export const AppConfig = {
    site_name: 'NoSignal',
    title: 'NoSignal | Just Write',
    description: '你的网站描述',
    author: '你的名字',
    locale_region: 'zh-CN',
    locale: 'zh'
};
```

### SEO 与社交

- 网站 URL：编辑 `astro.config.mjs` 中的 `site` 字段
- 网站图标：替换 `public/favicon.svg`
- 社交图片：编辑 `public/showcase.jpg` 和 `public/showcase.png`

### 导航

编辑 `src/components/Navbar.astro` 来修改导航链接。

## 内容管理

### 使用 Keystatic 管理面板

运行开发服务器，然后访问：
```
http://localhost:4321/keystatic
```

#### 文章集合

在 `src/content/posts/*.mdoc` 创建新博客文章

**前置参数说明：**

| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `title` | string | 是 | 文章标题 |
| `series` | string | 否 | 系列名称（关联相关文章） |
| `layout` | string | 是 | 固定值：`../../layouts/post.astro` |
| `pubDate` | date | 是 | 发布日期（YYYY-MM-DD） |
| `description` | string | 否 | SEO 描述 |
| `excerpt` | string | 否 | 文章摘要（用于列表显示） |
| `author` | string | 是 | 作者名称 |
| `isPinned` | boolean | 否 | 置顶文章 |
| `image` | object | 否 | 封面图片 |
| `tags` | array | 否 | 标签（用于分类） |
| `updates` | array | 否 | 更新历史 |

**示例：**

```yaml
---
title: 我的第一篇文章
series: 教程
layout: ../../layouts/post.astro
pubDate: 2026-03-04
description: 简短描述
excerpt: >-
  这是更长的摘要，会显示在文章列表中。
author: 你的名字
isPinned: false
image: {}
tags:
  - 教程
  - 示例
updates:
  - date: 2026-03-04
    title: 初始版本
    content: 首次发布
---
```

#### 日记集合

快速记录和每日笔记，放在 `src/content/diary/*.mdoc`

**前置参数说明：**

| 字段 | 类型 | 必填 |
|------|------|------|
| `title` | string | 是 |
| `pubDate` | date | 是 |
| `description` | string | 否 |

#### Now 页面

Now 页面展示你当前正在进行的事情。编辑 `src/content/pages/now.mdoc`

**参数说明：**

- `title`: 固定为 "Now"
- `updatedDate`: 最后更新日期
- `content`: Markdown 内容

### 手动创建内容

你也可以直接在编辑器中创建内容文件：

```
src/content/posts/my-post.mdoc
src/content/diary/2026-03-04.mdoc
```

### 自定义组件

此博客支持自定义 Markdoc 组件：

#### 提示块

```markdoc
{% aside type="tip" title="有用的提示" %}
这里是你的内容
{% /aside %}
```

类型可选：`tip`、`note`、`danger`、`caution`

## 开发

### 项目结构

```
no-signal/
├── src/
│   ├── content/
│   │   ├── posts/      # 博客文章
│   │   ├── diary/      # 每日笔记
│   │   └── pages/      # 静态页面（now）
│   ├── components/     # Astro 组件
│   ├── layouts/       # 页面布局
│   ├── pages/          # 路由页面
│   ├── styles/         # 全局样式
│   └── utils/          # 工具函数和配置
├── public/             # 静态资源
├── keystatic.config.tsx # CMS 配置
└── astro.config.mjs     # Astro 配置
```

### 添加新标签

1. 在文章编辑器中创建新标签
2. 标签会自动出现在标签索引页面

### 搜索

网站使用 Pagefind 进行静态搜索。搜索索引在构建过程中生成。

## 常见问题

### Keystatic 无法加载

确保你正在运行开发服务器：
```bash
npm run dev
```

### 构建错误

清除缓存：
```bash
rm -rf node_modules/.astro
```

### 内容不显示

- 检查前置参数格式
- 确保文件在正确的目录
- 验证 `layout` 路径是否正确

## 许可证

MIT

## 致谢

基于 [Astro](https://astro.build)、[Keystatic](https://keystatic.com) 和 [Tailwind CSS](https://tailwindcss.com) 构建。
