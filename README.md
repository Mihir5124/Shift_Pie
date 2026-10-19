# Shiftpie

**Double right-click a file, pick a slice, done.**

Shiftpie is a tiny Windows utility that adds a circular "pie" menu to any file. Double right-click a file in Explorer or on the Desktop and a pie of actions for that file type opens at your cursor: convert it, compress or crop an image, zip it, copy its path. No app to open, no menus to dig through.

## Features

- **Pie menu at your cursor.** Options change with the file type, with a **MORE** slice when there are over eight.
- **Convert between many formats**, with converters built in (see the table below).
- **Light image editing:** compress, crop with a draggable box and exact numeric fields, and add a background (padding, rounded corners, gradient).
- **Low footprint.** Idle, only a small background service and a tray icon run. The pie window is started on demand and closes when you are done.
- **Silent finish.** Converted files are saved next to the original (or in Downloads if that folder is read-only). Existing files are never overwritten. A small pill shows progress and closes itself.
- **Quit any time** from the tray icon (under the `^` hidden icons near the clock).
- **Private.** Everything runs locally. Nothing is uploaded.

## Supported conversions

| Input | Output |
|---|---|
| PDF | DOCX (keeps text position, size, bold/italic and embedded images), TXT, PNG, JPG |
| Images: PNG, JPG, WEBP, BMP, GIF, AVIF, ICO | PNG, JPG, WEBP, PDF, plus COMPRESS, CROP, ADD BG |
| Text: TXT, MD, LOG, CSV, JSON, HTML, XML, YAML, INI | PDF, DOCX, HTML, TXT (CSV and JSON convert to each other) |
| DOCX, ODT | PDF, TXT, HTML, MD (ODT also to DOCX) |
| XLSX | CSV, JSON, TXT, HTML, PDF (first sheet) |
| PPTX | TXT, MD, PDF (slide text) |
| DOC, RTF, WPS, XLS, ODS, PPT, ODP | PDF, DOCX, ODT, XLSX, PPTX and more. **Needs [LibreOffice](https://www.libreoffice.org/)** |
| Audio: MP3, WAV, OGG, FLAC, M4A, AAC, OPUS, WMA | MP3, WAV, OGG, FLAC, M4A. **Needs [ffmpeg](https://ffmpeg.org/)** |
| Video: MP4, MKV, AVI, MOV, WEBM, WMV, FLV, M4V | MP4, WEBM, MKV, GIF, MP3. **Needs ffmpeg** |
| Any file | ZIP, COPY PATH |

If LibreOffice or ffmpeg is missing, the pie shows a **GET LIBREOFFICE** or **GET FFMPEG** slice that opens the download page. If LibreOffice is installed, DOCX, XLSX and PPTX to PDF use it for better fidelity.

## Install

1. Download `Shiftpie-Setup.exe`.
2. Run it and click through the wizard. It installs for the current user only and needs no admin rights.
3. On the last page, choose whether Shiftpie should start when you sign in.

Windows SmartScreen may warn because the installer is not code-signed: choose **More info**, then **Run anyway**.

The Start menu gets **Shiftpie** (starts the service) and **Stop Shiftpie**. To uninstall, use **Settings > Apps > Shiftpie**.

## Usage

1. Make sure Shiftpie is running (its tray icon is visible).
2. In Explorer or on the Desktop, **double right-click** a file.
3. Click a slice. Press **Esc** or move the cursor away to dismiss the pie.

The first right-click opens Explorer's context menu, so Shiftpie presses Esc to close it. If your second click happens to land on the menu's top-left corner, it can still trigger the first menu item. Try it on a harmless file first.

## Limitations

- **Windows 10/11 (x64) only.**
- One file at a time, even if several are selected.
- PDF to DOCX rebuilds text and embedded images but not vector lines, shapes or table borders, and cannot read scanned (image-only) pages.
- PDFs generated from text, DOCX or XLSX use a Latin-only font, so non-Latin characters appear as `?`.
- DOCX, ODT, XLSX and PPTX conversions without LibreOffice are text-based: formatting and images are not kept. XLSX uses the first sheet only.
- With Windows 11 tabbed Explorer, the selected file is read from whichever tab has a selection.

## Built with

[Electron](https://www.electronjs.org/), [pdf.js](https://mozilla.github.io/pdf.js/), [docx](https://github.com/dolanmiu/docx), [pdf-lib](https://pdf-lib.js.org/), [JSZip](https://stuk.github.io/jszip/), [uiohook-napi](https://github.com/SnosMe/uiohook-napi), [koffi](https://koffi.dev/) and [systray2](https://github.com/felixhao28/node-systray).
