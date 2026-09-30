# INSTALL — Setup Guide (Windows & macOS)

English | [Bahasa Melayu](INSTALL.ms-MY.md) · Back to [README](README.md)

Step-by-step setup for the five tools used in **The POV — Develop with AI: From Problem to Working App** (Yayasan Peneraju).

| # | Tool | What it is |
|---|------|------------|
| 1 | Node.js | JavaScript runtime — `npm` and `npx` ship with it |
| 2 | [OpenCode](https://opencode.ai) | AI coding assistant that runs in your terminal |
| 3 | [gsd-opencode](https://github.com/rokicool/gsd-opencode) | GSD workflow add-on for OpenCode (slash commands) |
| 4 | [OpenChamber](https://github.com/openchamber/openchamber) | Web/desktop workspace for OpenCode |
| 5 | [Tailscale](https://tailscale.com) | Private network (tailnet) to reach your machine from anywhere |

Each section ends with a verify command — run it before moving to the next section.

---

## 1. Prerequisites: Node.js, npm, npx

`npm` and `npx` ship **with** Node.js — installing Node.js is enough.

**Windows — pick one:**

Download the LTS installer from <https://nodejs.org>, or:

```powershell
winget install OpenJS.NodeJS.LTS
```

**macOS — pick one:**

Download the LTS installer from <https://nodejs.org>, or:

```bash
brew install node
```

**Verify** — each command should print a version number:

```bash
node -v
npm -v
npx -v
```

---

## 2. OpenCode

<https://opencode.ai> — the AI coding assistant you use inside a terminal.

**macOS — pick one:**

```bash
# Easiest (install script)
curl -fsSL https://opencode.ai/install | bash

# Homebrew tap (recommended over plain `brew install opencode` — updated more frequently)
brew install anomalyco/tap/opencode

# Or via npm
npm install -g opencode-ai
```

**Windows** — upstream recommends WSL for the best experience. Native options (PowerShell):

```powershell
choco install opencode      # Chocolatey
scoop install opencode      # Scoop
npm install -g opencode-ai  # Or via npm
```

**First run:**

1. Open a terminal in a project folder and run:

```bash
opencode
```

2. Use `/connect` inside OpenCode, then sign in at <https://opencode.ai/auth> (or another provider) and paste your API key.
3. Run `/init` in the project — this creates an `AGENTS.md` file so the assistant understands your codebase.

---

## 3. gsd-opencode

<https://github.com/rokicool/gsd-opencode> — adds the GSD (Get Shit Done) workflow to OpenCode: slash commands for planning, executing, and verifying work.

**Install — easiest (works on macOS, Windows, Linux):**

```bash
npx gsd-opencode
```

Or always get the newest release:

```bash
npx gsd-opencode@latest
```

**Or install globally:**

```bash
npm install gsd-opencode -g
gsd-opencode install
```

**Non-interactive (no prompts):**

```bash
npx gsd-opencode --global   # installs to ~/.config/opencode/
npx gsd-opencode --local    # installs to .opencode/ (this project only)
```

**Verify:**

1. **Restart OpenCode** after installing, so the new slash commands load.
2. In OpenCode, run:

```text
/gsd-help
```

**Update / uninstall:**

```bash
npx gsd-opencode@latest   # update (or: gsd-opencode update)
gsd-opencode uninstall    # uninstall
```

**Recommended:** choose how much reasoning effort GSD uses with `/gsd-set-profile` (`simple`, `smart`, or `genius`) — restart OpenCode after changing it.

---

## 4. OpenChamber

<https://github.com/openchamber/openchamber> — a web/desktop workspace for OpenCode, so you can drive it from a browser or your phone instead of the raw terminal.

**Option A — Desktop app (macOS / Windows / Linux):**

Download from <https://github.com/openchamber/openchamber/releases/latest>. The desktop app bundles the matching OpenCode CLI, so no separate OpenCode install is needed.

**Option B — CLI for the Web/PWA (requires Node.js 22+):**

```bash
curl -fsSL https://raw.githubusercontent.com/openchamber/openchamber/main/scripts/install.sh | bash
```

**Run it:**

```bash
openchamber --ui-password be-creative-here
```

> **⚠ Safety first — ALWAYS protect OpenChamber with `--ui-password`.**
> It binds to **localhost by default**; only use `--lan` on **trusted networks**.

**Common commands:**

| Command | What it does |
|---------|--------------|
| `openchamber status` | Show whether OpenChamber is running |
| `openchamber connect-url --qr` | Print the connect URL with a QR code |
| `openchamber tunnel start --provider cloudflare --mode quick --qr` | Expose the UI through a quick Cloudflare tunnel |
| `openchamber startup enable` | Start OpenChamber automatically at login |
| `openchamber logs` | Show logs |
| `openchamber stop` | Stop OpenChamber |
| `openchamber update` | Update OpenChamber |

---

## 5. Tailscale

<https://tailscale.com> — creates a private network (a **tailnet**) so you can reach your machine — for example the OpenChamber web UI — from anywhere, as if you were on the same Wi-Fi.

**Windows:**

Download the installer from <https://tailscale.com/download>, or:

```powershell
winget install Tailscale.Tailscale
```

Then log in from the system tray — your browser opens for sign-in.

**macOS:**

Install the **"Tailscale"** app from the App Store, or:

```bash
brew install --cask tailscale
```

Then log in from the menu bar — your browser opens for sign-in.

**Admin console configuration** — go to <https://login.tailscale.com/admin> and set these up (recommended for beginners):

1. **MagicDNS** — enable it (**Settings → DNS**) so your devices can reach each other by name instead of IP address.
2. **HTTPS certificates** — enable (**Settings → DNS → HTTPS Certificates**) so `tailscale serve` can serve HTTPS.
3. **Access controls (ACLs)** — the default allow-all policy is fine for a personal tailnet; tighten it later.
4. **Key expiry** — under **Settings → Keys** (or per-device re-authentication period); disable expiry for your own always-on machine if you like.
5. **Device approval** — under **Settings → Device management**, turn on approval for new devices (recommended).

**Typical use in this training:** install Tailscale on the PC running OpenChamber **and** on your phone/laptop — then open the OpenChamber web UI from anywhere via the tailnet.

**Serve an app on a port:**

When your app is running on a local port — for example `npm run dev` on `http://localhost:3000` — you can share it with every device on your tailnet using `tailscale serve`:

```bash
# 1. Start your app (example: dev server on port 3000)
npm run dev

# 2. In a second terminal, serve that port over the tailnet
tailscale serve --bg 3000
```

`serve` prints the URL — something like `https://<machine-name>.<tailnet>.ts.net` — open it on your phone or any other device on the tailnet. HTTPS is automatic (that's why you enabled certificates above), and the app stays **private**: only devices signed in to your tailnet can reach it.

**Manage what's being served:**

```bash
tailscale serve status   # show what is being served (and the URL)
tailscale serve reset    # stop serving and clear the config
```

> **Tip:** `serve` shares only within your tailnet. To expose a service to the public internet you would use `tailscale funnel` instead — usually not what you want for this training.

**Handy commands:**

```bash
tailscale status             # see who is on your tailnet
tailscale ip                 # show this machine's tailnet IP
tailscale serve --bg <port>  # expose a local service over HTTPS on the tailnet
```

---

## 6. Verify everything

Run each command; everything should succeed before you continue to the guides.

| Tool | Verify command |
|------|----------------|
| Node.js / npm / npx | `node -v` · `npm -v` · `npx -v` |
| OpenCode | `opencode --version` |
| gsd-opencode | `/gsd-help` (inside OpenCode) |
| OpenChamber | `openchamber status` |
| Tailscale | `tailscale status` |

**Next:** read [GSD.md](GSD.md) to learn the workflow, or [START.md](START.md) to prepare your idea first. Back to [README](README.md).
