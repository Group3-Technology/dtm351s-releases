# G3 DTM 351-S Teslameter — Control GUI

Downloads for the desktop application that reads and logs measurements from
the **Group3 DTM 351-S 3-axis digital teslameter** over serial connections.

### [⬇ Download the latest release](https://github.com/Group3-Technology/dtm351s-releases/releases/latest)

| File | Platform |
|------|----------|
| `G3_DTM351_Control-macos.zip` | macOS 11 (Big Sur) or newer |
| `G3_DTM351_Control-windows.zip` | Windows 10/11 (64-bit) |
| `SHA256SUMS.txt` | Checksums for the above |

Each download contains the application, the full **User Guide** (PDF), and
third-party licence notices. No installer, no admin rights, and no separate
runtime to install — unzip and run.

You will need up to **three serial connections** to the PC — native RS-232
ports or USB-to-serial adapters — because the instrument presents one port
per channel. The application also has a demo mode, so you can explore it
without any hardware.

---

## Installing

The application is **not code-signed**, so the first launch needs one extra
click to tell your operating system it is safe to run. This is normal for
in-house instrument software, and only needed once.

### Windows

1. Unzip `G3_DTM351_Control-windows.zip` somewhere convenient — for example
   `C:\Program Files\G3_DTM351` or your Desktop. **Keep all the files
   together in the folder.**
2. Open the folder and double-click **`G3_DTM351_Control.exe`**.
3. If Windows shows a blue **"Windows protected your PC"** dialog, click
   **More info → Run anyway**. Once only.

> Don't move the `.exe` out of its folder on its own — it needs the files
> alongside it.

**Using USB-to-serial adapters? Set each adapter's Latency Timer to 1 ms.**
Windows defaults it to 16 ms, which is enough to break the alignment between
the three channels — readings blank and return, and rows go missing from the
CSV log. The User Guide (section 3, *Installation*) has the steps; it is a
one-time setting per adapter.

### macOS

1. Unzip `G3_DTM351_Control-macos.zip` (double-click it in Finder).
2. Drag **`G3_DTM351_Control.app`** to your **Applications** folder.
3. Approve it on first launch — **the steps depend on your macOS version**,
   because Apple changed this in macOS 15. Check yours under the Apple menu
   → **About This Mac**.

<details open>
<summary><b>macOS 15 (Sequoia) or later — including macOS 26</b></summary>

1. Double-click the app. macOS blocks it with *"Apple could not verify
   … is free of malware."* Click **Done**. This first attempt is
   required — it's what makes the button below appear.
2. Go to **System Settings → Privacy & Security**, scroll to **Security**.
3. Next to *"G3_DTM351_Control was blocked to protect your Mac"*, click
   **Open Anyway** → confirm → authenticate.

</details>

<details>
<summary><b>macOS 14 (Sonoma) or earlier</b></summary>

**Right-click (or Control-click) the app → Open**, then click **Open** in
the dialog. Apple removed this route in macOS 15, so it won't work on
newer systems.

</details>

4. Afterwards, open it normally. You only approve it once.

Prefer the Terminal? This works on every macOS version and replaces the
whole procedure:

```bash
xattr -dr com.apple.quarantine "/Applications/G3_DTM351_Control.app"
```

## Verifying your download

Optional, but worth doing on a shared or unreliable connection — it confirms
the file arrived intact.

```bash
# macOS / Linux
shasum -a 256 -c SHA256SUMS.txt --ignore-missing

# Windows (PowerShell) — compare the output against SHA256SUMS.txt
Get-FileHash G3_DTM351_Control-windows.zip -Algorithm SHA256
```

## Documentation

The **User Guide** ships inside each download as `USER_GUIDE.pdf` — install
notes, connecting all three channels, Axis and Channel modes, CSV logging,
the graph window, and troubleshooting.

## Support

For assistance, contact **Group3 Technology** —
<https://www.group3technology.com>.

Please include the application version (under **Help → About**), your
operating system, and a short description of what you did and what
happened. For a connection problem, the **CONSOLE** tab shows the raw
serial traffic and can save it to a log file to attach.

## About this repository

This repository hosts **downloads only**. The application source is
maintained privately by Group3 Technology. The serial driver it builds on is
open source and available at
[Group3-Technology/group3lib](https://github.com/Group3-Technology/group3lib).

The application is MIT licensed — see [LICENSE](LICENSE). Third-party licence
notices are included in every download.
