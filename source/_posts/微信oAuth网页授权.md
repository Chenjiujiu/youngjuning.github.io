---
title: 微信 oAuth 网页授权流程
description: 本文讲述了如果用户在微信客户端中访问第三方网页，公众号可以通过微信网页授权机制，来获取用户基本信息，进而实现业务逻辑。
cover: https://cdn.jsdelivr.net/gh/youngjuning/images@main/1682564623975.png
date: 2023-04-27 11:02:56
categories:
  - [前端, 微信]
tags:
  - 微信
  - oAuth
  - 网页授权
  - 微信网页授权
  - 微信公众号
---

<ins class="adsbygoogle" style="display:block; text-align:center;"  data-ad-layout="in-article" data-ad-format="fluid" data-ad-client="ca-pub-7962287588031867" data-ad-slot="2542544532"></ins><script> (adsbygoogle = window.adsbygoogle || []).push({});</script>

如果用户在微信客户端中访问第三方网页，公众号可以通过微信网页授权机制，来获取用户基本信息，进而实现业务逻辑。

## 网页授权回调域名

1、在微信公众号请求用户网页授权之前，开发者需要先到公众平台官网中的 `开发` → `接口权限` → `网页服务` → `网页授权` - `网页授权获取用户基本信息` 的配置选项中，修改授权回调域名。请注意，这里填写的是域名（是一个字符串），而不是 URL，因此请勿加 `http://` 等协议头。

{% note info modern %}
注意：通过 `设置` → `公众号设置` → `功能设置` → `网页授权域名`
{% endnote %}

2、授权回调域名配置规范为全域名，比如需要网页授权的域名为：`www.qq.com`，配置以后此域名下面的页面 `http://www.qq.com/music.html`、`http://www.qq.com/login.html` 都可以进行 OAuth2.0 鉴权。但 `http://pay.qq.com`、`http://music.qq.com`、`http://qq.com` 无法进行 OAuth2.0 鉴权

3、如果公众号登录授权给了第三方开发者来进行管理，则不必做任何设置，由第三方代替公众号实现网页授权即可

## 业务域名

设置业务域名后，在微信内访问该域名下页面时，不会被重新排版。用户在该域名上进行输入时，不出现下图所示的安全提示。
注意事项：

1、可填写三个域名或路径（例：`wx.qq.com` 或 `wx.qq.com/mp`），需使用字母、数字及 `-` 的组合，不支持 IP 地址、端口号及短链域名。

2、填写的域名须通过ICP备案的验证。

3、将文件 `MP_verify_naGVGuiJ6KOsOwCA.txt`（点击下载）上传至填写域名或路径指向的 web 服务器（或虚拟主机）的目录（若填写域名，将文件放置在域名根目录下，例如 `wx.qq.com/MP_verify_naGVGuiJ6KOsOwCA.txt`；若填写路径，将文件放置在路径目录下，例如 `wx.qq.com/mp/MP_verify_naGVGuiJ6KOsOwCA.txt`），并确保可以访问。

4、一个自然月内最多可修改并保存三次，本月剩余保存次数：3
