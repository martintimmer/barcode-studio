# 🎛️ Barcode Studio

**🔗 Live app:** https://martintimmer.github.io/barcode-studio/

> Generate, save, and read **CODE 39 / ITF / CODE 128 / DATA MATRIX / EAN-13 / UPC-A / QR** codes — right in your browser.

A single-file, zero-install web app. Open `index.html`, type a payload, and get a live, print-ready code. No server, no build step, no image uploads.

🧩 **File:** `index.html` · 🖼️ **Icon:** `favicon.ico`
🌐 **Runs:** any modern browser (desktop, iOS, iPadOS)
🎨 **Theme:** light by default, dark available

---

## ✨ Features

- ⚡ **Live preview** — the code updates as you type
- 🧾 **7 formats** — Code 39, ITF, Code 128, Data Matrix, EAN-13, UPC-A, QR
- 💾 **One Save button** — export as **SVG**, **JPG**, or **PNG** (72 or **300 DPI**)
- 📄 **Payload filenames** — downloads are named after your data (e.g. `1002.png`)
- 📋 **Copy** — one tap to copy the payload
- 🔤 **QR caption** — show the payload as human-readable text beside the QR (left/right/top/bottom)
- 📚 **Batch → PDF** — import an XLS / JSON / CSV of serial numbers and export a printable QR sheet
- 🧭 **Input hints** — red notes show the exact length/characters allowed per format
- 🔗 **Deep links** — encode format, data, size and options in the URL for shareable links
- 📷 **Camera scanner** — reads all common barcodes and fills the payload
- 🌗 **Dark / light theme** — remembered between sessions
- 🔒 **Private by design** — everything is generated locally in the page

---

## 🚀 Quick Start

