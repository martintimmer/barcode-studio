# 🎛️ Barcode Studio

> Generate, save, and read **CODE 39 / ITF / CODE 128 / DATA MATRIX / EAN-13 / UPC-A / QR** codes — right in your browser.

A single-file, zero-install web app. Open `index.html`, type a payload, and get a live, print-ready code. No server, no build step, no image uploads.

🧩 **File:** `index.html`
🌐 **Runs:** any modern browser (desktop, iOS, iPadOS)
🎨 **Theme:** dark by default, light available

---

## ✨ Features

- ⚡ **Live preview** — the code updates as you type
- 🧾 **7 formats** — Code 39, ITF, Code 128, Data Matrix, EAN-13, UPC-A, QR
- 💾 **One Save button** — export as **SVG**, **JPG**, or **PNG**
- 📄 **Payload filenames** — downloads are named after your data (e.g. `1002.png`)
- 📋 **Copy** — one tap to copy the payload
- 🧭 **Input hints** — red notes show the exact length/characters allowed per format
- 📷 **Camera scanner** — reads all common barcodes and fills the payload
- 🌗 **Dark / light theme** — remembered between sessions
- 🔒 **Private by design** — everything is generated locally in the page

---

## 🚀 Quick Start

1. **Open** `index.html` in your browser *(double-click works)*.
2. **Pick a format** from the tabs in the toolbar.
3. **Type your data** into the `PAYLOAD / DATA` box on the left *(empty? the preview shows a live `1002` sample)*.
4. **Watch** the live code appear on the right.
5. **Click `SAVE ▾`** and choose **SVG**, **JPG**, or **PNG**.

> 💡 The first load needs an internet connection so the barcode libraries can be fetched from a CDN. After that the page works offline.

---

## 📖 User Manual

### 🏷️ Format tabs

| Tab | Format | Type | Input rules |
| --- | --- | --- | --- |
| `CODE 39` | Code 39 | 1D | `0-9 A-Z - . space $ / + %` (auto-uppercase) |
| `ITF` | Interleaved 2 of 5 | 1D | Digits `0-9`, **even** count only |
| `CODE 128` | Code 128-B | 1D | Printable ASCII (32–126) |
| `DATA MATRIX` | Data Matrix (ECC 200) | 2D | Any text |
| `EAN-13` | EAN-13 | 1D | `0-9` only, **12 or 13** digits |
| `UPC-A` | UPC-A | 1D | `0-9` only, **11 or 12** digits |
| `QR` | QR Code | 2D | Any text |

> For **ITF**, **EAN-13** and **UPC-A** a red note appears under the input box spelling out exactly how many characters and which kind are allowed. For EAN-13/UPC-A you can enter the number *without* the final check digit — it is calculated automatically.

### ⌨️ Payload field
The left panel is where you enter data. It regenerates on every keystroke — there is no "generate" button.
When the box is empty it shows a gray hint (`Type your input here, i.e. "1002" is live now`) and the preview keeps a live sample so you always see an example.
If the input is invalid for the selected format, a red message appears under the box.

### 🖼️ Preview panel
The right panel shows the live result, its format, and `[ LIVE ]` status. Codes are shown dark-on-white in light mode and light-on-dark in dark mode, and the downloaded image matches exactly what you see.

### 💾 Saving your code
Click **`SAVE ▾`** and pick a format:

| Option | Best for | Notes |
| --- | --- | --- |
| 🖋️ **SVG** | Print & design tools | Infinite scaling, tiny file *(not available for QR)* |
| 🖼️ **JPG** | Sharing / documents | Photo-friendly |
| 📄 **PNG** | Sharp pixels | Lossless, clean edges |

Files are named after your **payload**, e.g. `1002.svg`, `1002.png`, `1002.jpg`. Characters that aren't allowed in filenames are replaced with `_`.

### 📋 Copying the payload
Click **`COPY`** to put the current payload on your clipboard — handy after scanning.

### 📏 Output size
The **`[ OUTPUT SIZE ]`** slider sits directly under the live preview (25%–100%).
Drag it to scale the rendered code. Scaling is always proportional, so **no code is ever distorted** — including Data Matrix and QR. For QR the size label shows the real on-screen pixel size.

### ⚙️ Settings
Open with the **`SETTINGS +`** button in the top bar. Options adapt to the current format:

- 🔠 **Font size** — UI scale (13–19 px, default **15 px / Standard**, scales the whole workspace)
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

> 🔐 On **iPhone / iPad**, camera access requires the page to be served over **HTTPS** or **localhost**. Opening the file directly off local storage will not grant camera access.

### 🌗 Theme
Toggle **dark ⇄ light** with the button in the top-right corner. It shows the mode you'll switch *to* and remembers your choice.

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

## 📦 Publishing / Hosting

Because this is a single static file, you can host it anywhere. To enable the camera on mobile, serve it over HTTPS — **GitHub Pages** is the easiest option.

```powershell
cd "C:\Users\7000027237\Downloads\barcode-studio"
git init; git add index.html README.md; git commit -m "Barcode Studio v1.0.0"; git branch -M main
gh repo create barcode-studio --public --source=. --remote=origin --push
git tag -a v1.0.0 -m "Barcode Studio v1.0.0"; git push origin v1.0.0
gh release create v1.0.0 --title "Barcode Studio v1.0.0" --generate-notes index.html
```

Then enable **Settings → Pages → Branch: main / root** and open the `https://<user>.github.io/barcode-studio/` URL on your phone for camera support.
