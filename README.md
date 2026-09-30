# Algoteer Noesis — Alpha 3

A futures trading journal and analytics workstation. This is an **alpha release** for a small group of testers. It is not a finished product, and your feedback is the reason it exists.

---

## What's new since Alpha 3.2

- **Price charts of your own sessions.** A new **Price Chart** tab draws the market for a session in one-minute detail, on a real time axis — a stretch with no trading is drawn as a gap, never squeezed out — with the session's opening and closing times marked, and holidays and early closes named.
- **Move around a session.** Drag, or scroll sideways, to pan; scroll up or down, or pinch on a Mac trackpad, to zoom where the pointer is. The price scale fits what is on screen (or freeze it to compare levels). A crosshair reads out each candle's open, high, low, close and volume. Choose 1, 2, 5, 15, 30 or 60-minute candles; a candle built from fewer minutes than its timeframe (a quiet stretch with missing minutes) is drawn faded and says so. **Previous trade / Selected trade / Next trade** jump between your trades, and clicking a fill selects its trade in the Journal too. **All stored sessions** lists every session with price history, traded or not; a session you traded that has no price history is listed and named rather than silently left out.
- **Your entries and exits on the chart.** Every fill is drawn where it happened, and each trade is joined from entry to exit, with its average entry and exit prices as lines. Select a trade in the Journal and it is drawn brighter. Noesis checks every fill against the market's range for that minute and says so if any fill falls outside it.
- **Reference levels.** The prior session's high, low and close, this session's high and low, and your own price marks — click the price axis, or type a price. A mark belongs to the product (every `/RTY` session, across contract rolls) and stays until you remove it.
- **Market recording (Schwab connection only).** While Noesis is running and connected, it records the index futures market (`/ES`, `/MES`, `/NQ`, `/RTY`, `/YM`) and keeps it on your machine. The Price Chart draws a session from this recording when the price-history fetch has none, and says which source it used. Each completed day of the recording is also copied to your backup folder.
- **Recording carries on with the window closed.** While the market recording is running, closing the window hides it instead of quitting, and recording continues. A small ring in the menu bar (on Windows, an icon by the clock) shows what the recorder is doing. Its menu has **Open Noesis** and **Quit Noesis (stops recording)**. On a Mac, clicking the Noesis icon in the Dock also brings the window back, and **⌘Q** quits. The first time you close the window, Noesis says once that it is still recording. Turn this off in **Settings → Keep Recording When the Window Is Closed**, and closing the window quits as before. Without a Schwab connection there is nothing to record, so closing the window quits.
- **Open Noesis when you log in (optional).** **Settings → Open Noesis When I Log In** starts Noesis, and with it the recorder, when you log in. It is **off** unless you turn it on. On a Mac, if macOS asks you to approve it, the setting says where: System Settings → General → Login Items.
- **Times in your own time zone.** Every time Noesis shows is in your computer's time zone, wherever you are, labelled ET, CT, MT or PT in the US. To use a fixed zone instead, choose it in **Settings → Time Zone**. Your journal itself still stores the times as Thinkorswim prints them (Eastern), so nothing about your trades changes when you travel.
- **Globex or regular hours — one meaning everywhere.** The **Globex (All) / RTH Only** switch now counts the same trades in every view: the Dashboard, the Calendar, the Journal, the Price Chart and the exported reports. Regular trading hours are **09:30–16:15 ET**, judged by when a trade was entered. Every view says which it is showing — a line beside the switch, a badge on the Calendar, an *Hours:* line in the copied Summary, and a heading on HTML and PDF reports — and Noesis remembers your choice for the next launch.
- **Trades sync as soon as Schwab reports them (Schwab connection only).** While the market recording is running, Noesis listens for Schwab's account activity, and each order or fill event starts the same sync as the Sync button — no need to sync by hand. When a sync adds something, the bottom of the window says so; if one fails, it says that too. Turn it off with `"sync_on_activity": false` in `config.json`.
- **The Calendar names the month of a spill-over day.** A week that straddles two months is drawn once, under the month that owns most of it. Its days from the other month now read *Sep 28*, *Nov 1* and so on, and their figures are dimmed, so they never look like part of the month they sit under.
- **Layout fixes.** On macOS 27 the title bar was see-through, showing whatever was behind the window; it is now solid. The toolbar row is centred in its bar, and the Calendar's header box grows to fit its contents instead of spilling the *GLOBEX · ALL HOURS* line below it.
- **Dashboard "By Time" for a single session** now draws one step per trade, at the moment it closed, on the session's own clock (18:00 ET the evening before to 17:00 ET, shown in your time zone).
- **Share from the Journal.** A **Share** button copies the trades the Journal is showing -- the date range and hours you chose -- to the clipboard as JSON, with a sound unless sound is turned off in Settings.
- **Failures are reported, not hidden.** If a Schwab sync, a campaign rebuild or the market recording cannot save what it received, Noesis says so instead of reporting success.
- **Looks like your platform.** Mac scroll bars and system font on macOS; Windows 11 scroll bars on Windows. Figures in the Calendar are never cut off in a narrow window.
- **The window tells you when it is waiting.** If reading the saved Schwab credentials takes more than a moment — on a Mac, usually because macOS is asking your permission — Noesis says it is waiting rather than appearing to hang.

Alpha 3.2 brought trade classification, the pre-trade plan, the optional Schwab connection, separate Live and Paper folders, the daily journal backup, and Copy Diagnostics. All of those are still here.

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

**Price charts come only from Schwab.** Without a connection, the Price Chart tab says *"No price history is stored yet"* — that is expected, not a fault. The rest of Noesis is unaffected.

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
- **Price charts need a Schwab connection** (see above).
- **Connect one computer to Schwab at a time.** Connecting a second computer to the same Schwab login ends the first one's connection: it stops syncing and recording until you connect it again in **Settings → Schwab Connection**. Schwab also asks you to connect again at least every seven days.
- **Charts can only be fetched for recent sessions.** Schwab serves one-minute history for roughly the last six to eight weeks, and **nothing at all for a futures contract once it has expired**. Each time it starts, Noesis fetches the recent sessions you traded and keeps them, so opening it on your trading days is what keeps your charts complete. An older session, or one on a contract that has since rolled, may never have a chart.
- **The holiday and early-close calendar covers equity-index futures in 2026.** Outside that, gaps are drawn but not explained.
- **A very full menu bar can hide the recording ring.** macOS drops menu-bar icons that do not fit, and menu-bar managers such as Ice or Bartender may park new icons out of sight. On a Mac, the Dock icon always brings the window back. On Windows, the icon may sit in the notification area's overflow (the **^** by the clock).
- **Planned stop and target are not drawn on the chart yet**, and nor are excursion measures (how far a trade went against you and for you). Both are planned.
