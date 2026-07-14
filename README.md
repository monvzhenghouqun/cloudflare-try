# Cloudflare 静态站点部署说明

这是一个简单的静态网页示例，包含两种部署到 Cloudflare 的常见方法：Cloudflare Pages（推荐）和使用 Wrangler CLI 的 Pages 发布（适合本地/脚本化发布）。

## 1. 准备
- 一个 Cloudflare 账号
- 将本仓库推送到 GitHub（或 Git 提供商）以便使用 Pages（可选）
- 安装 `wrangler`（如果你想使用命令行发布）：

```bash
# 全局安装
npm install -g wrangler
# 或项目内安装
npm install --save-dev wrangler
```

## 2. 使用 Cloudflare Pages（推荐）
1. 在 Cloudflare 仪表盘中选择 **Pages**，点击 **Create a project**。
2. 连接你的 GitHub 仓库并选择本仓库。
3. 构建设置：
   - **Build command**: 留空（本项目为纯静态）
   - **Build directory**: `.`（项目根目录，包含 `index.html`）
4. 完成后 Cloudflare 会自动构建并部署，之后每次推送会触发自动部署。

## 3. 使用 Wrangler CLI 发布到 Pages（命令行）
1. 在 Cloudflare 仪表盘 → My Profile → API Tokens 中创建一个具有 `Account Resources: Pages` 权限的 API Token。
2. 登录 wrangler：

```bash
wrangler login
# 或使用 API token（示例）
export CLOUDFLARE_API_TOKEN=your_token_here
```

3. 使用 `wrangler pages` 发布（示例）：

```bash
# 第一次需要指定项目名
wrangler pages project create my-static-site
# 发布当前目录到 Pages
wrangler pages publish . --project-name=my-static-site
```

更详细的 `wrangler pages` 使用说明请参考官方文档：https://developers.cloudflare.com/pages/ 

## 4. 可选：自动化（GitHub Actions）
如果你想在 GitHub 上通过 Actions 自动发布，也可以创建一个 workflow，或直接使用 Cloudflare Pages 的 Git 集成（更简单）。

---
主页文件：`index.html`，已包含简单样式。祝部署顺利！如需我帮你创建 `wrangler.toml` 或 GitHub Actions workflow，我可以继续。