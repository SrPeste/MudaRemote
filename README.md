# ✨ MudaRemote: Advanced Mudae Automation ✨

[![Discord TOS Violation - **USE CAUTIOUSLY**](https://img.shields.io/badge/Discord%20TOS-VIOLATION-red)](https://discord.com/terms) ⚠️ **ACCOUNT BAN RISK!** ⚠️

**🛑🛑🛑 WARNING: SELF-BOT - POTENTIAL DISCORD TOS VIOLATION! ACCOUNT BAN RISK! 🛑🛑🛑**
**🔥 USE AT YOUR OWN RISK! 🔥 WE ARE NOT RESPONSIBLE FOR ANY ACTIONS TAKEN AGAINST YOUR ACCOUNT. 😱**

---

## 🚀 MudaRemote: Enhance Your Mudae Experience (Use Responsibly!) 🚀

MudaRemote is a Python-based self-bot designed to automate various tasks for the Discord bot Mudae. It offers features like real-time sniping and intelligent claiming but **using self-bots is against Discord's Terms of Service and may lead to account suspension or ban.** Please use with extreme caution and understand the risks involved.

**✨ Core Features: ✨**

*   **🎯 External Sniping (Wishlist, Series & Kakera Value):**
    *   **Wishlist Sniping:** Claims characters from your wishlist when rolled by *others*, using a configurable delay (`snipe_delay`).
    *   **Series Sniping:** Claims characters from your series wishlist when rolled by *others*, using a configurable delay (`series_snipe_delay`).
    *   **Kakera Value Sniping:** Claims characters based purely on their kakera value (if above `kakera_snipe_threshold`) when rolled by *others*, using `snipe_delay`. This triggers if the character isn't already a wishlist/series match.
*   **😴 Snipe-Only Mode (Configurable per Preset):**
    *   Set `rolling: false` in a preset to have that bot instance *only* listen for and execute external snipes.
    *   In this mode, the bot will not send any roll commands, initial setup commands, or perform status checks for rolls/claims. Ideal for dedicated sniping accounts.
*   **⚡ Reactive Self-Roll Sniping (Configurable, if Rolling Enabled):**
    *   Instantly (no delay) claims characters from your *own* rolls if they match your wishlist, series wishlist, or `kakera_snipe_threshold` (if `kakera_snipe_mode` is active).
    *   This action interrupts the current rolling batch to secure the claim.
    *   Can be toggled on/off with `reactive_snipe_on_own_rolls`. (Only active if `rolling: true`).
*   **👯 Multi-Account Support:** Manage and run multiple bot instances simultaneously via presets, each with its own configuration (including rolling/snipe-only mode).
*   **🤖 Automated Rolling & General Claiming (if Rolling Enabled):** Handles your rolling commands and makes general claims based on `min_kakera` after rolls are complete.
*   **🥇 Intelligent Claim Logic (if Rolling Enabled):** Utilizes `$rt` for a potential second claim after a successful primary claim or when in Key Mode.
*   **🔄 Auto Roll & Claim Reset Detection (if Rolling Enabled):** Monitors and waits for Mudae's reset timers to optimize actions.
*   **🔑 Key Mode (if Rolling Enabled):** Enables continuous rolling specifically for kakera collection, even when your main character claim rights are on cooldown.
*   **⏱️ Customizable Delays & Roll Speed:** Adjust general action delays and the speed of rolling commands.
*   **🗂️ Easy Preset Configuration:** Manage all settings for different accounts/scenarios via a `presets.json` file.
*   **📊 Console Logging:** Clear, color-coded real-time output of bot actions and status.

---

## 🛠️ Setup Guide 💨

1.  **🐍 Python:** Ensure Python 3.8+ is installed. ([Download Python](https://www.python.org/downloads/))
2.  **📦 Dependencies:** Open your terminal or command prompt and run:
    ```bash
    pip install discord.py-self inquirer
    ```
3.  **📝 `presets.json`:** Create a file named `presets.json` in the same directory as the script. Add your bot configurations here. See the example below for all available options.
4.  **🚀 Run:** Execute the script from your terminal:
    ```bash
    python mudae_bot.py 
    ```
    (Replace `mudae_bot.py` with your script's actual filename if different).
5.  **🕹️ Select Presets:** Choose which configured bot(s) to run from the interactive menu that appears.

---

### `presets.json` Configuration Example:

```json
{
  "YourBotAccountName": { 
    // --- REQUIRED SETTINGS ---
    "token": "YOUR_DISCORD_ACCOUNT_TOKEN", // Your Discord account token. KEEP THIS EXTREMELY SECRET!
    "channel_id": 123456789012345678,     // ID of the Discord channel for Mudae commands.
    "roll_command": "wa",                  // Your preferred Mudae roll command (e.g., wa, hg, w, ma). Only used if "rolling" is true.
    "delay_seconds": 1,                    // General delay (seconds) between some bot actions (e.g., after $tu before parsing). Only used if "rolling" is true.
    "mudae_prefix": "$",                   // The prefix Mudae uses in your server (usually "$").
    "min_kakera": 50,                      // Minimum kakera value for general (post-roll batch) character claims. Only used if "rolling" is true.

    // --- CORE OPERATIONAL MODE ---
    "rolling": true,                       // (Default: true) If true, bot performs rolling, claiming, $tu checks, etc. 
                                           // If false, bot enters SNIPE-ONLY mode: no rolling, no $tu checks, only listens for external snipes.

    // --- OPTIONAL SETTINGS (Some depend on "rolling: true") ---
    "key_mode": false,                     // (Default: false) If true AND "rolling" is true, rolls for kakera even if no character claim right is available.
    "start_delay": 0,                      // (Default: 0) Delay (seconds) before the bot starts after being selected in the menu.
    "roll_speed": 0.4,                     // (Default: 0.4) Delay (seconds) between individual roll commands. Only used if "rolling" is true.

    // External Sniping Settings (for characters rolled by OTHERS - Always active if configured, regardless of "rolling" status)
    "snipe_mode": true,                    // (Default: false) Enable external wishlist sniping.
    "wishlist": ["Character Name 1", "Character Name 2"], // List of character names for sniping.
    "snipe_delay": 2,                      // (Default: 2) Delay (seconds) before claiming an external wishlist snipe AND external kakera value snipe.
    
    "series_snipe_mode": true,             // (Default: false) Enable external series sniping.
    "series_wishlist": ["Series Name 1"],  // List of series names for sniping.
    "series_snipe_delay": 3,               // (Default: 3) Delay (seconds) before claiming an external series snipe.

    // Reactive Sniping Settings (for characters from YOUR OWN rolls - Only active if "rolling: true")
    "reactive_snipe_on_own_rolls": true,   // (Default: true) Enable/disable INSTANT reactive heart claims during YOUR OWN rolls.
                                           // If true, uses wishlist, series_wishlist, and kakera_snipe_threshold (if kakera_snipe_mode is true) as criteria.
                                           // If false, all claims for own rolls happen after the roll batch is complete.

    // Kakera Threshold Settings (used for BOTH reactive self-roll AND external kakera value snipes)
    "kakera_snipe_mode": true,             // (Default: false) If true, enables `kakera_snipe_threshold` as a criterion for:
                                           //    1. INSTANT reactive heart claims during own rolls (if "rolling" AND reactive_snipe_on_own_rolls are true).
                                           //    2. DELAYED external kakera value-only heart snipes (uses `snipe_delay`).
    "kakera_snipe_threshold": 100,         // (Default: 0) Minimum kakera value to trigger claims mentioned above if `kakera_snipe_mode` is true.
    
    // Other (Only active if "rolling: true")
    "snipe_ignore_min_kakera_reset": false // (Default: false) If true, for post-roll general claims, min_kakera is effectively 0 if your claim reset is <1hr away.
                                           // This does NOT affect reactive sniping or external kakera value sniping thresholds.
  }
  // Add more presets for other accounts here, separated by commas.
}
```

---

## 🎮 Obtaining Your Discord Token 🔑

Self-bots require your Discord account token. **This token grants full access to your account – keep it extremely private! Sharing it is like giving away your password.** It is recommended to use this bot on an alternative account.

1.  **Open Discord in your web browser** (e.g., Chrome, Firefox). *Not the desktop app.*
2.  Press **F12** to open Developer Tools.
3.  Navigate to the **`Console`** tab.
4.  Paste the following code snippet into the console and press Enter:
    ```javascript
    window.webpackChunkdiscord_app.push([
      [Math.random()],
      {},
      req => {
        if (!req.c) return;
        for (const m of Object.keys(req.c)
          .map(x => req.c[x].exports)
          .filter(x => x)) {
          if (m.default && m.default.getToken !== undefined) {
            return copy(m.default.getToken());
          }
          if (m.getToken !== undefined) {
            return copy(m.getToken());
          }
        }
      },
    ]);
    console.log('%cToken copied to clipboard!', 'font-size: 18px; color: lightgreen; font-weight: bold;');
    ```
5.  Your token will be copied to your clipboard. Carefully paste it into the `"token"` field in your `presets.json` file.

---

## 🤝 Contributing

Contributions are welcome! Feel free to report issues, suggest features, or submit pull requests to the project repository.

**🙏 Please use this tool responsibly and ethically, with full awareness of the potential risks to your Discord account. 🙏**

**Happy (and Cautious!) Mudae-ing!** 😉

---
**License:** [MIT License](LICENSE)
