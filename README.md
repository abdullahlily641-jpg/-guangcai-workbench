# 广财财税 AI 营销项目 · 员工执行分工工作台

纯静态单文件工作台，完全自包含（内联 CSS + 原生 JS，无任何外部 CDN / 第三方依赖），可脱离 WorkBuddy 生态独立运行。

## 目录结构（整目录即 GitHub Pages 站点根）

```
github-pages-deploy/
├── index.html   # 工作台主页面（唯一核心文件）
├── CNAME        # 自定义域名：gongcai.wegrow2025.com
├── .nojekyll    # 禁用 GitHub 的 Jekyll 处理
└── README.md    # 本说明
```

## 上线步骤（GitHub Pages + 自定义域名）

### 1. 新建 GitHub 仓库
- 在 GitHub 新建一个 **公开（Public）** 仓库，例如 `guangcai-workbench`。
- 不要把仓库名当成域名——真正对外访问的域名由 `CNAME` 文件决定。

### 2. 推送本目录到仓库
在 `github-pages-deploy/` 目录下执行（把 `<你的GitHub用户名>` 换成实际用户名）：

```bash
git init
git add -A
git commit -m "广财财税AI营销项目-员工执行分工工作台"
git branch -M main
git remote add origin https://github.com/<你的GitHub用户名>/guangcai-workbench.git
git push -u origin main
```

> 也可不走命令行：直接在 GitHub 网页端把本目录 3 个文件（index.html / CNAME / .nojekyll）拖到新仓库即可。

### 3. 开启 GitHub Pages
- 仓库 `Settings` → `Pages` → `Build and deployment` → `Source` 选 **Deploy from a branch**。
- `Branch` 选 **main**，`Folder` 选 **/ (root)**，点 **Save**。
- 约 1 分钟后，GitHub 会显示站点地址 `https://<你的GitHub用户名>.github.io/guangcai-workbench/`。

### 4. 绑定自定义域名
- 仍在 `Settings` → `Pages` → `Custom domain` 填入 `gongcai.wegrow2025.com`，点 **Save**。
- 稍等片刻出现 `DNS check successful` 后，勾选 **Enforce HTTPS**（GitHub 免费提供 SSL 证书，需 DNS 生效后才会可选）。
- 若 `Custom domain` 被清空：确认 `CNAME` 文件已正确提交（内容为 `gongcai.wegrow2025.com`）。

### 5. 在 wegrow2025.com 的 DNS 后台加解析（关键，需你/运维操作）
到 `wegrow2025.com` 的域名解析控制台（腾讯云 DNSPod / 阿里云云解析等）添加一条记录：

| 记录类型 | 主机记录 | 记录值（指向）        | TTL  |
|----------|----------|-----------------------|------|
| CNAME    | gongcai  | `<你的GitHub用户名>.github.io` | 600  |

> 注意：记录值末尾的 `.github.io` 后**不要**加点（GitHub 现版已不要求）。
> 如果想换成别的子域名（如 `workbench.wegrow2025.com`），同时改 `CNAME` 文件内容和这条解析的主机记录即可。

### 6. 访问
DNS 生效（通常几分钟，最多 24h）后，打开：

**https://gongcai.wegrow2025.com**

即为对外正式链接，域名带 `wegrow`，与 WorkBuddy 无关。

## 后续维护
- 修改工作台内容：改 `index.html` 后重新 `git commit && git push` 即可，GitHub Pages 会自动重新构建（约 1 分钟）。
- 负责人在页面里用「更新」维护进度，数据存在浏览器 `localStorage`，建议定期用页面右上角「导出」做备份（导出文件可「导入」恢复）。
- 若需多人共享同一份进度而非各自本地存储，后续可接入后端数据库——届时再评估。

## 备注
- 当前交付测算以项目起始日 2026-08-19 为基准，页面右上角「设置」可改起始日与周期，所有日期自动重算。
- 5 大模块最晚第 60 天（2026-10-18）全部交付，总复盘第 90 天（2026-11-17）。
