# v2ss-docker 

docker-compose 快速部署 shadowsocks v2ray-plugin nginx  <br>


> 这个项目可以在几分钟内部署一套新服务.

## FAQ:

1. 电信网路晚上速度慢怎么解决 ?
   > 关闭光猫 QOS , 关闭后速度还是慢可使用国内服务器转发, 或者忍一忍 早点睡 😝
1. 为什么不使用 v2ray 或 trojan ?
   > SS 解码速度快 , 配合插件提高安全性, 如果有需求可以出trojan版教程 
1. MinIO 有什么用 ?
   > 让服务更像一个正常网站, 可以根据喜欢换别的
1. 可以换端口么 ?
   > 可以, 不用443的话2天就要换一次端口 🤣
1. 使用 Cloudflare 后无法连接?
   > Cloudflare 的IP已经快封没了. 
1. 如何选择VPS运营商
   > 小运营商更不容易被封 . AWS 和 Google 是GFW重点关注对象,定期会把有嫌疑的服务批量封禁 <br>
   > AWS 和 Google 的免费大礼包还是很香的.<br>
1. 如何避免被封禁
   > 不要看违规内容,看了会提高服务器的嫌疑等级. <b>没有人上网一天只看一个网站<b>




## 1. Edit Config
```bash
# 修改密码 password
vim v2ss/config.json

# 修改域名 server_name
vim nginx/server.conf
```
## 2.Replace Cert
> 阿里云免费申请

## 3.Run

```bash
docker-compose up -d --build
```

## 4. Clash Clinet
> password 和 host 与之前保持一致
```yaml
proxies:
- name: "ss-v2ray"
  type: ss
  server: server.com #😐 改
  port: 443
  cipher: chacha20-ietf-poly1305
  password: "123123" #😐 改
  plugin: v2ray-plugin
  plugin-opts:
    mode: websocket
    tls: true
    host: server.com #😐 改
    path: "/v2ss"
```
