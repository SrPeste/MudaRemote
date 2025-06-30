[English](README.md) | [Français](README.fr.md) | [简体中文](README.zh-CN.md) | [日本語](README.ja.md) | [한국어](README.ko.md)

# ✨ MudaRemote: Mudae 高级自动化 ✨

[![Discord TOS Violation - **谨慎使用**](https://img.shields.io/badge/Discord%20TOS-VIOLATION-red)](https://discord.com/terms) ⚠️ **账号封禁风险！** ⚠️

**🛑🛑🛑 警告：自机器人 - 潜在的 Discord 服务条款违规！账号封禁风险！ 🛑🛑🛑**
**🔥 使用风险自负！ 🔥 我们不对您的账户采取的任何行动负责。 😱**

---

## 🚀 MudaRemote: 提升您的 Mudae 体验 (负责任地使用！)

MudaRemote 是一个基于 Python 的自机器人，旨在自动化 Discord 机器人 Mudae 的各种任务。它提供实时狙击和智能认领等功能。**然而，使用自机器人违反了 Discord 的服务条款，可能导致您的账户被暂停或封禁。** 请务必谨慎使用，并了解其中涉及的风险。

### ✨ 核心功能:

*   **🎯 外部狙击 (心愿单、系列和 Kakera 值):**
    *   **心愿单狙击:** 当 *其他人* 抽到您心愿单中的角色时，自动认领 (可配置延迟)。
    *   **系列狙击:** 当 *其他人* 抽到您系列心愿单中的角色时，自动认领 (可配置延迟)。
    *   **Kakera 值狙击:** 当 *其他人* 抽到角色时，根据其 Kakera 值 (如果高于阈值) 自动认领。
*   **🟡 外部 Kakera 反应狙击 (新功能！):** 自动点击 *任何* Mudae 消息中的 Kakera 反应按钮。
*   **😴 仅狙击模式:** 将机器人实例配置为 *只* 监听和执行外部狙击，而不发送抽卡命令。
*   **⚡ 反应式自抽狙击:** 如果 *您自己* 抽到的角色符合条件 (心愿单、系列、Kakera 值)，则立即认领。中断当前抽卡批次。
*   **👯 多账户支持:** 同时运行多个机器人实例，每个实例都有自己的配置。
*   **🤖 自动化抽卡和通用认领:** 处理您的抽卡命令，并在抽卡完成后根据最低 Kakera 值进行通用认领。
*   **🥇 智能认领逻辑:** 利用 `$rt` 进行潜在的第二次认领。
*   **🔄 自动抽卡和认领重置检测:** 监控并等待 Mudae 的重置计时器以优化操作。
*   **🔑 关键模式:** 即使您的主要角色认领权限处于冷却状态，也能持续抽卡以收集 Kakera。
*   **⏱️ 可自定义的延迟和抽卡速度:** 调整通用操作延迟和抽卡命令的速度。
*   **🗂️ 简易预设配置:** 通过 `presets.json` 文件管理不同账户/场景的所有设置。
*   **📊 控制台日志:** 清晰、彩色编码的机器人操作和状态实时输出。

---

## 🛠️ 设置指南

1.  **🐍 Python:** 确保已安装 Python 3.8+。([下载 Python](https://www.python.org/downloads/))
2.  **📦 依赖项:** 打开您的终端或命令提示符并运行:
    ```bash
    pip install discord.py-self inquirer
    ```
3.  **📝 `presets.json`:** 在脚本的同一目录下创建名为 `presets.json` 的文件。在此处添加您的机器人配置。有关所有可用选项，请参阅以下示例。
4.  **🚀 运行:** 从您的终端执行脚本:
    ```bash
    python mudae_bot.py
    ```
    (如果文件名不同，请将 `mudae_bot.py` 替换为您的脚本的实际文件名)。
5.  **🕹️ 选择预设:** 从出现的交互式菜单中选择要运行的已配置机器人。

---

### `presets.json` 配置示例:

```json
{
  "YourBotAccountName": {
    // --- 必填设置 ---
    "token": "YOUR_DISCORD_ACCOUNT_TOKEN", // 您的 Discord 账户令牌。请务必保密！
    "channel_id": 123456789012345678,     // Mudae 命令的 Discord 频道 ID。
    "roll_command": "wa",                  // 您偏好的 Mudae 抽卡命令 (例如: wa, hg, w, ma)。仅当 "rolling" 为 true 时使用。
    "delay_seconds": 1,                    // 机器人某些操作之间的通用延迟 (秒) (例如: $tu 解析前)。仅当 "rolling" 为 true 时使用。
    "mudae_prefix": "$",                   // Mudae 在您的服务器中使用的前缀 (通常是 "$")。
    "min_kakera": 50,                      // 通用 (抽卡批次后) 角色认领的最低 Kakera 值。仅当 "rolling" 为 true 时使用。

    // --- 核心操作模式 ---
    "rolling": true,                       // (默认: true) 如果为 true，机器人执行抽卡、认领、$tu 检查等操作。
                                           // 如果为 false，机器人进入仅狙击模式: 不抽卡，不进行 $tu 检查，只监听外部狙击。

    // --- 可选设置 (部分取决于 "rolling: true") ---
    "key_mode": false,                     // (默认: false) 如果为 true 且 "rolling" 为 true，即使没有角色认领权限，也会为收集 Kakera 而抽卡。
    "start_delay": 0,                      // (默认: 0) 在菜单中选择后，机器人启动前的延迟 (秒)。
    "roll_speed": 0.4,                     // (默认: 0.4) 单个抽卡命令之间的延迟 (秒)。仅当 "rolling" 为 true 时使用。

    // 外部狙击设置 (针对其他人抽到的角色/Kakera - 无论 "rolling" 状态如何，如果配置，始终处于活动状态)
    "snipe_mode": true,                    // (默认: false) 启用外部心愿单狙击 (心形认领)。
    "wishlist": ["Character Name 1", "Character Name 2"], // 用于心形狙击的角色名称列表。
    "snipe_delay": 2,                      // (默认: 2) 认领外部心愿单狙击和外部 Kakera 值狙击前的延迟 (秒)。

    "series_snipe_mode": true,             // (默认: false) 启用外部系列狙击 (心形认领)。
    "series_wishlist": ["Series Name 1"],  // 用于心形狙击的系列名称列表。
    "series_snipe_delay": 3,               // (默认: 3) 认领外部系列狙击前的延迟 (秒)。

    "kakera_reaction_snipe_mode": false,   // (默认: false) 启用外部 Kakera 反应狙击 (点击 Kakera 按钮)。
    "kakera_reaction_snipe_delay": 0.75,   // (默认: 0.75) 点击外部 Kakera 反应前的延迟 (秒)。

    // 反应式狙击设置 (针对您自己抽到的角色/Kakera - 仅当 "rolling: true" 时处于活动状态)
    "reactive_snipe_on_own_rolls": true,   // (默认: true) 启用/禁用在您自己抽卡期间的即时反应式心形认领和 Kakera 点击。
                                           // 如果为 true，则使用心愿单、系列心愿单和 kakera_snipe_threshold (如果 kakera_snipe_mode 为 true) 作为心形认领的标准。
                                           // 这些反应式认领的角色上的 Kakera 也会被点击。
                                           // 如果为 false，则所有针对自己抽卡的认领/Kakera 点击都在抽卡批次完成后发生。

    // Kakera 阈值设置 (用于反应式自抽心形认领和外部 Kakera 值心形狙击)
    "kakera_snipe_mode": true,             // (默认: false) 如果为 true，则启用 `kakera_snipe_threshold` 作为心形认领的标准，适用于:
                                           //    1. 在您自己抽卡期间的即时反应式心形认领 (如果 "rolling" 和 reactive_snipe_on_own_rolls 都为 true)。
                                           //    2. 延迟的外部 Kakera 值专属心形狙击 (使用 `snipe_delay`)。
    "kakera_snipe_threshold": 100,         // (默认: 0) 如果 `kakera_snipe_mode` 为 true，触发上述心形认领的最低 Kakera 值。

    // 其他 (仅当 "rolling: true" 时处于活动状态)
    "snipe_ignore_min_kakera_reset": false // (默认: false) 如果为 true，对于抽卡后的通用认领，如果您的认领重置时间少于 1 小时，则 min_kakera 实际上为 0。
                                           // 这不影响反应式狙击或外部 Kakera 值狙击阈值。
  }
  // 在此处添加其他账户的更多预设，用逗号分隔。
}
```

---

## 🎮 获取您的 Discord 令牌 🔑

自机器人需要您的 Discord 账户令牌。**此令牌授予对您账户的完全访问权限 – 请务必将其保密！分享它就像泄露您的密码。** 建议您在备用账户上使用此机器人。

1.  **在您的网络浏览器中打开 Discord** (例如: Chrome, Firefox)。*而不是桌面应用程序。*
2.  按 **F12** 打开开发者工具。
3.  导航到 **`Console`** 选项卡。
4.  将以下代码片段粘贴到控制台并按 Enter:
    ```javascript
    window.webpackChunkdiscord_app.push([
    	[Symbol()],
    	{},
    	req => {
    		if (!req.c) return;
    		for (let m of Object.values(req.c)) {
    			try {
    				if (!m.exports || m.exports === window) continue;
    				if (m.exports?.getToken) return copy(m.exports.getToken());
    				for (let ex in m.exports) {
    					if (m.exports?.[ex]?.getToken && m.exports[ex][Symbol.toStringTag] !== 'IntlMessagesProxy') return copy(m.exports[ex].getToken());
    				}
    			} catch {}
    		}
    	},
    ]);

    window.webpackChunkdiscord_app.pop();
    console.log('%cWorked!', 'font-size: 50px');
    console.log(`%cYou now have your token in the clipboard!`, 'font-size: 16px');
    ```
5.  您的令牌将被复制到剪贴板。请小心地将其粘贴到 `presets.json` 文件中的 `"token"` 字段。

---

## 🤝 贡献

欢迎贡献！随时报告问题、提出功能建议或向项目仓库提交拉取请求。

**🙏 请负责任地、合乎道德地使用此工具，并充分了解对您的 Discord 账户的潜在风险。 🙏**

**祝您 Mudae 愉快 (并谨慎)！** 😉

---
**许可证:** [MIT 许可证](LICENSE)
