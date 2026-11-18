# Agent Plugins Hub Releases

官方 Runtime/CLI 成品分发仓库。当前 npm CLI 为 **`@agentplug/cli@0.1.0-preview.10`**；macOS Runtime 为 [**0.1.2-macos.4**](https://github.com/starXmate/agent-plugins-hub-releases/releases/tag/v0.1.2-macos.4)。Ubuntu 24.04 x64 与 Windows 11 x64 继续使用 [Runtime 0.1.1](https://github.com/starXmate/agent-plugins-hub-releases/releases/tag/v0.1.1)，尚不包含本次项目连接更新。

## 安装

需要 **Node.js 16 或更高版本**。macOS 支持 26.5 及更新的 26.x，包含 Apple Silicon 与 Intel。

```sh
npm install -g @agentplug/cli
agentplug list
```

首次管理命令自动准备匹配平台的运行环境，下载官方 Runtime 并验签。帮助与版本查询无需下载 Runtime。

## 选择项目级或用户级

以真实市场条目 Frontend Design 为例。项目级供指定项目使用；用户级供当前用户在本机各项目使用。Codex 项目级连接前，先在 Codex 中信任目标项目。

```sh
# 项目级：从目标项目目录执行
agentplug add catalog:skill-anthropics-skills-frontend-design --agent codex --project .

# 项目级：从其他目录指定项目，将示例路径换成实际路径
agentplug add catalog:skill-anthropics-skills-frontend-design --agent codex --project "/path/to/My Project"

# 用户级：从任意目录执行
agentplug add catalog:skill-anthropics-skills-frontend-design --agent codex --user

# Claude Code
agentplug add catalog:skill-anthropics-skills-frontend-design --agent claude-code --project .
agentplug add catalog:skill-anthropics-skills-frontend-design --agent claude-code --user

# Cursor
agentplug add catalog:skill-anthropics-skills-frontend-design --agent cursor --project .
agentplug add catalog:skill-anthropics-skills-frontend-design --agent cursor --user
```

在 Cursor 中批准并加载对应 Hub MCP 服务后，运行 `agentplug confirm-agent-reload <连接ID> --confirm`，连接 ID 取自安装结果的 `connection.connection.id`。

由 Hub 执行的 Skill/MCP 最低已验证稳定版本：Codex `0.152.1`、Claude Code `2.1.263`、Cursor `3.18.9`；连接时继续检查实际可用接口。这些项目连接与版本兼容变化需要 macOS Runtime `0.1.2-macos.4` 或更新版本。Cursor 桌面交互聊天仍单列验收。

```sh
agentplug list
agentplug update <安装ID>
agentplug remove <安装ID>
agentplug help add
```

仓库包含多个插件时，加 `--path <插件子目录>`。终端会展示来源、权限和范围，并审查 Agent 连接。安装 ID 在更新后保持稳定；移除保留其他引用所需的共享版本与数据。

[插件市场](https://plugins.xiqinger.com/marketplace) · [使用文档](https://plugins.xiqinger.com/docs#cli) · [npm 包](https://www.npmjs.com/package/@agentplug/cli)

## 从旧版升级

```sh
npm install -g @agentplug/cli
```

已有 Runtime 不会因 CLI 升级自动替换。继续使用原 Node.js 24.18.0 安装路径，下载并解压本页对应架构的签名归档，执行 `agentplug setup <解压后的目录>`，再审查并重新连接目标 Agent。

## 发行校验

两种原生 Mac 均已验证真实系统 Keychain、Codex App Server 首次安装、升级保留绑定与授权、撤销并重连及冷启动。实际测试平台、源码和精确摘要见 [Runtime 0.1.2-macos.4](https://github.com/starXmate/agent-plugins-hub-releases/releases/tag/v0.1.2-macos.4) 附带的验收报告；Homebrew 与模型对话继续单列。

Assets 中的 Runtime 归档、`*.sigstore.json`、`SHA256SUMS`、npm `*.tgz`/`*.inventory.json` 和 `verified-*.json` 用于自动验签与追溯。普通用户使用顶部 npm 安装命令即可。

## License

CLI 与 Runtime 使用 [Apache-2.0](https://www.apache.org/licenses/LICENSE-2.0)，第三方依赖保留各自许可证。
