<p align="center">
  <img src="https://raw.githubusercontent.com/pyrogram/artwork/master/artwork/pyrogram-logo.png" alt="RNGram Logo" width="130">
</p>

<h1 align="center">⚡ RNGram</h1>

<p align="center">
  <b>Elegant, Modern, and Asynchronous Telegram MTProto API Framework in Python</b>
  <br>
  <i>Powered by Kurigram 2.2.26 core with built-in Pyromod, Rich Text Formatter, and Smart Keyboard Helpers.</i>
</p>

<p align="center">
  <a href="https://pypi.org/project/RNGram"><img src="https://img.shields.io/pypi/v/RNGram.svg?style=for-the-badge&color=blue" alt="PyPI Version"></a>
  <a href="https://pypi.org/project/RNGram"><img src="https://img.shields.io/pypi/pyversions/RNGram.svg?style=for-the-badge&color=3776AB" alt="Python Versions"></a>
  <a href="https://t.me/Renboyz"><img src="https://img.shields.io/badge/Telegram-Channel-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram Channel"></a>
  <a href="https://github.com/renzetx/RNGram/blob/main/COPYING.lesser"><img src="https://img.shields.io/badge/License-LGPLv3-green.svg?style=for-the-badge" alt="License"></a>
  <img src="https://img.shields.io/badge/MTProto-Layer%20229-orange?style=for-the-badge" alt="MTProto Layer 229">
</p>

---

## 🌟 Highlights

**RNGram** is a high-performance, asynchronous Telegram client framework based on **Kurigram 2.2.26** (MTProto Layer 229), crafted for both user accounts and bots. It bridges cutting-edge Telegram features with beloved developer extensions into a single, cohesive library.

* 🚀 **MTProto Layer 229**: Full access to modern Telegram features (Stars, Gifts, Paid Media, Stories, Business Connections, and Message Effects).
* 💬 **Built-in Pyromod**: Conversational flow (`listen()`, `ask()`, `wait_for_click()`) bound directly to `Message`, `Chat`, and `User`.
* 🎨 **Rich Message & Text Formatter**: Native helpers for Expandable Blockquotes, Spoilers, Custom Emojis, Formatted Timestamps (`tg-time`), and shorthand client formatting.
* ⌨️ **Smart Keyboards**: Intuitive `InlineKeyboard`, `ikb()`, and `btn()` builders with pagination and language flag presets.
* 🛡️ **Resource-Safe & Leak-Proof**: Bounded LRU caching, automatic listener lifecycle cleanup, and strong task reference tracking (`_create_tracked_task`).
* ⚡ **Hardware Accelerated**: Offloaded crypto tasks via `crypto_executor` and seamless C-extension support with `TgCrypto`.

---

## 📦 Installation

Install the latest stable release from PyPI:

```bash
pip install -U RNGram
```

For maximum performance with C-accelerated cryptographic routines:

```bash
pip install -U "RNGram[fast]"
```

> **Requirements:** Python 3.10 or higher.

---

## 🚀 Quick Start

### 1. Basic Echo Bot with Rich Text

```python
from pyrogram import Client, filters, enums

app = Client(
    "my_bot",
    api_id=12345,
    api_hash="0123456789abcdef0123456789abcdef",
    bot_token="123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11"
)

@app.on_message(filters.command("start") & filters.private)
async def start_handler(client: Client, message):
    # Use client formatter methods with expandable blockquote and custom emoji
    text = (
        f"{client.bold('Hello, ' + message.from_user.first_name)}! 👋\n\n"
        f"{client.expandable_blockquote('Welcome to RNGram! This is a collapsible blockquote supported in modern Telegram.')}\n\n"
        f"Server time: <tg-time unix='1720000000' format='r'>recently</tg-time>"
    )
    await message.reply_text(text, parse_mode=enums.ParseMode.HTML)

app.run()
```

---

### 2. Interactive Conversation (Pyromod)

Easily build multi-step question/answer prompts without messy state machines:

```python
@app.on_message(filters.command("survey") & filters.private)
async def survey_handler(client, message):
    # Ask a question and wait for the user's response
    name_msg = await message.chat.ask("What is your name?", timeout=60)
    
    # Ask the next question
    age_msg = await message.chat.ask(f"Nice to meet you {name_msg.text}! How old are you?", timeout=60)
    
    await message.reply(f"Profile saved! ✅\nName: {name_msg.text}\nAge: {age_msg.text}")
```

---

### 3. Smart Inline Keyboard (`ikb` & `btn`)

Build dynamic and clean inline keyboards effortlessly:

```python
from pyrogram.helpers import ikb, btn

@app.on_message(filters.command("menu"))
async def menu_handler(client, message):
    keyboard = ikb([
        [btn("🌐 Official Channel", "https://t.me/Renboyz", type="url")],
        [btn("Option 1", "opt_1"), btn("Option 2", "opt_2")],
        [btn("❌ Close", "close_menu")]
    ])
    
    await message.reply("Please choose an option:", reply_markup=keyboard)
```

---

### 4. Modern Telegram Features (Paid Media & Effects)

```python
from pyrogram.types import InputMediaPhoto

# Send paid media with Telegram Stars
await app.send_paid_media(
    chat_id=chat_id,
    stars_amount=15,
    media=[InputMediaPhoto("exclusive_content.jpg")],
    caption="Unlock this premium photo with Telegram Stars! ⭐"
)

# Send message with animated fullscreen effect
await app.send_message(
    chat_id=chat_id,
    text="Congratulations on your achievement! 🏆",
    effect_id=5104841245755180586  # Telegram flame/fireworks effect ID
)
```

---

## 📊 Feature Overview

| Capability | Standard Pyrogram | RNGram (v2.2.26) |
| :--- | :---: | :---: |
| **MTProto Layer** | Layer 158 (Legacy) | **Layer 229 (Modern)** |
| **Telegram Stars & Paid Media** | ❌ | ✅ |
| **Expandable Blockquotes & Time Tags** | ❌ | ✅ |
| **Message Effects (`effect_id`)** | ❌ | ✅ |
| **Invert Media (`show_caption_above_media`)** | ❌ | ✅ |
| **Interactive Listeners (`ask` / `listen`)** | Requires external plugin | **Built-in & Bounded** |
| **Text Formatter & Delimiters** | Manual string concatenation | **`client.bold()`, `ikb()`, etc.** |
| **Bounded Memory Caches (Anti-Leak)** | ❌ (Unbounded dicts) | **✅ (LRU with capacity)** |
| **Graceful Shutdown & Task Tracking** | ⚠️ Partial | **✅ Strong task references** |

---

## 💬 Community & Support

* 📢 **News & Updates:** [Telegram Channel (@Renboyz)](https://t.me/Renboyz)
* 🐞 **Issue Tracker:** [GitHub Issues](https://github.com/renzetx/RNGram/issues)
* 📖 **Upstream Reference:** [Kurigram Documentation](https://docs.pyrogram.org)

---

## 📜 License

**RNGram** is licensed under the terms of the **GNU Lesser General Public License v3.0 or later (LGPLv3+)**.  
See the [COPYING](COPYING) and [COPYING.lesser](COPYING.lesser) files for complete details.

<p align="center">
  Made with ❤️ by <b><a href="https://t.me/Renboyz">Renboys</a></b> and the Open Source Community.
</p>
