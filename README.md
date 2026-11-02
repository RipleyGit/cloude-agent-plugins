# Cloud Agent Plugins (Agent 插件集合仓库)

这是 [open-cloude-agent](https://github.com/RipleyGit/open-cloude-agent) 的官方 Agent 插件集合仓库与插件推荐注册中心（Registry）。

---

## 🌟 仓库定位与架构

在 `open-cloude-agent` 中，**Agent 插件**与**普通 UI 插件**有严格区分：
- **普通 UI 插件**：在「设置 -> 插件」中管理，提供独立的 Web 面板、工作区扩展。
- **Agent 插件**：在「设置 -> 智能体」中管理，作为系统的底层 Provider（与 Claude Code、Cursor、Codex 并列），提供完整的 LLM 执行驱动、模型管理与双向会话同步。

本仓库通过 `plugins.json` 维护经过官方验证的 Agent 插件列表，并在 `plugins/` 目录下通过 Git Submodule 收录各个具体的 Agent 插件子项目。

---

## 📦 收录的 Agent 插件列表

| 插件名称 | 子项目路径 | Provider ID | 插件仓库 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| **Google Antigravity (AGY)** | `plugins/cloude-agent-agycli` | `agy` | [cloude-agent-agycli](https://github.com/RipleyGit/cloude-agent-agycli) | 本地 Google `agy` 执行驱动与 Agent Provider，支持 Gemini 2.5/3.8 系列模型 |

---

## 🛠️ 如何为本项目贡献新的 Agent 插件

1. 将你的 Agent 插件独立开源为一个 Git 仓库（确保 `manifest.json` 声明 `type: "agent"` 以及 `agent: { providerId, cliName, models, ... }`）。
2. 在本项目中添加 Git Submodule：
   ```bash
   git submodule add https://github.com/<your-username>/<your-agent-plugin>.git plugins/<your-agent-plugin>
   ```
3. 在 `plugins.json` 的 `plugins` 数组中添加对应的元数据描述。
4. 提交 Pull Request。审核合并后，所有 `open-cloude-agent` 客户端将在「设置 -> 智能体」的安装列表中自动展示你的 Agent 插件！

## 📄 License
MIT
