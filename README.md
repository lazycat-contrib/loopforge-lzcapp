# LoopForge 懒猫微服打包

上游：https://github.com/Tencent/LoopForge （MIT）

自托管编码 Agent 交付工作台：以 Docker 沙箱编排 CodeBuddy / Codex / Claude Code，用 SOP 固化交付流程，关键节点人工把关。

## 打包说明

- 平台镜像：`ghcr.io/tencent/loopforge`（semver tag 如 0.3.7，amd64/arm64），MySQL 8.4 作数据库
- 由 [ca-x/lazycat-github-action](https://github.com/ca-x/lazycat-github-action) 镜像模式自动同步，定时 + 手动触发，发布喵喵商店
- **Docker 沙箱**：平台通过挂载的 `/var/run/docker.sock` 以 sibling 容器方式运行 SOP 与对话工作区（`AGENTFLOW_LOCAL_SANDBOX=docker`）；`AGENTFLOW_ISOLATED_IMAGE` 指向同步到懒猫镜像仓库的同一发布镜像
- 工作区/CLI 缓存/家目录均持久化在 `/lzcapp/var/*`
- 免密说明：本应用使用账号体系（首个注册账号自动成为管理员），登录页支持自助注册（可关闭）

## 使用

1. 打开应用，登录页注册账号（第一个账号即管理员）
2. 「个人设置」配置 CodeBuddy / Codex / Claude Code 的 API Key，按需连接 GitHub
3. 与 Main Bot 对话或运行内置 SOP；「平台验收 · 脚本与审批」体验项目无需 API Key
