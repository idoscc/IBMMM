提示：

1：用的人增多，肯定会步达拉斯的后尘，用起来别太狠，建议轻度用户使用

2：脚本默认情况下：仅支持IBM伦敦仅支持IBM伦敦仅支持IBM伦敦 ，每天自动更新V2ray并重启

详细教程视频（YouTube）：https://youtu.be/2WGJbtsY6gw

   | Secrets变量 | 形式 |
  | --------------------- | ----------- |
  | `IBM_CF_USERNAME`       | IBM Cloud 邮箱地址 |
  | `IBM_CF_PASSWORD` | IBM Cloud 邮箱密码 |
  | `IBM_CF_APP_NAME` | IBM Cloud 应用程序名 |
  | `V2_UUID` | 自定义UUID码 |
  | `V2_WS_PATH_VMESS` </br> `V2_WS_PATH_VLESS` | 协议选择一个，填入自定义PATH路径 |
  
注：VMESS默认的alterId为64

本项目基于P3TERX项目修改而来，感谢P3TERX

配置 Cloudflare 高速节点中转
这部分不配置也可以直接连 应用程序域名 使用, 就是有点慢.

注册并登录https://www.cloudflare.com/
点击 Workers
点击 创建Worker
在脚本位置加入下面这段, url.hostname修改为对应的 应用程序域名.
addEventListener(
  "fetch",event => {
    let url=new URL(event.request.url);
    url.hostname="ibmyes.us-south.cf.appdomain.cloud";
    let request=new Request(url,event.request);
    event.respondWith(
      fetch(request)
    )
  }
)
点击保存并部署, 这里会给一个网址(比如cloudflare_workers.dev), 这个就是 v2ray 客户端要连的地址.
