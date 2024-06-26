## Cloudflare-Workers&Pages

### 前言鸣谢

#### cf-workers vless这个[js文件](https://github.com/gudong1012/Cloudflare-workers-vless/blob/main/cf-workers%20vless%20.js)是[MisakaNo 大佬主页](https://github.com/Misaka-blog)的一个开源项目 [ cf-wkrs-pages-vless](https://github.com/Misaka-blog/cf-wkrs-pages-vless) 之前的老版本的项目源码,可以在Cloudflare上面通过部署workers,来创建一个vless节点！是我好几个月之前的看了MisakaNo的blog和油管视频去部署的Cloudflare worker vless节点。

#### 但是现在如果复制粘贴直接部署在Cloudlfare worker打开网站，会有 1101报错。电报频道里看到解决方案https://t.me/CMLiussss_channel/110，后来看了cmliu大佬的油管视频，[点击观看视频](https://youtu.be/FE_gJrk2sSc?si=Vl0AtghlyoyIoNhI)，知道怎么去解决这个问题了，还是很感谢cmliu大佬的，cm大佬喂饭，干货满满。

#### 只要在代码最后vless://${userID}@${hostName}里vless中添加数字123就可以正常打开。（代码第749行）通过混淆特殊的字符串防止被Cloudflare杀死，vle<span style="color:red;">123</span>ss://${userID}@${hostName}

#### cf-pages这个js文件是[cmliu 大佬主页](https://github.com/cmliu)的一个开源项目 [CF-Workers-SUB](https://github.com/cmliu/CF-Workers-SUB) ，使得我们可以免费的在 Cloudflare 上通过部署Page，来创建一个免费节点订阅！

```
function getVLESSConfig(userID, hostName) {
const vlessLink = `vle123ss://${userID}@${hostName}:80?encryption=none&security=none&fp=randomized&type=ws&host=${hostName}&path=%2F%3Fed%3D2048#${hostName}`
const vlessTlsLink = `vle123ss://${userID}@${hostName}:443?encryption=none&security=tls&sni=${hostName}&fp=randomized&type=ws&host=${hostName}&path=%2F%3Fed%3D2048#${hostName}`
```
### 何为 Cloudflare Workers?

Cloudflare Workers 是 Cloudflare 提供的一种服务，它允许开发者在全球分布的边缘服务器上运行自定义的 JavaScript 代码。

Cloudflare Workers 可以用来处理 HTTP 请求，从而允许开发者通过编写 JavaScript 代码来实现各种功能，例如路由请求、修改请求和响应、执行身份验证、实现缓存策略等。

### 准备工作

1. 注册 Cloudflare 账号，[注册地址](https://dash.cloudflare.com/sign-up)

2. 购买注册域名一个

   可以在 Namesilo 进行购买，因为他的 WHOIS 隐私 是免费的，可以适当的进行一下隐私保护，而且域名还都挺便宜的。

   购买地址：[点击访问](https://www.namesilo.com/)

   也可以在Spaceship购买数字.xyz域名

   购买地址：[点击访问](https://www.spaceship.com/)

3. 托管域名到 Cloudflare
