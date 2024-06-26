### Cloudflare-Workers&Pages

## 前言

cf-pages这个js文件是[cmliu 大佬主页](https://github.com/cmliu)的一个开源项目 [CF-Workers-SUB](https://github.com/cmliu/CF-Workers-SUB) ，使得我们可以免费的在 Cloudflare 上面通过部署 Page ，来创建一个免费订阅！

cf-workers vless这个js文件是[MisakaNo 大佬主页](https://github.com/Misaka-blog)的一个开源项目 [ cf-wkrs-pages-vless](https://github.com/Misaka-blog/cf-wkrs-pages-vless) 之前的老版本的项目源码,可以在Cloudflare上面通过部署workers,来创建一个vless订阅！

现在如果复制粘贴直接部署在Cloudlfare workers打开网站会有 1101报错。但是看了cmliu大佬的油管视频，[点击观看视频](https://youtu.be/FE_gJrk2sSc?si=Vl0AtghlyoyIoNhI)

只要在代码最后vless://${userID}@${hostName}里vless中添加数字123就可以正常打开。（代码第749行）混淆字符串防止被Cloudflare杀死，vle<span style="color:red;">123</span>ss://${userID}@${hostName}

```
function getVLESSConfig(userID, hostName) {
const vlessLink = `vle123ss://${userID}@${hostName}:80?encryption=none&security=none&fp=randomized&type=ws&host=${hostName}&path=%2F%3Fed%3D2048#${hostName}`
const vlessTlsLink = `vle123ss://${userID}@${hostName}:443?encryption=none&security=tls&sni=${hostName}&fp=randomized&type=ws&host=${hostName}&path=%2F%3Fed%3D2048#${hostName}`
```
### 何为 Cloudflare Worker?

Cloudflare Worker 是 Cloudflare 提供的一种服务，它允许开发者在全球分布的边缘服务器上运行自定义的 JavaScript 代码。

Cloudflare Worker 可以用来处理 HTTP 请求，从而允许开发者通过编写 JavaScript 代码来实现各种功能，例如路由请求、修改请求和响应、执行身份验证、实现缓存策略等。

## 准备工作

1. 注册 Cloudflare 账号，[注册地址](https://dash.cloudflare.com/sign-up)

2. 购买注册域名一个

   可以在 Namesilo 进行购买，因为他的 WHOIS 隐私 是免费的，可以适当的进行一下隐私保护，而且域名还都挺便宜的。

   购买地址：[点击访问](https://www.namesilo.com/)

   也可以在Spaceship购买数字.xyz域名

   购买地址：[点击访问](https://www.spaceship.com/)

3. 托管域名到 Cloudflare
