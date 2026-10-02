<p align="center">
  <img src="https://raw.githubusercontent.com/pyrogram/artwork/master/artwork/pyrogram-logo.png" alt="RNGram Logo" width="125">
</p>

<h1 align="center">
  <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/High%20Voltage.png" alt="Zap" width="38" height="38" style="vertical-align: middle;">
  RNGram
  <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/High%20Voltage.png" alt="Zap" width="38" height="38" style="vertical-align: middle;">
</h1>

<p align="center">
  <a href="https://github.com/renzetx/RNGram">
    <img src="https://readme-typing-svg.demolab.com?font=Outfit&weight=600&size=20&duration=2500&pause=800&color=2CA5E0&center=true&vCenter=true&width=620&lines=%E2%9A%A1+Modern+Telegram+MTProto+Framework+in+Python;%F0%9F%9A%80+Full+MTProto+Layer+229+Support;%F0%9F%92%AC+Built-in+Pyromod+Conversation+Flow;%F0%9F%8E%A8+Rich+Message%2C+Quotes%2C+and+Effects;%F0%9F%9B%A1%EF%B8%8F+Leak-Proof+LRU+Memory+%26+Task+Safety" alt="Typing Animation" />
  </a>
</p>

<p align="center">
  <a href="https://pypi.org/project/RNGram"><img src="https://img.shields.io/pypi/v/RNGram.svg?style=for-the-badge&color=2CA5E0&logo=pypi&logoColor=white" alt="PyPI Version"></a>
  <a href="https://pypi.org/project/RNGram"><img src="https://img.shields.io/pypi/pyversions/RNGram.svg?style=for-the-badge&color=3776AB&logo=python&logoColor=white" alt="Python Versions"></a>
  <a href="https://t.me/Renboyz"><img src="https://img.shields.io/badge/Telegram-Channel-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram Channel"></a>
  <a href="https://github.com/renzetx/RNGram/blob/main/COPYING.lesser"><img src="https://img.shields.io/badge/License-LGPLv3-2ea44f.svg?style=for-the-badge" alt="License"></a>
  <a href="#"><img src="https://img.shields.io/badge/MTProto-Layer%20229-ff69b4?style=for-the-badge&logo=telegram" alt="MTProto Layer 229"></a>
</p>

---

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/Glowing%20Star.png" alt="Star" width="30" height="30" style="vertical-align: middle;"> Mengapa Memilih RNGram?

**RNGram** adalah framework Telegram MTProto API asinkron berperforma tinggi berbasis **Pyrogram (MTProto Layer 229)** yang dirancang untuk kebutuhan bot modern, userbot, dan aplikasi berskala besar.

RNGram menggabungkan ekosistem protokol Telegram terkini dengan ekstensi pengembang terbaik langsung di dalam satu pustaka siap pakai tanpa dependensi eksternal yang rumit.

<table>
  <tr>
    <td width="50%">
      <h3><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/Rocket.png" width="24" height="24" style="vertical-align: middle;"> MTProto Layer 229</h3>
      <p>Dukungan penuh fitur Telegram modern: Telegram Stars, Gifts, Paid Media, Stories, Business Connection, dan Message Effects.</p>
    </td>
    <td width="50%">
      <h3><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Smilies/Speech%20Balloon.png" width="24" height="24" style="vertical-align: middle;"> Percakapan Interaktif (Pyromod)</h3>
      <p>Bangun interaksi tanya-jawab dengan <code>listen()</code>, <code>ask()</code>, dan <code>wait_for_click()</code> yang terpasang langsung pada objek Message, Chat, dan User.</p>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h3><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Activities/Sparkles.png" width="24" height="24" style="vertical-align: middle;"> Rich Text & Formatting</h3>
      <p>Kutipan yang bisa diciutkan (<i>Expandable Blockquotes</i>), Custom Emojis, Spoilers, dan timestamp dinamis (<code>&lt;tg-time&gt;</code>).</p>
    </td>
    <td width="50%">
      <h3><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Shield.png" width="24" height="24" style="vertical-align: middle;"> Resource-Safe & Anti-Leak</h3>
      <p>Manajemen RAM aman dengan Bounded LRU Cache, pembersihan otomatis listener, dan pelacakan <i>strong reference</i> asyncio tasks.</p>
    </td>
  </tr>
</table>

---

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Package.png" alt="Package" width="30" height="30" style="vertical-align: middle;"> Instalasi

Instal versi rilis stabil dari PyPI:

```bash
pip install -U RNGram
```

Untuk performa maksimal dengan akselerasi kriptografi C (*recommended*):

```bash
pip install -U "RNGram[fast]"
```

> [!TIP]
> **Persyaratan Sistem:** Python 3.10 atau versi yang lebih baru (mendukung penuh Python 3.10, 3.11, 3.12, 3.13, hingga 3.14).

---

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Smilies/Robot.png" alt="Robot" width="30" height="30" style="vertical-align: middle;"> Panduan Cepat (Quick Start)

### 1. Bot Sederhana dengan Rich Text Formatting

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
    text = (
        f"{client.bold('Halo, ' + message.from_user.first_name)}! 👋\n\n"
        f"{client.expandable_blockquote('Ini adalah kutipan panjang yang bisa dibuka dan ditutup di aplikasi Telegram modern!')}\n\n"
        f"Waktu server: <tg-time unix='1720000000' format='r'>baru saja</tg-time>"
    )
    await message.reply_text(text, parse_mode=enums.ParseMode.HTML)

