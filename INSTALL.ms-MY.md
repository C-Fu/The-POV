# INSTALL — Panduan Pemasangan (Windows & macOS)

Bahasa Melayu | [English](INSTALL.md) · Kembali ke [README](README.ms-MY.md)

Panduan langkah demi langkah untuk memasang lima alat yang digunakan dalam program **The POV — Develop with AI: From Problem to Working App** (Yayasan Peneraju).

| # | Alat | Kegunaan |
|---|------|----------|
| 1 | Node.js | Runtime JavaScript — `npm` dan `npx` turut disertakan |
| 2 | [OpenCode](https://opencode.ai) | Pembantu pengaturcaraan AI yang berjalan dalam terminal |
| 3 | [gsd-opencode](https://github.com/rokicool/gsd-opencode) | Add-on workflow GSD untuk OpenCode (slash commands) |
| 4 | [OpenChamber](https://github.com/openchamber/openchamber) | Ruang kerja web/desktop untuk OpenCode |
| 5 | [Tailscale](https://tailscale.com) | Rangkaian peribadi (tailnet) untuk mengakses komputer anda dari mana-mana |

Setiap seksyen berakhir dengan arahan semakan — jalankannya sebelum terus ke seksyen seterusnya.

---

## 1. Prasyarat: Node.js, npm, npx

`npm` dan `npx` disertakan **bersama** Node.js — memasang Node.js sahaja sudah memadai.

**Windows — pilih satu:**

Muat turun pemasang LTS dari <https://nodejs.org>, atau:

```powershell
winget install OpenJS.NodeJS.LTS
```

**macOS — pilih satu:**

Muat turun pemasang LTS dari <https://nodejs.org>, atau:

```bash
brew install node
```

**Semak** — setiap arahan harus memaparkan nombor versi:

```bash
node -v
npm -v
npx -v
```

---

## 2. OpenCode

<https://opencode.ai> — pembantu pengaturcaraan AI yang anda gunakan di dalam terminal.

**macOS — pilih satu:**

```bash
# Paling mudah (skrip pemasangan)
curl -fsSL https://opencode.ai/install | bash

# Tap Homebrew (digalakkan berbanding `brew install opencode` biasa — dikemas kini lebih kerap)
brew install anomalyco/tap/opencode

# Atau melalui npm
npm install -g opencode-ai
```

**Windows** — pembangunnya mengesyorkan WSL untuk pengalaman terbaik. Pilihan native (PowerShell):

```powershell
choco install opencode      # Chocolatey
scoop install opencode      # Scoop
npm install -g opencode-ai  # Atau melalui npm
```

**Penggunaan pertama kali:**

1. Buka terminal dalam folder projek dan jalankan:

```bash
opencode
```

2. Gunakan `/connect` di dalam OpenCode, kemudian log masuk di <https://opencode.ai/auth> (atau pembekal lain) dan tampal API key anda.
3. Jalankan `/init` dalam projek — ini mencipta fail `AGENTS.md` supaya pembantu AI memahami codebase anda.

---

## 3. gsd-opencode

<https://github.com/rokicool/gsd-opencode> — menambah workflow GSD (Get Shit Done) pada OpenCode: slash commands untuk merancang, melaksanakan, dan menyemak kerja.

**Pasang — paling mudah (berfungsi pada macOS, Windows, Linux):**

```bash
npx gsd-opencode
```

Atau sentiasa dapat keluaran terkini:

```bash
npx gsd-opencode@latest
```

**Atau pasang secara global:**

```bash
npm install gsd-opencode -g
gsd-opencode install
```

**Tanpa soalan (non-interactive):**

```bash
npx gsd-opencode --global   # memasang ke ~/.config/opencode/
npx gsd-opencode --local    # memasang ke .opencode/ (projek ini sahaja)
```

**Semak:**

1. **Mulakan semula OpenCode** selepas pemasangan, supaya slash commands baharu dimuatkan.
2. Di dalam OpenCode, jalankan:

```text
/gsd-help
```

**Kemas kini / nyahpasang:**

```bash
npx gsd-opencode@latest   # kemas kini (atau: gsd-opencode update)
gsd-opencode uninstall    # nyahpasang
```

**Digalakkan:** pilih tahap usaha penaakulan GSD dengan `/gsd-set-profile` (`simple`, `smart`, atau `genius`) — mulakan semula OpenCode selepas menukarnya.

---

## 4. OpenChamber

<https://github.com/openchamber/openchamber> — ruang kerja web/desktop untuk OpenCode, supaya anda boleh mengawalnya dari pelayar atau telefon dan bukannya terminal sahaja.

**Pilihan A — Aplikasi desktop (macOS / Windows / Linux):**

Muat turun dari <https://github.com/openchamber/openchamber/releases/latest>. Aplikasi desktop ini turut menyertakan OpenCode CLI yang sepadan, jadi tiada pemasangan OpenCode berasingan diperlukan.

**Pilihan B — CLI untuk Web/PWA (perlukan Node.js 22+):**

```bash
curl -fsSL https://raw.githubusercontent.com/openchamber/openchamber/main/scripts/install.sh | bash
```

**Jalankan:**

```bash
openchamber --ui-password be-creative-here
```

> **⚠ Utamakan keselamatan — SENTIASA lindungi OpenChamber dengan `--ui-password`.**
> Ia terikat kepada **localhost secara lalai**; gunakan `--lan` hanya pada **rangkaian yang dipercayai**.

**Arahan biasa:**

| Arahan | Kegunaan |
|--------|----------|
| `openchamber status` | Papar sama ada OpenChamber sedang berjalan |
| `openchamber connect-url --qr` | Papar URL sambungan berserta kod QR |
| `openchamber tunnel start --provider cloudflare --mode quick --qr` | Dedahkan UI melalui tunnel Cloudflare secara pantas |
| `openchamber startup enable` | Mulakan OpenChamber secara automatik semasa log masuk |
| `openchamber logs` | Papar log |
| `openchamber stop` | Hentikan OpenChamber |
| `openchamber update` | Kemas kini OpenChamber |

---

## 5. Tailscale

<https://tailscale.com> — mencipta rangkaian peribadi (**tailnet**) supaya anda boleh mengakses komputer anda — contohnya UI web OpenChamber — dari mana-mana, seolah-olah berada pada Wi-Fi yang sama.

**Windows:**

Muat turun pemasang dari <https://tailscale.com/download>, atau:

```powershell
winget install Tailscale.Tailscale
```

Kemudian log masuk dari system tray — pelayar anda akan terbuka untuk log masuk.

**macOS:**

Pasang aplikasi **"Tailscale"** dari App Store, atau:

```bash
brew install --cask tailscale
```

Kemudian log masuk dari menu bar — pelayar anda akan terbuka untuk log masuk.

**Konfigurasi admin console** — pergi ke <https://login.tailscale.com/admin> dan tetapkan perkara berikut (digalakkan untuk pemula):

1. **MagicDNS** — aktifkan (**Settings → DNS**) supaya peranti anda boleh berhubung antara satu sama lain menggunakan nama, bukan alamat IP.
2. **HTTPS certificates** — aktifkan (**Settings → DNS → HTTPS Certificates**) supaya `tailscale serve` boleh menyajikan HTTPS.
3. **Access controls (ACLs)** — polisi lalai allow-all memadai untuk tailnet peribadi; ketatkan kemudian.
4. **Key expiry** — di bawah **Settings → Keys** (atau tempoh pengesahan semula setiap peranti); lumpuhkan tamat tempoh untuk mesin anda sendiri yang sentiasa hidup, jika mahu.
5. **Device approval** — di bawah **Settings → Device management**, aktifkan kelulusan untuk peranti baharu (digalakkan).

**Kegunaan lazim dalam latihan ini:** pasang Tailscale pada PC yang menjalankan OpenChamber **dan** pada telefon/laptop anda — kemudian buka UI web OpenChamber dari mana-mana melalui tailnet.

**Sajikan aplikasi pada satu port:**

Apabila aplikasi anda berjalan pada port tempatan — contohnya `npm run dev` di `http://localhost:3000` — anda boleh kongsikannya dengan semua peranti dalam tailnet menggunakan `tailscale serve`:

```bash
# 1. Mulakan aplikasi anda (contoh: dev server pada port 3000)
npm run dev

# 2. Dalam terminal kedua, sajikan port tersebut melalui tailnet
tailscale serve --bg 3000
```

`serve` akan memaparkan URL — lebih kurang `https://<nama-mesin>.<tailnet>.ts.net` — bukanya pada telefon anda atau mana-mana peranti lain dalam tailnet. HTTPS adalah automatik (itulah sebabnya anda mengaktifkan sijil di atas), dan aplikasi kekal **peribadi**: hanya peranti yang log masuk ke tailnet anda boleh mengaksesnya.

**Urus apa yang sedang disajikan:**

```bash
tailscale serve status   # papar apa yang sedang disajikan (dan URLnya)
tailscale serve reset    # berhenti menyajikan dan kosongkan konfigurasi
```

> **Tip:** `serve` berkongsi hanya dalam tailnet anda sahaja. Untuk mendedahkan servis kepada internet awam, gunakan `tailscale funnel` — biasanya bukan yang anda perlukan untuk latihan ini.

**Arahan berguna:**

```bash
tailscale status             # lihat siapa berada dalam tailnet anda
tailscale ip                 # papar IP tailnet mesin ini
tailscale serve --bg <port>  # dedahkan servis tempatan melalui HTTPS dalam tailnet
```

---

## 6. Sahkan semuanya

Jalankan setiap arahan; semuanya harus berjaya sebelum anda terus ke panduan seterusnya.

| Alat | Arahan semakan |
|------|----------------|
| Node.js / npm / npx | `node -v` · `npm -v` · `npx -v` |
| OpenCode | `opencode --version` |
| gsd-opencode | `/gsd-help` (di dalam OpenCode) |
| OpenChamber | `openchamber status` |
| Tailscale | `tailscale status` |

**Seterusnya:** baca [GSD.md](GSD.md) untuk memahami workflow, atau [START.md](START.md) untuk menyiapkan idea anda dahulu. Kembali ke [README](README.ms-MY.md).
