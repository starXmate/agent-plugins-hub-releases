# Agent Plugins Hub Releases

官方 Runtime/CLI 成品分发仓库。当前预览：[**v0.1.1 · Linux / Windows x64**](https://github.com/starXmate/agent-plugins-hub-releases/releases/tag/v0.1.1)。

## 快速使用

需要 **Node.js 24.18.0**。本轮使用 GitHub 安装入口，安装一次即可管理插件：

```sh
npm install -g https://github.com/starXmate/agent-plugins-hub-releases/releases/download/v0.1.1/agentplug-0.1.0-preview.2.tgz
```

```sh
agentplug add <市场条目或owner/repo> --agent codex
agentplug list
agentplug update <安装ID>
agentplug remove <安装ID>
```

仓库包含多个插件时，加 `--path <插件子目录>`。首次管理命令自动下载并校验对应平台的运行组件，无需选择 Assets 或手动处理签名文件。终端先展示来源、权限和范围，确认后安装；目标 Agent 连接会单独审查。安装 ID 在更新后保持不变，移除保留共享版本与数据。

在[插件市场](https://plugins.xiqinger.com/)发现条目后，可复制 Hub 命令，也可继续使用来源方安装方案。帮助：`agentplug help`、`agentplug help add`、`agentplug help advanced`。

无需全局安装时，可直接执行同一薄包：

```sh
npx --yes https://github.com/starXmate/agent-plugins-hub-releases/releases/download/v0.1.1/agentplug-0.1.0-preview.2.tgz list
```

公共 npm 包本轮不发布，裸 `npx agentplug` 暂不可用，请使用上面的 GitHub 入口。

## 已验证范围

- Ubuntu 24.04 x64（glibc 2.39）及 Windows 11 25H2 x64（build 26200），Node 24.18.0；Intel macOS、Homebrew 和其他架构暂缓。
- 同一签名候选已在两个原生 Runner 验证首次启动、四条管理命令、稳定安装 ID、数据保留及冷启动。
- Linux 以 nobody、空白配置从真实公开 URL 下载并通过相同管理闭环，市场固定仓库来源审查也通过。Windows 公开下载归档验签、摘要与原生成品一致。
- 此版提供基础插件管理；实际 Agent 加载、模型调用、多 Agent 及完整生产稳定性继续单独验收。

<details>
<summary>维护者：Assets 各文件的用途</summary>

| 文件 | 用途 |
| --- | --- |
| `agentplug-*.tgz` | 顶部安装命令使用的公共薄启动器。 |
| Linux/Windows `*.tar.gz` | CLI 自动选择并下载的运行组件。 |
| `*.sigstore.json` | CLI 自动配套获取并验证的来源、完整性证据。 |
| `*.inventory.json` | 薄包内容及摘要记录。 |
| `acceptance-evidence.json` 及其签名 | 固定候选、摘要和实际原生作业的验收证据。 |

这些附件用于自动校验与追溯，普通用户使用顶部安装入口即可。
</details>
