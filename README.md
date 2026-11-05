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
agentplug add <owner/repo> --path <插件子目录> --agent codex
agentplug list
agentplug update <安装ID>
agentplug remove <安装ID>
```

插件位于仓库根目录时省略 `--path`。

首次管理命令自动下载并验签对应平台 Runtime。用户不需要逐个下载 Assets 或操作签名文件。安装前会展示来源、权限和范围，确认后执行；连接受支持的本机 Agent 时可追加 `--agent codex`。更新沿用稳定安装 ID，移除保留共享版本与可恢复数据。

无需全局安装也可运行同一薄包，例如：

```sh
npx --yes https://github.com/starXmate/agent-plugins-hub-releases/releases/download/v0.1.0/agentplug-0.1.0-preview.1.tgz list
```

当前 0.1.0 对部分市场条目的短来源身份识别不完整。遇到“缺少唯一固定提交”时，请使用上述明确仓库与子目录的方式；修复将随下一版 Runtime 发布。

## 发行状态

- Runtime 与 `agentplug@0.1.0-preview.1` 薄包已在上述 GitHub Release 公开，双平台签名成品验收通过；Linux 真实公开下载、四条管理命令、数据保留和冷启动已实测。
- 公共 npm 包尚未发布，裸 `npx agentplug` 暂不可用；当前请使用上面的 GitHub 安装入口。
- 此版提供基础插件管理；完整生产稳定性、真实 Agent/模型及多 Agent 验收继续后续。

[查看所有版本与下载文件](https://github.com/starXmate/agent-plugins-hub-releases/releases)

<details>
<summary>维护者：Assets 各文件的用途</summary>

| 文件 | 用途 |
| --- | --- |
| `agentplug-*.tgz` | 上面的 npm 安装命令使用的薄启动器，自动选择平台。 |
| `agent-plugins-hub-*-linux-x64.tar.gz` / `*-win32-x64.tar.gz` | 平台运行组件，由 CLI 自动下载；也供受控离线安装。 |
| `*.sigstore.json` | 自动验证来源和完整性，CLI 下载时配套获取。 |
| `*.inventory.json` | 薄包内容和摘要记录，供发行核对。 |
| `acceptance-evidence.json` 及其签名 | 固定候选、摘要及实际平台作业的验收证据。 |

保留这些附件支持自动校验和追溯，普通用户使用顶部安装入口即可。
</details>
