# Cloudflare Worker 零成本代理节点完整部署技术文档
文档版本：V2.0  
最后更新：2026-05-10  
适用平台：Windows / macOS / Android / iOS  
部署成本：0 元  
使用说明：仅限网络技术学习与合法测试，严禁违法使用

---

## 目录
1. 合规与风险声明
2. 项目概述
3. 前置资源与工具
4. Cloudflare Worker 创建与初始化
5. 开源脚本部署与环境变量配置
6. 免费域名注册（10 年有效期）
7. 域名托管至 Cloudflare（NS 解析）
8. 自定义域名与 Worker 绑定
9. 节点订阅获取与客户端配置
10. 功能与性能验证
11. 常见故障排查
12. 项目维护与更新
13. 开源协议

---

## 1. 合规与风险声明
1. 本文档仅用于计算机网络技术学习、研究与合法网络测试。
2. 使用者承诺遵守所在国家/地区法律法规，不用于非法用途。
3. 因违规使用产生的一切责任由使用者自行承担。
4. 本项目基于 Cloudflare 官方服务与开源脚本实现，仅作技术分享。

---

## 2. 项目概述
本项目基于 Cloudflare Workers 无服务器架构，搭配开源代理脚本与免费域名，实现零成本、高速、稳定的代理节点部署。

### 核心优势
- 完全免费：无服务器、无订阅、无域名费用
- 全球加速：Cloudflare 自动优选线路
- 高兼容性：支持 YouTube 4K、AI 工具访问
- 简易部署：全程鼠标操作，无需代码
- 长期稳定：10 年免费域名，支持自动续签

### 技术架构
Cloudflare Worker + 开源 JS 脚本 + 免费域名 + TLS 加密

---

## 3. 前置资源与工具
### 3.1 必备账号
- Cloudflare 账号：https://dash.cloudflare.com/
- 免费域名平台：https://dns.xyz

### 3.2 核心资源链接
- 稳定开源脚本：https://github.com/3Kmfi6HP/EDtunnel/blob/main/_worker.js
- 在线 UUID 生成器：https://www.uuidgenerator.net/
- 客户端工具：V2rayN / Clash Meta / NekoBox

### 3.3 命名规范
- Worker 名称禁止包含：proxy、vpn、代理、翻墙
- 域名前缀保持常规英文/数字，不使用敏感词

---

## 4. Cloudflare Worker 创建与初始化
1. 登录 Cloudflare 控制台
2. 左侧菜单：Compute → Workers & Pages
3. 点击 Create application → Workers → Create Worker
4. 设置名称（无敏感词）→ Deploy
5. Worker 创建完成（空壳状态）

---

## 5. 开源脚本部署与环境变量配置
### 5.1 获取脚本代码
打开脚本链接，全选复制全部代码。

### 5.2 部署代码
1. 进入 Worker → Edit code
2. 删除默认 hello world 代码
3. 粘贴复制的脚本 → Save and Deploy

### 5.3 配置 UID 环境变量
1. Settings → Variables
2. 添加变量：
   - 名称：UID（必须大写）
   - 值：UUID 生成器生成的字符串
3. 保存配置

---

## 6. 免费域名注册（10 年）
1. 登录 https://dns.xyz
2. 免费域名 → 创建域名
3. 选择后缀：.cc / .tk / .ml
4. 设置前缀 → 注册成功（有效期 10 年）

---

## 7. 域名托管至 Cloudflare
1. Cloudflare → Domains → Add a Domain
2. 输入域名 → 选择免费套餐
3. 记录 Cloudflare 提供的 2 个 NS 地址
4. 回到域名平台，修改 DNS 为这 2 个 NS
5. 等待 3–5 分钟，解析生效

---

## 8. 自定义域名与 Worker 绑定
1. Worker → Settings → Domains & Routes
2. Add Custom Domain
3. 输入已托管域名 → 添加完成
4. 状态显示 Active 即为成功

---

## 9. 节点订阅获取与客户端配置
### 9.1 获取订阅链接
浏览器访问：