app.run()
```

---

### 2. Alur Percakapan Interaktif (Pyromod)

Buat dialog formulir tanpa memerlukan state machine yang rumit:

```python
@app.on_message(filters.command("daftar") & filters.private)
async def register_dialog(client, message):
    # Ajukan pertanyaan dan tunggu respons dari user
    nama = await message.chat.ask("Siapa nama lengkap Anda?", timeout=60)
    
    # Ajukan pertanyaan berikutnya
    umur = await message.chat.ask(f"Senang berkenalan denganmu, {nama.text}! Berapa usia Anda?", timeout=60)
    
    await message.reply(
        f"✅ Data berhasil disimpan!\n"
        f"• Nama: {nama.text}\n"
        f"• Usia: {umur.text}"
    )
```

---

### 3. Smart Keyboards (`ikb` & `btn`)

Menyusun tombol *inline keyboard* menjadi ringkas dan elegan:

```python
from pyrogram.helpers import ikb, btn

@app.on_message(filters.command("menu"))
async def menu_handler(client, message):
    keyboard = ikb([
        [btn("📢 Saluran Resmi", "https://t.me/RNMarkets", type="url")],
        [btn("⚡ Fitur 1", "f1"), btn("🚀 Fitur 2", "f2")],
        [btn("❌ Tutup Menu", "close_menu")]
    ])
    
    await message.reply("Silakan pilih menu di bawah ini:", reply_markup=keyboard)
```

---

### 4. Fitur Telegram Modern (Paid Media & Efek Animasi Pesan)

```python
from pyrogram.types import InputMediaPhoto

# Mengirim media berbayar menggunakan Telegram Stars
await app.send_paid_media(
    chat_id=chat_id,
    stars_amount=15,
    media=[InputMediaPhoto("konten_eksklusif.jpg")],
    caption="Buka foto eksklusif ini menggunakan 15 Telegram Stars! ⭐"
)

# Mengirim pesan dengan efek animasi layar penuh (Flame / Fireworks)
await app.send_message(
    chat_id=chat_id,
    text="Selamat atas pencapaian Anda! 🎉",
    effect_id=5104841245755180586  # ID Efek animasi resmi Telegram
)
```

---

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Gem%20Stone.png" alt="Gem" width="28" height="28" style="vertical-align: middle;"> Matriks Perbandingan Fitur

| Fitur & Kapabilitas | Pyrogram Biasa | Kurigram Standar | **RNGram (v2.2.26)** |
| :--- | :---: | :---: | :---: |
| **MTProto Layer** | Layer 158 (Lama) | Layer 229 | **Layer 229 (Terbaru)** |
| **Telegram Stars & Paid Media** | ❌ | ✅ | **✅ (Lengkap)** |
| **Expandable Blockquote & Time Tags** | ❌ | ✅ | **✅ (Lengkap)** |
| **Message Effects (`effect_id`)** | ❌ | ✅ | **✅ (Lengkap)** |
| **Caption di Atas Media (`show_caption_above_media`)** | ❌ | ✅ | **✅ (Lengkap)** |
| **Built-in Pyromod (`ask` / `listen`)** | ❌ Butuh plugin luar | ❌ Tidak ada | **✅ (Terintegrasi)** |
| **Text Formatter Helper (`client.bold()`)** | ❌ | ❌ | **✅ (Terintegrasi)** |
| **Smart Keyboard (`ikb`, `btn`, `bki`)** | ❌ | ❌ | **✅ (Terintegrasi)** |
| **Manajemen Memori Bounded LRU Cache** | ❌ Memory Leak | ✅ | **✅ (Stabil & Leak-Proof)** |
| **Tracked Asyncio Tasks (`_create_tracked_task`)** | ❌ Rentan GC | ✅ | **✅ (Anti-Crash)** |

---

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Activities/Party%20Popper.png" alt="Party" width="30" height="30" style="vertical-align: middle;"> Komunitas & Dukungan

* 📢 **Saluran Pembaruan:** [Telegram Owner](https://t.me/Renboyz)
* 💬 **Channel Update:** [Channel Update](https://t.me/RNMarkets)
* 🐛 **Laporan Kendala:** [GitHub Issues](https://github.com/renzetx/RNGram/issues)
* 📖 **Referensi Dokumentasi:** [Dokumentasi](https://docs.pyrogram.org)

---

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Locked%20with%20Key.png" alt="License" width="28" height="28" style="vertical-align: middle;"> Lisensi

**RNGram** dilisensikan di bawah ketentuan **GNU Lesser General Public License v3.0 or later (LGPLv3+)**.  
Rincian lengkap dapat dibaca pada berkas [COPYING](COPYING) dan [COPYING.lesser](COPYING.lesser).

<br>

<p align="center">
  Dikembangkan oleh <b><a href="https://t.me/Renboyz">Renboys</a></b> bersama Komunitas Open Source. <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Smilies/Heart%20on%20Fire.png" alt="Heart on fire" width="22" height="22" style="vertical-align: middle;">
</p>
