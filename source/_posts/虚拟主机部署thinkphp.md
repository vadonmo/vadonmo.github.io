---
title: 虚拟主机部署thinkphp
toc: true
date: 2019-01-24 18:58:30
category: thinkphp
tags:
- 教程
- thinkphp
---
## 前言
前两天部分服务需要迁移到虚拟主机，php就这点好，环境依赖太低。随便给个地都能跑起来。之前就不部署了一个，觉得再部署个也是分分钟的事。。然而被事实狠狠的打了脸。还是自己太年轻。
<!-- more -->
## 环境准备
### ftp文件管理器
我是用的[filezilla](https://filezilla-project.org/)，习惯了。用其他的也一样，不是重点。
### 虚拟主机一份
各大服务商都行，随便来个。这个是公司提供的，服务商就不说了。
### thinkphp项目一份
项目基于thinphp5， 其他版本应该也差不多。
## 部署步骤
1.   讲代码通过ftp文件管理器上传至虚拟主机 `/htdocs` 目录中，其他虚拟主机请参照说明，比如 `www` 等
2.   将 `public` 中 `index.php`、`.htaccess` 移到根目录，入口变了，最好在其他目录下添加 `.htaccess` 文件，内容为 `deny from all` 避免被直接访问。
3.   修改 `index.php`, 入口遍了相应的路径也要改变下。
```
define('APP_PATH', __DIR__ . '/application/');
// 加载框架引导文件
require __DIR__ . '/thinkphp/start.php';
```
4.  修改 `.htaccess`，此处有坑。。
```
<IfModule mod_rewrite.c>
  # Options +FollowSymlinks -Multiviews
  RewriteEngine On

  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteRule ^(.*)$ index.php/$1 [QSA,PT,L]
</IfModule>
```

## 其他问题
### 500内部服务器错误
1. 入口文件未找到。（我入口正常，nginx没问题）
2. apache里重写未开启。 （我本地开启了，虚拟主机不知道，应该都是开启的，客服说没问题）
3. hataccess文件出错。（就错在这一步）

按照上面步骤部署完后，打开一脸懵逼，居然报500错误。。一定是服务提供商环境没开全，怒怼客服，客服说我 `.htaccess`文件写错了，可我本地明明好好的，然后客服把我第4步第二行给注释掉了，就好了。。原因如下：

<blockquote>
[In some (or all?) server configurations, mod_rewrite requires followsymlinks to be enabled, or it will crater with a 500-Server Error.]

在某些服务器配置中，mod_rewrite要求有followsymlinks，否则会显示500内部服务器错误。

If your mod_rewrite code works without the options +followsymlinks directive, that means that your server configuration file has enabled them already, and you won't need that directive in your .htaccess files.

The requirement for enabling followsymlinks is not well-defined. The only way I learned about it was because I got a 500-Server Error the first time I ever enabled mod_rewrite, and the error log entry said something to the effect of, "You must enable SymLinks for this to work."

在任何情况下，只要您没有指定FollowSymLinks的选项（即Options FollowSymLinks），或者指定了SymLinksIfOwnerMatch选项，Apache将不得不调用额外的系统函数来检查符号链接。每次针对文件名的请求都将触发一次检查。

如果你没有使用followsymlinks规则而网站访问正常，说明你的服务器配置已经默认调用followsymlinks的重写规则，你无需再为你的htaccess文件定义了。但在有些服务器500 Server Error之后的错误日志中提示需要定义SymLinks使得rewrite重写规则起作用。

</blockquote>

## 结语
到处都是坑，不学就掉坑。