## Cloudflare-pages代理脚本:

### 基础部署视频教程：https://www.youtube.com/watch?v=LeT4jQUh8ok

### 快速部署视频教程：https://www.youtube.com/watch?v=Ea3wb5G08l4

### 进阶使用视角教程：https://www.youtube.com/watch?v=s91zjpw3-P8

------------------------------------------------------------------------
## CF vless代码一键部署后需要设置环境变量:

### 1、UUID须自定义。

### 3、伪装域名由变量PROXYDOMAIN设置，可自定义。

### 4、订阅地址：https://[YOUR-域名]/[YOUR-TOKEN]，即可获取订阅内容。

### 5、支持Base64、clash-meta、sing-box订阅格式, 内置订阅器由cmliu大佬提供维护支持。

</details>

### 变量说明
| 变量名(备注) | 参考示例 | 
|--------|---------|
| UUID（必填）| xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx |
| SOCKS5（选填）| user:password@127.0.0.1:1080 |
| TOKEN（必填，可自定义）| vless |
| PROXYDOMAIN（必填，可自定义）| www.bing.com |
| RPROXYIP（必填，需订阅器支持）| true |
| PROXYIP（选填，支持多ProxyIP使用,作间隔）| proxyip.fxxk.dedyn.io |
| SUB（必填，可自建）| vless-4ca.pages.dev |
| SUBAPI（必填，可自建）| apiurl.v1.mk |
| SUBCONFIG（必填，可自定义）| https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini |

------------------------------------------------------------------------
</details>

## Pages 部署方法
1. 部署 Cloudflare Pages：
   - 在 Github 上先 Fork 本项目，并点上 Star !!!
   - 在 Cloudflare Pages 控制台中选择 `连接到 Git`后，选中 `edgetunnel`项目后点击 `开始设置`。
   - 在 `设置构建和部署`页面下方，选择 `环境变量（高级）`后并 `添加变量`后点击 `保存并重新部署`即可。

2. 给 Pages绑定 CNAME自定义域：
   - 在 Pages控制台的 `自定义域`选项卡，下方点击 `设置自定义域`。
   - 填入你的自定义次级域名，注意不要使用你的根域名。例如： 您分配到的域名是 `fuck.cloudns.biz`，则添加自定义域填入 `lizi.fuck.cloudns.biz`即可
   - 按照 Cloudflare 的要求将返回你的域名DNS服务商，添加 该自定义域 `shili`的 CNAME记录 `edgetunnel.pages.dev` 后，点击 `激活域`即可。

3. 给 Pages设定 环境变量：
   - 在 Pages控制台的 `设置`选项卡，下方点击 `环境变量`。
   - 填入你的环境变量，注意使用大写，例如：UUID、SOCKS5（若有推荐优先）、RPROXYIP（需订阅器支持）、SUBAPI、SUBCONFIG

4. 使用自己的`优选域名`/`优选IP`的订阅内容(可选)：
   - 已通过提交虚假的节点配置给订阅服务，避免节点配置信息泄露。***[#6](https://github.com/cmliu/edgetunnel/pull/6) 感谢 [fatkun](https://github.com/fatkun)***
   - 当您使用 `let sub = 'sub.cmliussss.workers.dev';` 等非空参数时，您的worker节点配置将通过指定的订阅生成器创建完整的节点订阅信息。这种方式确实便捷，但同时意味着您的节点配置信息将被发送给订阅服务的提供者。
   - 如果你想使用自己的优选域名或者是自己的优选IP，可以参考 [WorkerVless2sub GitHub 仓库](https://github.com/cmliu/WorkerVless2sub) 中的部署说明自行搭建。
   - 在 Pages控制台的 `设置`选项卡，选择 `环境变量`> `制作`> `编辑变量`> `添加变量`；
   - 变量名设置为`SUB`，对应的值为你部署的订阅生成器地址。例如 `sub.cmliussss.workers.dev`，后点击 **保存**。
   - 之后在 Pages控制台的 `部署`选项卡，选择 `所有部署`> `最新部署最右的 ...`> `重试部署`，即可。
   - 注意，如果您使用了自己的订阅地址，要求订阅生成器的 `SUB`域名 和 `[YOUR-PAGES-URL]`的域名 不同属一个顶级域名，否则会出现异常。您可以在 `SUB` 变量赋值为 Pages.dev 分配到的域名。

5. 解决转换订阅的隐私问题(可选)：
   - 搭建反代订阅转换工具，通过随机化服务器地址和节点账号密码，解决用户转换订阅的隐私问题。
   - 可以参考[不良林psub项目](https://github.com/bulianglin/psub)自行搭建，视频原理以及教程 https://youtu.be/X7CC5jrgazo
   - 在 Pages控制台的 `设置`选项卡，选择 `环境变量`> `制作`> `编辑变量`> `添加变量`；
   - 变量名设置为`SUBAPI`，对应的值为你部署的订阅生成器地址。例如 `psub.cmliucdn.workers.dev`，后点击 **保存**。注意不要带https等协议信息和符号。
   - 之后在 Pages控制台的 `部署`选项卡，选择 `所有部署`> `最新部署最右的 ...`> `重试部署`，即可。
   - 注意，如果您使用了反代订阅转换工具，要求订阅转换工具的 `SUBAPI`域名 和 `[YOUR-PAGES-URL]`的域名 不同属一个顶级域名，否则会出现异常。您可以在 `SUBAPI` 变量赋值为 workers.dev 分配到的域名，注意不要带https等协议信息和符号。

------------------------------------------------------------------------
## 感谢：

### CF-vless代码作者[zizifn](https://github.com/zizifn/edgetunnel)。
### CF-vless代码作者[3Kmfi6HP](https://github.com/3Kmfi6HP/EDtunnel)。
### CF-vless订阅生成作者[cmliu](https://github.com/cmliu/WorkerVless2sub)。
### CF-vless订阅转换作者[bulianglin](https://github.com/bulianglin/psub)。
### CF优选IP程序作者[badafans](https://github.com/badafans/Cloudflare-IP-SpeedTest)、[XIU2](https://github.com/XIU2/CloudflareSpeedTest)。

------------------------------------------------------------------------
## 声明：

### 所有代码来源于Github社区与ChatGPT的整合；如您需要开源代码，请提Issues留下您的联系邮箱。

------------------------------------------------------------------------
