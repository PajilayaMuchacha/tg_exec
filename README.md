# 🧰 tg-exec (Go)

**tg-exec** - a lightweight CLI tool that runs any command and sends a Telegram notification when it finishes.

<details open>
<summary>🇬🇧 English</summary>

## ✨ Features

- 🕐 Report completion of any shell command
- 💬 Send Telegram message on success or failure
- 📄 Include command output (only on failure, or always if configured)
- ⚙️ Support both global and per-user configuration
- 🌍 Use system timezone (or custom via `TIMEZONE` / `TG_EXEC_TZ`)
- 🔁 Retry and exponential backoff if Telegram API fails
- 🧩 Simple `.conf` configuration format
- 🧑‍💻 Optional debug mode (`DEBUG=1`)
- 🔒 Free for personal and internal use (CC BY-NC 4.0)

---

## 🧱 Installation

### From `.deb` package
```bash
sudo dpkg -i tg-exec_*_amd64.deb
```

### Manual build
```bash
sudo apt install golang-go
git clone https://github.com/WithoutCowards/tg-exec.git
cd tg-exec
GO111MODULE=on CGO_ENABLED=0 go build -ldflags "-s -w" -o /usr/local/bin/tg-exec ./cmd/tg-exec
```

---

## ⚙️ Configuration

Global config: `/etc/tg-exec/config.conf`  
User override: `~/.config/tg-exec/config.conf` (has higher priority)

```ini
# Telegram bot credentials
TOKEN=""            # Required. Bot token from BotFather
CHAT_ID=""          # Required. Chat ID (negative for groups)

# General settings
NOTE="$(hostname)"             # Optional. Adds server name or custom note
ALWAYS="1"                     # 1 = always send, 0 = only on failure
PARSE_MODE="HTML"              # HTML or MarkdownV2
TIMEZONE=""                    # e.g. Europe/Moscow
DEBUG="0"

# Telegram API behavior
TG_EXEC_HTTP_TIMEOUT="10"      # HTTP timeout (seconds)
TG_EXEC_RETRIES="3"            # Retry count
TG_EXEC_BACKOFF="2"            # Seconds between retries (doubles each time)

# Behavior flags
TG_EXEC_STRICT="0"             # 1 = exit with error if send fails
```

---

## 🧠 Environment Variables

| Variable | Description                                     | Default |
|-----------|-------------------------------------------------|----------|
| `TELEGRAM_BOT_TOKEN` | Bot token                                       | - |
| `TELEGRAM_CHAT_ID` | Chat ID (e.g. `-123456`)                        | - |
| `TG_NOTE` | Custom note (hostname or alias)                 | hostname |
| `TG_EXEC_ALWAYS` | Always send message (1 = yes, 0 = only on fail) | 1 |
| `TG_EXEC_PARSE_MODE` | Telegram parse mode                             | HTML |
| `TG_EXEC_HTTP_TIMEOUT` | API request timeout                             | 10 |
| `TG_EXEC_RETRIES` | Retry attempts                                  | 3 |
| `TG_EXEC_BACKOFF` | Backoff interval (sec)                          | 2 |
| `TG_EXEC_STRICT` | Exit on send failure                            | 0 |
| `TG_EXEC_TZ` | Custom timezone                                 | system |
| `DEBUG` | Enable debug logs                               | 0 |

---

## 🧪 Usage

```bash
DEBUG=1 tg-exec "echo hello"
```

**Example Telegram message:**
```
✅ Command completed successfully
Command:
echo hello
Note: myserver.local
Start time: 2025-01-01 00:21:01 +00
End time: 2025-01-01 00:21:01 +00
Duration: 0 sec.
Exit code: 0
Output:
hello
```

**Behavior matrix:**

| ALWAYS | Telegram message | Output included |
|:-------:|:-----------------|:----------------|
| `1` | Always | Yes |
| `0` | Only on failure | Yes (only on error) |

---

## 🧩 Example Integrations

**With environment override:**
```bash
TELEGRAM_BOT_TOKEN="..." TELEGRAM_CHAT_ID="-123456" tg-exec "uptime"
```

