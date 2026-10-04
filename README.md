# Semaphore Link

**Free Windows companion app for the MetaTrader 5 utility "Signal Copier Semaphore – Telegram to MT5".**

Semaphore Link reads the Telegram channels you choose with **your own Telegram account**, recognises trading signals and follow-up messages, and hands them to the Semaphore EA in MetaTrader 5 through files in the MT5 *Common* folder. The EA sizes and executes the trades with your risk settings.

Semaphore Link is an **unofficial Telegram client** and is not affiliated with Telegram. It only reads; it never sends a message.

## Download

Get the latest version from **[Releases](../../releases/latest)**:

- `SemaphoreLink-<version>-win-x64.exe` – the app (single file, no installer)
- `SHA256SUMS.txt` – checksum to verify the download

### Verify the download (recommended)

In PowerShell, in your Downloads folder:

```powershell
Get-FileHash .\SemaphoreLink-1.0.0-win-x64.exe -Algorithm SHA256
```

The hash must match the line in `SHA256SUMS.txt` (and the value in the Semaphore blog post on MQL5).

### "Windows protected your PC"

The app is not code-signed yet, so Windows SmartScreen may warn on the first start. After verifying the checksum, click **More info → Run anyway**.

## Requirements

- Windows 10/11 or Windows Server 2016+ (64-bit), PC or VPS
- MetaTrader 5 with the Semaphore EA, on the **same** computer and Windows user
- A Telegram account and your own API key (api_id / api_hash) from [my.telegram.org](https://my.telegram.org) → *API development tools*
- Edge, Chrome or Firefox (Internet Explorer is not supported)

The MQL5 VPS rented inside the terminal is **not** enough – Semaphore Link has to run next to the terminal on a full Windows machine or Windows VPS.

## First start

1. Start `SemaphoreLink-1.0.0-win-x64.exe`. Your browser opens the Link page on `127.0.0.1` (only reachable from this computer).
2. Enter api_id and api_hash, then your phone number, and click **Send login code**. Type the code from your Telegram app (and your two-step password if you use one).
3. Tick the channels to follow – leave **Dry run** on for every new channel.
4. In MT5, attach the Semaphore EA to one chart per account. Its panel shows **LISTENING**.

Full setup guide: see the Semaphore blog post on the author's MQL5 profile and the user manual.

### Run at log-on (VPS)

Task Scheduler → *Create Task* → trigger **At log on** → action: start `SemaphoreLink-1.0.0-win-x64.exe`. Enable automatic Windows log-on so the app and MT5 start again after a restart. Close Remote Desktop sessions instead of logging off.

## Privacy

- Your Telegram session and API key are stored **encrypted for your Windows user** (DPAPI) in `%LOCALAPPDATA%\Semaphore`.
- No server in between, no telemetry, no licence check. Nothing leaves your computer except the normal connection to Telegram.
- The app acts only on the chats you tick.

## Uninstall

Delete the EXE and the folder `%LOCALAPPDATA%\Semaphore`. End the session in Telegram → *Settings → Devices* ("Semaphore Link"). Signal files in `%APPDATA%\MetaQuotes\Terminal\Common\Files\Semaphore` can be deleted as well.

## Support

Questions and bug reports: via the Semaphore product page / comments on MQL5.

## Disclaimer

Trading forex and CFDs on margin carries a high risk of loss. Signals can be wrong; a signal copier executes what a channel writes, within your limits. Test every channel in dry run first. See [LICENSE.txt](LICENSE.txt).

© 2026 Pitt Petruschke (PiP)
