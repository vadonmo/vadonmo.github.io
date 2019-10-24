---
title: antd pro部署后刷新404解决方案
date: 2019-10-24 08:35:24
toc: true
category: 前端
tags: 
 - antd
 - antd Pro
---
### 前言
最近在部署antdPro开发的前后端分离程序时，发现在本地正常，部署至服务器后刷新则出现404，原因在于antd Pro 支持两种路由模式，默认模式为 `browserHistory`，这种模式比较优雅，而对应的 `hash` 模式中间多了 `#` ，显得不那么好看。
<!-- more -->
```
https://cdn.com/users/123 # browserHistory
https://cdn.com/#/users/123 #hashHistory
```

<a name="snyti"></a>
### 修改方式
在 `config/config.js` 中修改下面的配置即可。

```javascript
export default {
	...
	history: 'hash',// 默认是 browser
}
```

<a name="wDdBW"></a>
### 解决方案
官网不包括 `Apache` 的解决方案，在这里做一下总结。主要是使其每次都访问 `index.html` 页面。
<a name="l2zJf"></a>
#### Nginx 部署
这里直接贴出来官方的配置，暂时没用 `nginx` 。<br />

```nginx
server {
    listen 80;
   	...
    location / {
        # 用于配合 browserHistory使用
        try_files $uri $uri/ /index.html;

        # 如果有资源，建议使用 https + http2，配合按需加载可以获得更好的体验
        # rewrite ^/(.*)$ https://preview.pro.ant.design/$1 permanent;
    }
}
```

<a name="jpCjZ"></a>
#### Apache 部署
与 `Nginx` 相同，配置如下：

```nginx
<Directory "C:\wwwroot\redbook.qiandaoba.cn">
		Options FollowSymLinks ExecCGI
		AllowOverride All
		Require all granted
		DirectoryIndex index.html
		# 用于配合 browserHistory使用	
		FallbackResource /index.html
	</Directory>
```