---

## 🧱 Debian Packaging

To build from source:

```bash
sudo apt install -y debhelper devscripts golang-any
dpkg-buildpackage -us -uc
```

Result:
```
../tg-exec_*_amd64.deb
```

---

## 🐛 Debug Mode

To enable verbose logging:

```bash
DEBUG=1 tg-exec "echo test"
```

Example debug output:
```
[DEBUG] Loaded config keys: map[TOKEN:... CHAT_ID:... ALWAYS:1]
[DEBUG] Sending Telegram message to <CHAT_ID>
[DEBUG] Telegram message sent successfully.
```

---

## 📜 License

**License:** CC BY-NC 4.0

---

</details>

---

<details>
<summary>🇷🇺 Русская версия</summary>

## ✨ Возможности
- 🕐 Отправляет уведомления о завершении любой команды
- 💬 Сообщение в Telegram при успехе или ошибке
- 📄 Вывод команды включается при ошибке (или всегда, если указано)
- ⚙️ Поддерживает глобальные и пользовательские конфиги
- 🌍 Использует системный часовой пояс
- 🔁 Повторные попытки при ошибках Telegram API
- 🧩 Удобный формат конфигурации `.conf`
- 🧑‍💻 Режим отладки (`DEBUG=1`)
- 🔒 Бесплатно для личного и внутреннего использования

---

## ⚙️ Установка

### Через `.deb` пакет
```bash
sudo dpkg -i tg-exec_*_amd64.deb
```

### Ручная сборка
```bash
sudo apt install golang-go
git clone https://github.com/WithoutCowards/tg-exec.git
cd tg-exec
GO111MODULE=on CGO_ENABLED=0 go build -ldflags "-s -w" -o /usr/local/bin/tg-exec ./cmd/tg-exec
```

---

## 📦 Конфигурация

Глобальный файл: `/etc/tg-exec/config.conf`  
Пользовательский: `~/.config/tg-exec/config.conf`

```ini
TOKEN=""            
CHAT_ID=""

NOTE="$(hostname)"
ALWAYS="1"
PARSE_MODE="HTML"
TIMEZONE=""
DEBUG="0"

TG_EXEC_HTTP_TIMEOUT="10"
TG_EXEC_RETRIES="3"
TG_EXEC_BACKOFF="2"

TG_EXEC_STRICT="0"
```

---

## 🧠 Переменные окружения

| Переменная | Описание | По умолчанию |
|-------------|-----------|--------------|
| `TELEGRAM_BOT_TOKEN` | Токен бота | - |
| `TELEGRAM_CHAT_ID` | ID чата | - |
| `TG_NOTE` | Имя сервера или заметка | hostname |
| `TG_EXEC_ALWAYS` | Отправлять всегда / только при ошибке | 1 |
| `TG_EXEC_PARSE_MODE` | Формат сообщения | HTML |
| `TG_EXEC_HTTP_TIMEOUT` | Таймаут (сек) | 10 |
| `TG_EXEC_RETRIES` | Повторы | 3 |
| `TG_EXEC_BACKOFF` | Интервал между повторами | 2 |
| `TG_EXEC_STRICT` | Завершать при ошибке отправки | 0 |
| `TG_EXEC_TZ` | Часовой пояс | системный |
| `DEBUG` | Включить отладку | 0 |

---

## 🧪 Использование

```bash
tg-exec "systemctl restart nginx"
```

Пример сообщения:
```
✅ Команда выполнена успешно
Команда:
systemctl restart nginx
Note: prod-web01
Время старта: 2025-01-01 00:25:00 +00
Время окончания: 2025-01-01 00:25:02 +00
Длительность: 2 сек.
Код возврата: 0
```

Режим отладки:
```bash
DEBUG=1 tg-exec "echo test"
```

---

## 🧱 Сборка Debian пакета

```bash
sudo apt install -y debhelper devscripts golang-any
dpkg-buildpackage -us -uc
```

Результат:
```
../tg-exec_*_amd64.deb
```

---

## 📜 Лицензия

**Лицензия:** CC BY-NC 4.0

---

</details>