# 💖✨ Mudae Auto-Claim Bot ✨💖

[![Discord TOS Violation - **USE WITH EXTREME CAUTION**](https://img.shields.io/badge/Discord%20TOS-VIOLATION-red)](https://discord.com/terms) ⚠️ **RISK OF ACCOUNT BAN!** ⚠️

**🛑🛑🛑  STOP! READ THIS ** **CRITICAL WARNING** **BEFORE PROCEEDING!** 🛑🛑🛑

This bot is a **SELF-BOT**. Using self-bots is **STRICTLY PROHIBITED** by Discord and **VIOLATES their Terms of Service**.

**🔥  YOU RISK PERMANENT SUSPENSION OR BAN OF YOUR DISCORD ACCOUNT IF YOU USE THIS BOT. 🔥**

**😱  WE ARE NOT RESPONSIBLE FOR ANY ACCOUNT ACTIONS TAKEN AGAINST YOU BY DISCORD.  😱**

**⚠️  USE THIS BOT AT YOUR OWN RISK! PROCEED WITH EXTREME CAUTION AND ONLY IF YOU FULLY UNDERSTAND THE DANGERS.  ⚠️**

---

## 🚀 Unleash the Power of Automation in Mudae! (Responsibly!) 🚀

The **Mudae Auto-Claim Bot** is your Python-powered assistant for automating tasks in the popular Mudae Discord bot!  Streamline your character collection, maximize your kakera gains, and take your Mudae game to the next level! 🌟

**✨  Key Features That Make This Bot Shine: ✨**

*   **👯‍♀️ Multi-Account Mastery:**  Run **multiple Discord accounts simultaneously**! Manage all your Mudae endeavors from one script! 🚀
*   **🤖 Fully Automated Rolling & Claiming:**  Sit back and relax! The bot **automatically rolls, detects claimable characters & kakera, and claims them for you!**  ✨
*   **💎 Kakera-Smart Claiming:**  Set your **minimum `kakera` value**!  The bot intelligently prioritizes claiming characters with **high kakera value** (or claim everything if you want!). 🧠
*   **🥇 Intelligent Claim Logic - Maximize Your Gains!**  Not just claiming, but **smart claiming!**  The bot prioritizes high-value characters and even uses `$rt` for **second claims** when opportunity strikes! 🏆
*   **🔄 Roll Reset? No Problem!**  Runs out of rolls?  The bot **automatically detects roll depletion and patiently waits** for the next reset! ⏳
*   **✅ Claim Rights?  Always in Check!**  No wasted commands! The bot **verifies claim availability** before acting, optimizing efficiency. ⚡
*   **⏱️ Customizable Delays - Be Human-Like!**  Adjust delays to **mimic human behavior** and **minimize the risk of rate-limiting**.  🤫
*   **🔑 Key Mode - Kakera Collection On Steroids!**  Enable "Key Mode" and the bot will **relentlessly roll for kakera** even when claim rights are down! Never stop collecting! 💰
*   **🗂️ Preset Power - Configuration Made Easy!**  Manage settings for **all your accounts in one organized `presets.json` file!**  Simplicity at its finest! 📂
*   **📊 Real-time Console Monitoring - Stay Informed!**  Watch the bot in action! **Real-time logs and status updates** right in your console!  👀
*   **📜 Detailed Logging - Keep Track of Your Treasures!**  Maintain a **record of all bot actions and claimed characters**! Your Mudae history at your fingertips! 📖

---

## 🛠️ Get Started in Minutes! Installation is a Breeze! 💨

1.  **🐍 Python Powerhouse:**  Make sure you have **Python 3.8 or HIGHER** installed. Get it from [python.org](https://www.python.org/downloads/)!  🚀

2.  **📦 Install the Essentials:** Open your terminal or command prompt and run:

    ```bash
    pip install discord.py-self inquirer
    ```

3.  **📝 Craft Your `presets.json` Configuration:**  Create a file named `presets.json` in the same folder as `mudae_bot.py`.  This is where the magic happens! ✨

    ```json
    {
      "MyAwesomeBot1": {  // 🌟 Give your preset a cool name!
        "token": "YOUR_DISCORD_ACCOUNT_TOKEN_1",   // 🔑  Your secret account token! (See Usage section!)
        "prefix": "!",                             // ⚙️  Bot command prefix (you likely won't use this much)
        "channel_id": 123456789012345678,         // 💬  Discord Channel ID - where the bot works! (Get it in Discord!)
        "roll_command": "wa",                       // 🎲  Mudae roll command of choice (wa, wg, ha, hg, w, h)
        "delay_seconds": 1,                         // ⏳  Delay between actions (seconds, keep it above 0.8 for safety!)
        "mudae_prefix": "$",                        // 💰  Mudae's command prefix (usually $)
        "min_kakera": 50,                           // 💎  Minimum kakera value to claim characters (0 to claim all)
        "key_mode": false                           // 🔑  Enable Key Mode? (true/false - for Kakera-focused rolling)
      },
      "KakeraHunterBot": {   // 🚀 Another awesome preset!
        "token": "YOUR_DISCORD_ACCOUNT_TOKEN_2",
        "prefix": "?",
        "channel_id": 987654321098765432,
        "roll_command": "wg",
        "delay_seconds": 1.5,
        "mudae_prefix": "$",
        "min_kakera": 75,
        "key_mode": true
      }
      // ... Add more presets for all your accounts! 🚀🚀🚀
    }
    ```

    **🔍  `presets.json` Settings - Explained in Detail:**

    *   **`preset_name`**:  A **descriptive name** for your preset (e.g., "MainAccount", "AltBot").  This helps you identify bots in the console.
    *   **`token`**: **YOUR DISCORD ACCOUNT TOKEN!**  This is **SUPER SECRET!**  See the "Usage" section below for how to get it. **NEVER SHARE YOUR TOKEN!** 🔒
    *   **`prefix`**:  The bot's command prefix.  You likely won't use this much, set it to anything (e.g., `!`, `?`, `.`).
    *   **`channel_id`**:  The **Discord Channel ID** where the bot will operate. **Enable Developer Mode in Discord** (Settings -> Advanced), then **right-click the channel and "Copy ID"**. 💬
    *   **`roll_command`**:  Your preferred **Mudae roll command** (e.g., `wa`, `wg`, `ha`, `hg`, `w`, `h`). 🎲
    *   **`delay_seconds`**:  **Delay in seconds** between bot actions. **Keep it above 0.8 for safety!**  🐢💨
    *   **`mudae_prefix`**:  The **Mudae bot's prefix** (usually `$`). 💰
    *   **`min_kakera`**:  **Minimum kakera value** for claiming characters. `0` to claim everything! 💎
    *   **`key_mode`**:  `true` or `false`. `true` for **Kakera Key Mode** - continuous kakera rolling even when claim rights are down! 🔑

4.  **🚀 Run the Bot!** Open your terminal/command prompt, navigate to the bot's folder, and type:

    ```bash
    python mudae_bot.py
    ```

5.  **🕹️ Interactive Menu - Choose Your Bots!**  The script starts and presents a menu!

    *   Use **↑ and ↓ arrow keys** to navigate.
    *   **"Select and Run Preset"**: Run **one** bot preset. Choose from your `presets.json`.
    *   **"Select and Run Multiple Presets"**: Run **multiple** bots at once! Use **spacebar to select/deselect** presets, then **Enter to confirm**. 👯‍♀️👯‍♂️
    *   **"Exit"**: Close the script. 👋

---

## 🎮  Time to Roll! Usage Instructions - Get Your Token! 🔑

1.  **🔑 Get Your Secret Discord Token:**

    *   **OPEN DISCORD IN YOUR WEB BROWSER!** (Chrome, Firefox, Safari, etc.)  **NOT THE DESKTOP APP!** 🌐
    *   **Press F12** to open **Developer Tools** (or right-click -> "Inspect"). 👨‍💻
    *   Go to the **"Console"** tab. 💻
    *   **Paste this JavaScript code into the console and press Enter:**

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
    console.log('%cWorked!', 'font-size: 50px');
    console.log(`%cYou now have your token in the clipboard!`, 'font-size: 16px');
    ```

    *   You'll see "%cWorked!" and "%cYou now have your token in the clipboard!". 🎉
    *   **Your Discord token is now copied!**  **PASTE IT into the `token` field in your `presets.json` file!** 📝

    **🔒  TOKEN SECURITY IS PARAMOUNT! 🔒  Treat your token like a SUPER SECRET PASSWORD!  DO NOT SHARE IT WITH ANYONE!  Sharing your token gives full access to your Discord account!** 🛡️

2.  **Configure `presets.json`:**  Fill in your `presets.json` file with tokens, channel IDs, roll commands, delays, etc.  See the "Installation" section for details. 📝

3.  **Run `mudae_bot.py`:**  Start the bot from your terminal. 🚀

4.  **Select Presets from Menu:** Use the interactive menu to choose which bot presets to run. 🕹️

5.  **👁️ Monitor the Console:**  Keep an eye on the console for real-time bot activity, logs, and claimed characters! 👀

6.  **📜 Logging:**  Bot activity is logged to the console output. Copy and paste for saving logs if needed. ✍️

---

## 🤝  Join the Community! Contributing is Welcome! 🤝

Want to make the Mudae Auto-Claim Bot even better?  Contributions are highly appreciated!  Got ideas, bug fixes, or new features?  Let's collaborate!

*   **🐞 Open Issues:** Report bugs, suggest features, discuss improvements!
*   **🛠️ Submit Pull Requests:**  Contribute code changes!  Please provide clear descriptions of your changes.

**🙏  Remember to use this bot responsibly and ethically.  Be aware of and respect Discord's Terms of Service. 🙏**

**Happy Mudae-ing!  (But be careful!)** 😉