1. **Open** the [live app](https://martintimmer.github.io/barcode-studio/) or the local `index.html`.
2. **Pick a format** from the tabs in the toolbar.
3. **Type your data** into the `PAYLOAD / DATA` box on the left *(empty? the preview shows a live `1002` sample)*.
4. **Watch** the live code appear on the right.
5. **Click `SAVE ▾`** and choose **SVG**, **JPG**, or **PNG**.

> 💡 The first load needs an internet connection so the barcode libraries can be fetched from a CDN. After that the page works offline.

---

## 📖 User Manual

### 🏷️ Format tabs

| Tab | URL hash | Format | Type | Input rules |
| --- | --- | --- | --- | --- |
| `QR` | `#QR` | QR Code | 2D | Any text |
| `DATA MATRIX` | `#DataMatrix` | Data Matrix (ECC 200) | 2D | Any text |
| `CODE 39` | `#Code39` | Code 39 | 1D | `0-9 A-Z - . space $ / + %` (auto-uppercase) |
| `ITF` | `#ITF` | Interleaved 2 of 5 | 1D | Digits `0-9`, **even** count only |
| `CODE 128` | `#Code128` | Code 128-B | 1D | Printable ASCII (32–126) |
| `EAN-13` | `#EAN13` | EAN-13 | 1D | `0-9` only, **12 or 13** digits |
| `UPC-A` | `#UPCA` | UPC-A | 1D | `0-9` only, **11 or 12** digits |

> 📱 On phones the four primary tabs show and the other three are under a **`MORE ▾`** menu, so nothing overflows.

#### 🔗 Deep links

The address bar always reflects the current state, so you can copy it to share an exact code:

```
#<Mode>?=<data>&size=<25-100>
```

| Example | Result |
| --- | --- |
| `…/#QR` | Opens the QR generator |
| `…/#Code128?=ABC-123` | Code 128 with payload `ABC-123` |
| `…/#QR?=HQ0012564&size=75` | QR with payload `HQ0012564` at 75% size |
| `…/#EAN13?=590123412345&size=100` | EAN-13 at full size |
| `…/#QR?=HQ0012564&size=75&qrtext=1&qrpos=right&qrtsize=18` | QR with caption on the right at 18 px |
| `…/#QR?=HQ0012564&dpi=300` | QR saved at 300 DPI |

Supported parameters: `size` (10–100), `qrtext` (`0`/`1`), `qrpos` (`left`/`right`/`top`/`bottom`), `qrtsize` (8–48), `dpi` (`72`/`300`), `format` (`svg`/`png`/`jpg`).

> ⬇️ **Auto-download:** adding `format` to the URL downloads the image automatically when the link opens, e.g. `…/#QR?=HQ0012564&format=png&dpi=300` saves `HQ0012564.png` at 300 DPI (open without `format` to just preview).

- Clicking a tab pushes a history entry (back/forward works); typing data, moving a slider, or toggling settings updates the URL in place.
- Data is URL-encoded, so any text works — e.g. `#QR?=https%3A%2F%2Fexample.com`.
- Opening/reloading a link applies the format, payload, size and options.

> For **ITF**, **EAN-13** and **UPC-A** a red note appears under the input box spelling out exactly how many characters and which kind are allowed. For EAN-13/UPC-A you can enter the number *without* the final check digit — it is calculated automatically.

### ⌨️ Payload field
The left panel is where you enter data. It regenerates on every keystroke — there is no "generate" button.
When the box is empty it shows a gray hint (`Type your input here, i.e. "1002" is live now`) and the preview keeps a live sample so you always see an example.
If the input is invalid for the selected format, a red message appears under the box.

### 🖼️ Preview panel
The right panel shows the live result, its format, and `[ LIVE ]` status. Codes are shown dark-on-white in light mode and light-on-dark in dark mode, and the downloaded image matches exactly what you see.

### 💾 Saving your code
Click **`SAVE ▾`** and pick a format. **PNG** and **JPG** each have a **72 / 300 DPI** choice:

| Option | Best for | Notes |
| --- | --- | --- |
| 🖋️ **SVG** | Print & design tools | Infinite scaling, tiny file *(not available for QR)* |
| 🖼️ **JPG · 72 / 300 DPI** | Sharing / documents | Photo-friendly |
| 📄 **PNG · 72 / 300 DPI** | Sharp pixels | Lossless, clean edges |

**300 DPI** scales the pixel resolution (×300/72) and embeds the DPI in the file's metadata (PNG `pHYs`, JPEG JFIF) so it is print-ready.

Each option is a **real link** that encodes the current settings (`…/#QR?=HQ0012564&format=png&dpi=300`): **hover / long-press to see & copy the link**, and opening it auto-downloads the image. Clicking an option sets that URL and downloads.

Files are named after your **payload**, e.g. `1002.svg`, `1002.png`, `1002.jpg`. Characters that aren't allowed in filenames are replaced with `_`.

### 📋 Copying the payload
Click **`COPY`** to put the current payload on your clipboard — handy after scanning.

### 📏 Output size
The **`[ OUTPUT SIZE ]`** slider sits directly under the live preview (10%–100%, default **50%**).
Drag it to scale the rendered code. Scaling is always proportional, so **no code is ever distorted** — including Data Matrix and QR.
For QR the size maps to a fixed pixel size: **256 px at 50%**, **512 px at 100%** (shown in the preview's meta row).

### 🔤 QR caption (human-readable text)
In the QR settings you can turn on **HUMAN-READABLE TEXT** to print the payload beside the QR code, and choose its **POSITION** — `RIGHT`, `LEFT`, `TOP`, or `BOTTOM`. The caption uses the **PT Mono** font and the same colour as the code, and it is included in the exported PNG/JPG.
When enabled, controls appear **under the QR preview**:
- **`[ TEXT POSITION ]`** — pop the caption to `RIGHT / LEFT / TOP / BOTTOM`.
- **`[ TEXT PADDING ]`** — the gap between the QR and the text (0–40 px).
- **`[ TEXT SIZE ]`** — caption size (8–48 px).

The same options are also in `SETTINGS +`, and all are included in the URL (`qrpos`, `qrpad`, `qrtsize`).

### 📚 Batch (QR → PDF)
In **QR** mode, below the sliders, a **`Batch generator`** button (same style as `SCAN CAMERA`) opens a **large popup** that only produces **QR** codes:

1. **Import a file** — **drag & drop** (or click to browse) an XLS/XLSX, JSON, CSV or TSV. The first column is used (a header like `SN` / `Serial` / `Code` is ignored); JSON accepts strings or objects (`sn`/`serial`/`code`/`value`).
2. **Page size** — **A4** (21.0 × 29.7 cm), **A5** (14.8 × 21.0 cm), **Letter** (21.6 × 27.9 cm) or **CUSTOM** (type any paper W × H in cm).
3. **Text orientation** — where the readable text sits: `BELOW`, `ABOVE`, `RIGHT` or `LEFT`.
4. **Columns / Rows steppers** — `−` / `+` to change the grid up to **7 × 35** per page (extra items flow onto more pages automatically).
5. **Sliders** — **QR SIZE** (the printed QR size, **0.3–3.0 cm**), **TEXT SIZE** (caption mm), **GAP** (space between labels) and **SAFE MARGIN** (print-safe page border). Setting the QR size automatically shrinks the grid so it fits (e.g. 3 cm → 6 × 8 on A4).
6. **Advanced** — expand **CUSTOM MARGINS** to set independent **Top / Right / Bottom / Left** margins.
7. **Preview** — auto-generates the sheet on a print-like background. Zoom with **−/+**, **FIT**, or **100 %** (100 % = true physical size, so an A4 page shows at its real printed scale).
8. **`QR SIZE: … CM`** shows how big each QR prints (e.g. `0.46 CM`), updating live.
9. **`DOWNLOAD PDF`** writes `qr-batch.pdf` while a **progress bar** fills the status area. The PDF matches the preview exactly (page, grid, orientation, sizes and margins).

> A ready-made test file lives at `sample-sns-150.csv` (now **300** codes in the `HQ00#####` template).

### ⚙️ Settings
Open with the **`SETTINGS +`** button in the top bar. Options adapt to the current format:

- 🔠 **Font size** — UI scale (15–21 px, default **17 px / Standard**, scales the whole workspace)
- 🖼️ **Colored edge** — toggle the coloured frame around the page
- 🎨 **Distinct colors** — pick predefined **Color 1** (selected buttons + sliders) and **Color 2** (borders + hover); both persist
- ✅ **MOD-43 checksum** — Code 39 only
- 👁️ **Human-readable text** — show the value under 1D barcodes

> 📏 Code sizing lives in the **`[ OUTPUT SIZE ]`** slider below the preview, so it's always one tap away.

### 📷 Scanning with the camera
1. Click **`SCAN CAMERA`** in the top bar. The generator is hidden and only the reader is shown.
2. Allow camera access when prompted.
3. Point at a barcode — QR, Data Matrix, EAN-13/UPC-A, Code 39/93/128, ITF, Codabar and more.
4. The camera closes automatically, the app switches to the detected format, and loads the live preview.
5. Use **`COPY`** to copy the payload, or **`SAVE ▾`** to save a copy in the same mode it was scanned.

The reader is configured for **every symbology ZXing supports** (QR, Data Matrix, Aztec, PDF417, MaxiCode, Code 39/93/128, Codabar, ITF, EAN-13/8, UPC-A/E, RSS) with a "try harder" pass for accuracy. Formats the app can also generate (Code 39, ITF, Code 128, Data Matrix, EAN-13, UPC-A, QR) switch the mode automatically; anything else is loaded read-only so you can still **COPY** it.

> 🔐 On **iPhone / iPad**, camera access requires the page to be served over **HTTPS** or **localhost**. Opening the file directly off local storage will not grant camera access — use the [live app](https://martintimmer.github.io/barcode-studio/).

### 🌗 Theme
Toggle **dark ⇄ light** with the button in the top-right corner. It shows the mode you'll switch *to* and remembers your choice.

### 📱 Layout
Wide screens keep a **540px** minimum layout; phones/small screens (≤700px) reflow responsively with no horizontal scroll. Pinch-zoom is enabled on mobile, and the extra format tabs collapse into a **`MORE ▾`** menu.

---

## 🧰 Tech Stack

| Library | Role |
| --- | --- |
| [QRCode.js](https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js) | QR generation |
| [ZXing Browser](https://unpkg.com/@zxing/browser@0.1.5/umd/zxing-browser.min.js) | Camera decoding |
| [bwip-js](https://unpkg.com/bwip-js@4.6.0/) | Data Matrix + EAN-13/UPC-A generation |
| [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) | UI typeface |

Code 39, ITF, and Code 128 are generated by built-in, dependency-free routines.

---

## 🛠️ Troubleshooting

| Symptom | Fix |
| --- | --- |
| "library did not load" | Connect to the internet once and reload |
| Camera won't start | Serve over HTTPS/localhost and allow camera permission |
| `Invalid Code 39 character` | Stick to `0-9 A-Z - . space $ / + %` |
| ITF error | Digits only, and an even number of them |
| EAN-13 / UPC-A error | Digits only; EAN-13 needs 12–13, UPC-A needs 11–12 |
| Data Matrix fails | Usually means the library didn't load — check connection |
| QR export has no SVG | QR is raster-only (`JPG` / `PNG`) |

---

## 🔒 Privacy

Your data never leaves the device. Codes are generated and scanned entirely in the browser — nothing is uploaded to a server.

---

## 📦 Repo / Publishing

Files: `index.html`, `favicon.ico`, `README.md`.

```powershell
cd "C:\Users\7000027237\Downloads\barcode-studio"
git init; git add index.html favicon.ico README.md; git commit -m "Barcode Studio v1.0.0"; git branch -M main
gh repo create barcode-studio --public --source=. --remote=origin --push
git tag -a v1.0.0 -m "Barcode Studio v1.0.0"; git push origin v1.0.0
gh release create v1.0.0 --title "Barcode Studio v1.0.0" --generate-notes index.html
```

Hosting: **Settings → Pages → Branch: main / root** → the app is served at
**https://martintimmer.github.io/barcode-studio/** (HTTPS, so the camera works on phones).
