# v2ss-docker
docker-compose 快速部署 shadowsocks v2ray-plugin nginx  <br>
MinIO 只是用来伪装成真实网站
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

## 3. Clash Clinet
> password 和 host 与之前保持一致
```yaml
proxies:
- name: "ss-v2ray"
  type: ss
  server: server.com
  port: 443
  cipher: chacha20-ietf-poly1305
  password: "123123"
  plugin: v2ray-plugin
  plugin-opts:
    mode: websocket
    tls: true
    host: server.com
    path: "/v2ss"
```
