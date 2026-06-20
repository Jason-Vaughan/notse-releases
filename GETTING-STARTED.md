# Getting Started with Notse

This guide takes you from zero to a working teleprompter: install Notse on your
operator Mac, install the helper on the Windows machine running PowerPoint, and
connect the two over your network.

If you just want to look around first, you don't need any of this — see
[Try the demo](#try-it-first-no-setup) below.

---

## How Notse fits together

Notse runs on **two machines**:

| Machine | What runs there | Role |
|---|---|---|
| **Your Mac** (operator) | The **Notse app** | The teleprompter you read from. Also the "remote control" for updates. |
| **The graphics PC** (Windows) | The **Notse helper** | Watches the live PowerPoint show and sends the speaker notes to your Mac. |

The two talk to each other over your **local network** (Wi-Fi or Ethernet) using
port **9816**. They do **not** need the internet to talk to each other — only the
same network. (A VPN like Tailscale is optional, for when the two machines aren't
on the same LAN — see [Connecting across networks](#connecting-across-networks).)

### What you'll need
- A **Mac** (Apple Silicon) for the operator side.
- A **Windows** PC running **PowerPoint** for the graphics side.
- Both on the **same network**.
- A **Notse license key** (a free Demo Mode is built in — no key needed to try it).

---

## Try it first (no setup)

Download the latest Mac build from the
[Releases page](https://github.com/Jason-Vaughan/notse-releases/releases) and open
it. Notse starts in **Demo Mode** — a self-contained tour running against sample
content. No PowerPoint, no helper, no network, no license required. When you're
ready for the real thing, continue below.

---

## Step 1 — Install the Notse app (Mac)

1. Download the latest **`Notse-<version>-arm64.dmg`** from the
   [Releases page](https://github.com/Jason-Vaughan/notse-releases/releases).
2. Open the `.dmg` and drag **Notse** into your **Applications** folder.
3. Launch Notse from Applications. The app is signed and notarized by Apple, so it
   opens without security warnings.

> **⚠️ The one thing people miss:** the first time Notse needs the network, macOS
> shows a **"Notse would like to find devices on your local network"** prompt.
> You **must click Allow.** If you deny it (or never see it), Notse can't reach
> your helper and the **Connect** button will look like it does nothing. You can
> fix this later under **System Settings → Privacy & Security → Local Network →
> Notse**.

---

## Step 2 — Install the Notse helper (Windows)

On the Windows machine that runs PowerPoint:

1. Download the latest **`NotseHelper-Setup-<version>.exe`** from the
   [Releases page](https://github.com/Jason-Vaughan/notse-releases/releases).
2. Double-click it. The installer is **per-user** — it does **not** need an
   administrator or a UAC prompt.
3. When Windows shows a **Firewall** prompt on first launch, **allow Notse on
   Private networks.** This opens port **9816** so your Mac can reach the helper.
4. A **Notse tray icon** appears near the clock. The helper **starts
   automatically** every time you log in — you don't need to launch it by hand.

That's it on Windows. Leave PowerPoint and the helper running during your show.

> **Tailscale / VPN users:** the automatic firewall rule covers ordinary LANs. On
> a tailnet you may need to add a manual firewall rule for port 9816. See
> [Connecting across networks](#connecting-across-networks).

---

## Step 3 — Connect the two

On a plain local network you do **not** need Tailscale or any VPN.

1. On the **Windows** machine, find its **IP address** (open Command Prompt and
   run `ipconfig` — use the IPv4 address on your active network, e.g.
   `192.168.1.10`).
2. On your **Mac**, open Notse's settings and find the **Connect** panel.
3. In the address box (placeholder `IP:Port (e.g. 192.168.1.10:9816)`), type the
   Windows machine's address followed by `:9816`, then click **Connect**.
4. The status indicator turns green when you're connected. Start your PowerPoint
   slideshow and the speaker notes appear on your Mac.

The default port is **9816** — you only need to change it if you deliberately ran
the helper on a different port.

### Connecting across networks
If the two machines aren't on the same LAN (e.g. a remote operator), put both on a
**[Tailscale](https://tailscale.com)** tailnet and use the machine's **tailnet IP**
in step 3 instead of its LAN IP. On a tailnet you may also need a manual Windows
Firewall rule allowing inbound TCP **9816**.

---

## Step 4 — Activate your license

Notse runs in Demo Mode until you activate.

1. In Notse, open **Settings → License**.
2. Enter your key in the **`XXXX-XXXX-XXXX-XXXX`** box and click **Activate**.

Licenses are **$50/year per machine** and include updates for the length of your
subscription. Need a key? **[Buy one at jasonvaughan.com/notse](https://jasonvaughan.com/notse/)**.

---

## How updates work

Notse updates are **operator-triggered from your Mac** — nothing installs itself
silently in the background.

- Open **Settings → License → Check for Updates** on your Mac.
- When a newer version is available, Notse walks you through updating the Mac app
  **and delivers the matching helper update to your Windows machine over your
  network** — so both halves move to the same version together, from one place.
- The Windows helper does **not** need its own internet connection; your Mac
  fetches the update and hands it to the helper over the LAN. If you're fully
  offline, you simply stay on your current version until the Mac is back online.
- Want early builds? **Settings → License → Beta updates** switches you to the
  beta track. Leave it off to stay on stable.

> **About "downgrades":** if a release ever has a problem, we don't ask you to
> roll back. We publish a **fixed, higher** version — just **Check for Updates**
> again and you move forward to the good build.

---

## If something goes wrong

**The Connect button seems to do nothing / won't connect**
1. Check the **macOS Local Network permission** (Step 1's warning) — this is the
   most common cause. System Settings → Privacy & Security → Local Network → Notse.
2. Confirm the **IP:Port** is right and both machines are on the same network.
3. Confirm the Windows **firewall** is allowing Notse on Private networks (port
   9816). Re-running the helper installer re-prompts if needed.

**Reinstalling or repairing the helper**
Just download and re-run the latest **`NotseHelper-Setup-<version>.exe`**. It's
per-user (no admin), closes any running helper first, and restores the tray icon
and auto-start. This is also the way to update a helper that's too out of date to
take an over-the-network update.

**Send us a diagnostic report**
In Notse, open **Settings → Diagnostics → Report…**. This opens a pre-filled email
to support with your app and helper versions, connection state, and a recent
event log already attached — just add what happened and send. You can review and
edit everything before it goes.

---

## More help
- **Found a bug?** [File an issue.](https://github.com/Jason-Vaughan/notse-releases/issues/new?template=bug_report.yml)
- **Have an idea or a question?** [Start a discussion.](https://github.com/Jason-Vaughan/notse-releases/discussions)
- **Full support overview:** [SUPPORT.md](SUPPORT.md)
- **Licensing or purchase:** [jasonvaughan.com](https://jasonvaughan.com)
