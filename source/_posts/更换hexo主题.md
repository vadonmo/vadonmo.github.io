---
layout: post
title: 更换hexo主题
excerpt: 趁热打铁，写完上一篇，赶紧马不停蹄再来一篇，万一没激情就只不定哪天才能写了
date: 2019-01-23 14:30:01
toc: true
category: 爬坑记录
tags: 
 - hexo
 - 教程
---
## 前言
趁热打铁，写完上一篇，赶紧马不停蹄再来一篇，万一没激情就只不定哪天才能写了。

## 环境准备
<!--more-->
[在这](https://hexo.io/themes/)挑一款好看的主题，我选的是[这个](https://clovertuan.github.io/)，很简洁。

## 主题更换
其实每一个主题作者都写了步骤，按照步骤来准没错。
### 切换到hexo主题目录
```
cd themes
```
### 安装
```
 git clone https://github.com/esappear/hexo-theme-clover clover
```
## 以下为原作者教程，没啥可说的，每个人配置都不一样。

# Clover
## [Preview](https://clovertuan.github.io)
![preview](https://media.githubusercontent.com/avatars/8626321?orig=1&token=ANM6mziZ-bdE9fPaDWu1LVN0JQ-Vz-k_ks5b0I9FwA%3D%3D)

## Prerequisite
You got a blog project built by [Hexo](https://hexo.io). Your project directory should like this:
```
_config.yml  node_modules  package.json  public  scaffolds  source  themes
```
## Installation
- Clone the repository.
```
git clone https://github.com/esappear/hexo-theme-clover themes/clover
```
- Set theme in `_config.yml` file of the project root:
```
theme: clover
```
- Add `hexo-renderer-sass`
```
npm install hexo-renderer-sass --save
```
## Features
### Free home page.
You can set posts of specific categories or tags in home page.
```
home:
  # set card style of home page
  # card: project-card
  category: Projects
  tag:
    - js
    - css
  except_category: Something
  except_tag: 'someTag'
```
Post which belongs to `category` or `tag` and don't belongs to `except_category` or `except_tag` will be filtered.

### Page excerpt and photos
You can set an excerpt or photos in `Front-matter`.
```
---
layout: post
title: my_post_title
excerpt: my_post_excerpt
photos: [my_photo_url]
---
```
### Tags page.
- Create a page named tags
  ```
  hexo new page "tags"
  ```
- Edit tags page, set page layout to `tag`.
  ```
  ---
  layout: tag
  title: tags
  date: 2018-10-05 12:12:53
  ---
  ```
### Categories page.
- Create a page named categories
  ```
  hexo new page "categories"
  ```
- Edit categories page, set page layout to `category`.
  ```
  ---
  layout: category
  title: categories
  date: 2018-10-05 12:12:53
  ---
  ```
### About page.
- Create a page named about
  ```
  hexo new page "about"
  ```
- Edit categories page, set page layout to `about`.
  ```
  ---
  layout: about
  title: about
  date: 2018-10-05 12:12:53
  ---
  ```

### Social Media
```
social:
  GitHub: your-url
  Dribbble: your-url
  Behance: your-url
  Lofter: your-url
  Instagram: your-url
```

### Custom Menu
```
menu:
  Project: /
  Stuffs: /tags/Stuffs
  Archive: /archives
  About: /about
```

### Card Style
Two kinds of card style: `project-card` and `article-card`. (Never mind the name.)
```
card_style:
  home: project-card
  archive: article-card
  tag: article-card
  category: article-card
```