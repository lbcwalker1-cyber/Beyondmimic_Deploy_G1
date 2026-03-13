# GitHub Copilot 配置说明 / GitHub Copilot Configuration

## 关于 PyCharm 中 Claude Sonnet 4.5 不可用的问题

### 问题说明

在 PyCharm 的 GitHub Copilot 插件中，可选模型列表中可能不包含 **Claude Sonnet 4.5**，原因如下：

---

### 原因分析

#### 1. 订阅计划限制
Claude Sonnet 4.5 等较新的模型需要 **GitHub Copilot Business** 或 **GitHub Copilot Enterprise** 订阅计划才能使用。免费版或个人版（Individual）可能无法访问所有可选模型。

- 请前往 [GitHub 账号设置](https://github.com/settings/copilot) 确认当前订阅计划。

#### 2. 组织/企业策略限制
如果你通过组织或企业账号使用 Copilot，管理员可能限制了可用模型范围。

- 请联系你的组织管理员，在 **Organization Settings → Copilot → Policies** 中启用 Claude 模型。

#### 3. PyCharm Copilot 插件版本过旧
旧版本的 JetBrains Copilot 插件可能尚未支持 Claude Sonnet 4.5。

- 请在 PyCharm 中前往 **Settings → Plugins → GitHub Copilot**，确保插件已更新至最新版本（建议使用 JetBrains Marketplace 中的最新稳定版）。

#### 4. 地区可用性
部分模型可能尚未在所有地区开放，具体可用性因地区和 GitHub 服务策略而异，请以官方文档为准。

---

### 解决步骤

1. **检查订阅**：确认你拥有 Copilot Business 或 Enterprise 订阅。
2. **更新插件**：将 PyCharm 的 GitHub Copilot 插件更新至最新版本。
3. **检查组织策略**：联系管理员确认 Claude 模型已在组织层面启用。
4. **重启 IDE**：更新插件或更改设置后，重启 PyCharm 使更改生效。
5. **切换模型**：在 Copilot Chat 窗口，点击模型选择下拉框，查看 Claude Sonnet 4.5 是否已出现。

---

### 参考链接

- [GitHub Copilot 支持的模型列表](https://docs.github.com/en/copilot/using-github-copilot/asking-github-copilot-questions-in-your-ide)
- [GitHub Copilot 计划对比](https://github.com/features/copilot/plans)
- [JetBrains Marketplace - GitHub Copilot 插件](https://plugins.jetbrains.com/plugin/17718-github-copilot)

---

## About Claude Sonnet 4.5 Not Available in PyCharm Copilot

### Reasons

1. **Subscription Plan**: Claude Sonnet 4.5 requires **GitHub Copilot Business** or **Enterprise** plan.
2. **Organization Policy**: Your org admin may have restricted available models — check *Organization Settings → Copilot → Policies*.
3. **Outdated Plugin**: Update the GitHub Copilot plugin in PyCharm to the latest version via *Settings → Plugins*.
4. **Regional Availability**: Some models may not be available in all regions.

### Steps to Fix

1. Verify your Copilot subscription at https://github.com/settings/copilot
2. Update the GitHub Copilot plugin in PyCharm to the latest version
3. Ask your organization admin to enable Claude models in Copilot policies
4. Restart PyCharm after any changes
