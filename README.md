# nginx-config-snippets

Nginx 配置片段与排错手册：10 个拿来即用的配置片段 + 排错手册 + 上线检查清单。

每个片段解决一个具体问题，头部注释标注用法与要改的位置，全部来自生产环境实战。

## 快速开始

```bash
git clone https://github.com/lizs-eng/nginx-config-snippets.git
cp snippets/reverse_proxy.conf /etc/nginx/conf.d/myapp.conf
# 改 server_name 与 proxy_pass 为你的域名与后端
nginx -t && systemctl reload nginx
```

## 免费样章（3 个，本仓库）

| 片段 | 解决什么 |
|---|---|
| `reverse_proxy.conf` | 标准反向代理（透传真实 IP/Host） |
| `websocket_proxy.conf` | WebSocket 反代：Upgrade 三件套 + 400/断连排错 |
| `https_redirect.conf` | HTTP→HTTPS 跳转 + HSTS + gzip |

## 完整版（¥19.9）

追加 7 个片段 + 3 份手册：

- **rate_limit.conf** 接口限流防刷（429 + 突发处理）
- **cache_static.conf** 静态资源缓存策略 + SPA 路由回退
- **load_balance.conf** 多实例负载均衡 + 会话保持 + 备用机
- **large_upload.conf** 大文件上传（默认 1M 限制的解法）
- **security_headers.conf** 安全响应头全套
- **stream_tcp.conf** TCP/UDP 端口转发（数据库不直接暴露）
- **手册**：《使用说明》（三步接入+回滚）《排错手册》（502/400/413/循环重定向/证书 六大经典报错）《性能与安全清单》（上线前逐条过）

→ 完整版与更多作品：[面包多小店](https://mbd.pub/o/engineer)

## 校准与许可

- 按 2026-10 的 nginx 主线版本（1.24+）行为校准
- 发现问题欢迎提 issue；许可：MIT（见 LICENSE）
