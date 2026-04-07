# 💀 Grim Reaper

> Nepal mobile number extractor

A desktop GUI tool for bulk-extracting valid Nepali mobile numbers from Excel, CSV, Word, PDF, and plain-text files. Built during work at an SMS service provider to automate contact harvesting from unstructured documents.

![Python](https://img.shields.io/badge/Python-3.10+-blue) ![PySide6](https://img.shields.io/badge/GUI-PySide6-green) ![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey) ![License](https://img.shields.io/badge/License-MIT-yellow)

---

## Features

- **Multi-format extraction** — handles `.xlsx`, `.xls`, `.csv`, `.docx`, `.doc`, `.pdf`, `.txt` in one pass
- **NTA prefix validation** — validates against all known NTC, Ncell, Smart Cell, UTL, and Hello Mobile prefixes (verified 2025)
- **OCR for scanned PDFs** — falls back to Tesseract OCR with confidence filtering (≥60%) when no text layer is found
- **Nepali digit support** — normalizes Devanagari digits and Preeti font encodings before extraction
- **Global deduplication** — reports unique count vs. total extracted across all files
- **Drag-and-drop + folder scan** — drop a folder to recursively collect all supported files

---

## Supported Operators

| Operator | Prefixes |
|---|---|
| NTC (Namaste) | 984, 985, 986, 974, 975, 976 |
| Ncell | 980, 981, 982, 970, 971 |
| Smart Cell | 961, 962, 988 |
| UTL CDMA | 972 |
| Hello Mobile | 963 |

---

## Installation if you do not wish to use the .exe

### Prerequisites

- Python 3.10+
- Tesseract OCR *(optional — scanned PDFs only)*
- Poppler for Windows *(optional — scanned PDFs only)*

### Install dependencies
```bash
pip install PySide6 pandas openpyxl xlrd pdfplumber python-docx docx2txt

# Optional — for scanned PDF OCR support
pip install pdf2image pytesseract Pillow
```

### OCR setup (optional)

1. **Tesseract** — download from [UB Mannheim](https://github.com/UB-Mannheim/tesseract/wiki), install to `<project_root>/tesseract/`, and include the `nep` language pack
2. **Poppler** — download from [oschwartz10612/poppler-windows](https://github.com/oschwartz10612/poppler-windows/releases), extract to `<project_root>/poppler/Library/bin/`

If neither is installed, the app runs normally — OCR is silently disabled.

### Run
```bash
python app.py
```

---

## Usage

1. Launch the app
2. Add files via **Add** or drag-and-drop files/folders onto the window
3. Click **Start**
4. Monitor the live log panel for per-file progress
5. On completion, choose a save path — output is a `.xlsx` with a single `Phone Number` column
