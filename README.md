# Algoteer Noesis — Alpha 3.2

A futures trading journal and analytics workstation. This is an **alpha release** for a small group of testers. It is not a finished product, and your feedback is the reason it exists.

---

## What's new since Alpha 2

- **Trade classification.** Record how each trade was *taken* — separately from whether it made money — so a trade that broke your rules and won anyway is visible instead of forgotten.
- **A pre-trade plan.** Three optional numbers — planned stop, target and size — recorded before the position closes. This is what lets Noesis measure results in R.
- **Schwab connection (optional, read-only).** Noesis can fetch your executions directly from a Schwab account, alongside the CSV statements it already reads. It cannot place orders — there is no code in Noesis that can. See *Connecting to Schwab* below; most testers can ignore this entirely.
- **Separate Live and Paper statement folders**, so a paper export can no longer overwrite a live one before Noesis has read it.
- **A daily backup of your journal**, seven days kept.
- **Copy Diagnostics**, in Settings. If something goes wrong, this copies a report you can paste into an email. It contains no account numbers, passwords or tokens.

---

## Before you start: you need a license key

Noesis will not run without one. Email **stevej@algoteer.com** with your name and you'll be sent a license token. Keys are issued individually, so please don't share yours.

---

## Which file do I download?

### Windows

| Your machine | Download |
|---|---|
| Almost everyone | **`Algoteer_Noesis_x64.msi`** |
| Windows on Arm (Snapdragon, Surface Pro X / 11 Arm) | `Algoteer_Noesis_arm64.msi` |

**If you're not sure, choose `x64`.** To check: **Settings → System → About**, and read the **System type** line. It will say either "x64-based processor" or "ARM-based processor."

Installing the wrong one won't damage anything — it simply won't run.

### macOS

Download **`Algoteer_Noesis.dmg`**.

**Apple Silicon only** — an M1, M2, M3, or M4 Mac. Intel Macs are not supported in this alpha. To check: **Apple menu → About This Mac**. If it says **Chip: Apple M-something**, you're fine. If it says **Processor: Intel**, this release won't run on your machine.

---

## Installing on Windows

1. Download the `.msi` and double-click it.

2. **You will see a blue warning screen** that says *"Windows protected your PC — Microsoft Defender SmartScreen prevented an unrecognized app from starting."* This is expected. It appears because the installer isn't code-signed yet, not because anything is wrong with it.

   Click **More info**, then click the **Run anyway** button that appears underneath. The button is hidden until you click More info.

3. The installer adds Algoteer Noesis to your Start Menu and puts a shortcut on your desktop.

---

## Installing on macOS

1. Open the `.dmg` and drag **Algoteer Noesis** into your **Applications** folder.

2. **The first launch will be blocked.** macOS will say it cannot verify the developer. This is expected, for the same reason as the Windows warning — the app isn't notarized with Apple yet.

3. To allow it:
   - Try to open the app once and let it be refused.
   - Open **System Settings → Privacy & Security**.
   - Scroll down to the **Security** section. You'll see a line about Algoteer Noesis being blocked.
   - Click **Open Anyway**, then confirm.

   > **Note:** if you search the web for this, you'll be told to right-click the app and choose Open. **That no longer works** — Apple removed it in macOS Sequoia. Use System Settings as described above.

4. On first run, macOS will ask for permission to access your **Documents** folder. Click **Allow** — this is where Noesis reads statements from and writes reports to.

---

## Activating your license

On first launch, Noesis shows a small dialog headed **ALGOTEER NOESIS — ALPHA PREVIEW**, with a field labeled **LICENSE KEY OR TOKEN**.

Paste your token into that field and click **Activate Workstation**.

Your token is a single long run of letters and digits, possibly ending in one or two `=` characters. Paste in **all** of it, as one line, with no spaces or line breaks. The most common mistake is a partial copy — if your email client wrapped the token across several lines, make sure you've selected every one of them.

You only do this once. The token is saved and read automatically on every later launch. If something is wrong with it, the dialog tells you so in red underneath the field.

---

## Where Noesis keeps things

**Your documents** (both platforms), under your **Documents** folder:

```
Documents/Algoteer/Noesis/Account Statements/Live/    ← live-account CSV exports
Documents/Algoteer/Noesis/Account Statements/Paper/   ← paper-trading CSV exports
Documents/Algoteer/Noesis/Reports/                    ← exported reports land here
```

Files placed directly in `Account Statements/` are still read. Whichever folder a statement is in, Noesis reads the account type from the file itself.

**Its database:**

- Windows — `%LOCALAPPDATA%\Algoteer\Noesis\data\noesis.db`
- macOS — `~/Library/Application Support/Algoteer/Noesis/data/noesis.db`

**Its log**, which Settings → Diagnostics → Open Log Folder opens for you:

- Windows — `%LOCALAPPDATA%\Algoteer\Noesis\data\logs\`
- macOS — `~/Library/Application Support/Algoteer/Noesis/data/logs/`

**Your license token:**

- Windows — `%APPDATA%\Noesis\license.token`
- macOS — `~/Library/Application Support/Noesis/license.token`

---

## What Noesis sends over the network

On startup, Noesis sends a short message to Algoteer's server recording your license identifier (a random code, not your name), the app's build identifier, and your operating system and processor type. Nothing else is sent to Algoteer — your trades, statements, and account data stay entirely local and are never transmitted to us.

If you connect a Schwab account, Noesis also talks **directly to Schwab**, using credentials stored in your operating system's keychain (macOS Keychain, Windows Credential Manager). That traffic goes between your machine and Schwab only; none of it passes through Algoteer.

---

## Connecting to Schwab (optional)

Most testers should skip this. Noesis works exactly as before from CSV statements, and those remain the authoritative source in this release.

Connecting requires your **own** registered application at `developer.schwab.com`, which gives you a client ID and secret to enter in **Settings → Schwab Connection**. Schwab approves these individually and it can take several days. Without one, the Schwab buttons have nothing to connect with — that is expected, not a fault.

---

## Uninstalling

- **Windows** — Settings → Apps → Installed apps → Algoteer Noesis → Uninstall.
- **macOS** — drag Algoteer Noesis from Applications to the Trash.

Your data folders and database are deliberately left behind so that reinstalling doesn't lose your history. Delete them by hand if you want a clean slate.

---

## Reporting a problem

This is what the alpha is for, so please do. The more of this you can include, the faster it gets fixed:

- Your operating system and version, and which installer you used.
- What you were doing when it went wrong.
- What you expected to happen, and what actually happened.
- A screenshot, if there's anything to see.

---

## Known limitations in this alpha

- **Installers are not code-signed.** Hence the warnings above. Signing is in progress and these will disappear in a future build.
- **macOS is Apple Silicon only.** No Intel build.
- **Schwab syncing needs your own Schwab developer registration.** See above. CSV statements remain the primary source.
- **No price charts yet.** Charts of the market with your entries and exits drawn on them are the next release.
