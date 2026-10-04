# aaronalpha-node

属于你自己的 Cloudflare Worker 个人网络节点。

一次搭建，运行零成本（Cloudflare 免费套餐内）；域名需自购、自续费。

## 这是什么

- 跑在**你自己** Cloudflare 账号里的 Worker，VLESS + WebSocket + TLS
- UUID 你自己生成、自己独享，不经过任何第三方中转，不与他人共享
- 绑定你自己的域名，对外就是你自己的节点

## 快速部署（5 步）

1. 复制 `worker.js` 全文
2. 打开 [Cloudflare Dashboard](https://dash.cloudflare.com) → Workers 和 Pages → 创建 Worker → 粘贴代码 → 部署
3. 在 Worker 的变量里设置你自己的 `UUID`（去 uuidgenerator.net 生成一个）和管理密码
4. 绑定自定义域：Worker → Domains → Add Domain → 输入你的子域名（如 `node.你的域名.top`）
   - 如果提示该主机名已有 DNS 记录，先去 DNS 里删掉那条旧记录再添加
5. 按下面格式拼出你的节点链接，导入客户端（推荐免费的 Streisand，iOS App Store 可下）：
   - **一定要用「从剪贴板导入」，不要手动添加**

```
vless://你的UUID@你的域名:443?encryption=none&security=tls&sni=你的域名&fp=chrome&type=ws&host=你的域名&path=%2F你的UUID#备注名
```

## 验证

- 打开 `https://你的域名/` 应看到伪装页
- 打开 `https://你的域名/你的UUID` 应跳转到 `/login`
- 客户端连上后访问 `ip.sb`，对外显示 Cloudflare 美国节点 IP

## 风险与免责（必读）

1. Cloudflare 政策、网络环境变化属不可抗力，节点可能受影响
2. 域名按年续费，过期节点即失效，请自行留意
3. 链接即钥匙：vless 链接谁拿到谁能用，不要转发；建议定期更换 UUID
4. 免费套餐每天 10 万次请求，个人使用足够；被超额共享会导致停用
5. 请遵守你所在地的法律法规；部署与使用中的问题请自行排查

## 致谢

本项目代码基于开源项目 [edgetunnel](https://github.com/cmliu/edgetunnel)（MIT License），感谢原作者 cmliu。

## License

MIT
