# Agent Plugins Hub Releases

Agent Plugins Hub 的官方 Runtime/CLI 成品分发仓库，安装包保存在 GitHub Releases 中。

**当前版本：[v0.1.0 CLI 预览](https://github.com/starXmate/agent-plugins-hub-releases/releases/tag/v0.1.0)**（2026-11-05）。包含 Linux/Windows Runtime、薄启动器、签名及验收记录。

## 快速使用

需要 **Node.js 24.18.0**。已验收的平台为 Ubuntu 24.04 x64（glibc 2.39）和 Windows 11 25H2 x64（build 26200）；macOS 与 Homebrew 暂未发行。

安装公开薄启动器：

```sh
npm install -g https://github.com/starXmate/agent-plugins-hub-releases/releases/download/v0.1.0/agentplug-0.1.0-preview.1.tgz
```

管理插件：

```sh
agentplug add <条目或owner/repo>
agentplug list
agentplug update <安装ID>
agentplug remove <安装ID>
```

首次管理命令自动下载并验签对应平台 Runtime。安装前会展示来源、权限和范围，确认后执行；连接受支持的本机 Agent 时可追加 `--agent codex`。更新沿用稳定安装 ID，移除保留共享版本与可恢复数据。

无需全局安装也可运行同一薄包，例如：

```sh
npx --yes https://github.com/starXmate/agent-plugins-hub-releases/releases/download/v0.1.0/agentplug-0.1.0-preview.1.tgz list
```

## 发行状态

- Runtime 与 `agentplug@0.1.0-preview.1` 薄包已在上述 GitHub Release 公开，双平台签名成品验收通过；Linux 真实公开下载、四条管理命令、数据保留和冷启动已实测。
- 公共 npm 包尚未发布，裸 `npx agentplug` 暂不可用；当前请使用上面的 GitHub 安装入口。
- 此版提供基础插件管理；完整生产稳定性、真实 Agent/模型及多 Agent 验收继续后续。

[查看所有版本与下载文件](https://github.com/starXmate/agent-plugins-hub-releases/releases)
