# EDU Advising & Payment Clearance Assistant
### Academic Advising Automation & Student Clearance Verification Engine (Chrome Extension)
**Version:** 3.2 • Enterprise Edition  
**Platform:** Google Chrome / Microsoft Edge / Brave (Manifest V3)

---

## 📋 Executive Overview

The **EDU Advising & Payment Clearance Assistant** is an enterprise-grade browser automation extension designed to streamline academic advising and semester registration clearance workflows at East Delta University (EDU).

Manually querying student IDs one-by-one in the Advising Portal is repetitive, time-consuming, and prone to human error. This Assistant interfaces directly with the official EDU Advising Portal (Google Apps Script) to batch-verify student clearances in seconds, smart-skip previously cleared records, sanitize spreadsheet artifacts, and deliver multi-format outputs (Excel workbooks and 1-click clipboard paste columns).

---

## ✨ Key Capabilities

| Feature | Description |
| :--- | :--- |
| **📁 Batch Excel Verification** | Upload `.xlsx` or `.xls` workbooks. The Assistant checks clearances, skips already `Cleared` records, and exports an updated workbook. |
| **📝 Quick Paste Lookup** | Paste comma, space, or newline-separated student IDs directly from emails or notices for an instant lookup and downloadable Excel summary. |
| **📊 Zero-Setup Google Sheets** | Query any Google Sheet shared as *"Anyone with the link can view"* via the Google Visualization API. Reads all tabs with zero OAuth or backend scripts. |
| **⚡ Smart Skip Caching** | Automatically skips re-querying students already marked `Cleared` in previous runs, saving up to 80% processing time on incremental lists. |
| **📋 1-Click Clipboard Copying** | Copy updated status columns per worksheet with 1 click, allowing immediate <kbd>Ctrl+V</kbd> pasting back into active Google Sheets. |
| **↗ Full Tab Acceleration** | Launch the Assistant in a dedicated browser tab to prevent Chrome background throttling during large batch operations (50+ students). |
| **🛡️ 100% Client-Side Privacy** | Operates entirely within your local browser session using bundled offline libraries (`xlsx.full.min.js`). No external telemetry or credentials stored. |

---

## 🚀 Installation Guide

### Prerequisites
- Google Chrome, Microsoft Edge, or Brave Browser (desktop version).
- Active university account with access to the EDU Advising Portal.

### Step-by-Step Setup
1. **Download & Extract**:
   - Extract the `EDUPaymentChecker` folder or ZIP to a permanent directory on your computer (e.g., `Documents\CheckPayment` or `Downloads\CheckPayment`).
   - *Note: Do not delete or move this folder after installation, as the browser loads the extension directly from this directory.*
2. **Open Extensions Manager**:
   - Open your browser and navigate to:
     - **Chrome:** `chrome://extensions`
     - **Edge:** `edge://extensions`
     - **Brave:** `brave://extensions`
3. **Enable Developer Mode**:
   - Toggle the **Developer mode** switch in the top-right corner to **ON**.
4. **Load Unpacked Extension**:
   - Click the **Load unpacked** button in the top-left toolbar.
   - Select the `EDUPaymentChecker` folder containing `manifest.json`.
5. **Pin Extension**:
   - Click the puzzle piece icon (🧩) in the browser toolbar and pin **EDU Clearance Assistant** for instant access.

---

## 🎯 Operational Modes

The Assistant offers three independent, fully sandboxed operational modes:

### Mode 1: 📁 Batch Excel Processing
Designed for routine department advising lists and registration rosters.

1. Ensure the **📁 Excel File** mode tab is active.
2. Drag and drop your `.xlsx` or `.xls` file into the upload zone, or click to browse.
3. Verify that your file contains a student ID column named **`ID NUMBER`** (or `Student ID`, `ID NO`, `ID`).
   > 💡 *Need a template? Click **"📥 Download Standard Template (.xlsx)"** inside the upload card.*
4. Ensure the Advising Portal tab is open in your browser (the status banner will turn green: `● Connected to Advising Portal`).
5. Click **▶ Start Verification**.
6. The Assistant iterates through each student:
   - Students already marked `Cleared` are automatically skipped.
   - Pending students are queried on the portal.
   - Real-time counters track `Cleared`, `Accounts Hold`, and `Issues / Flagged`.
7. When complete, an updated spreadsheet (`[Filename]_updated.xlsx`) downloads automatically with a clean `Payment Completed` column.

---

### Mode 2: 📝 Quick Paste ID Lookup
Designed for quick verification of student lists received via email, chat, or urgent advising tickets.

1. Switch to the **📝 Quick Paste** mode tab.
2. Paste student IDs into the text box. The Assistant supports:
   - Comma-separated: `262000112, 262000212, 262000312`
   - Space or Tab-separated: `262000112  262000212  262000312`
   - Newline-separated lists.
3. The real-time badge shows the total unique IDs identified.
4. Click **▶ Start Verification**.
5. The Assistant checks each student and generates a ready-to-use formatted Excel summary (`Quick_Advising_Results_[timestamp].xlsx`).

---

### Mode 3: 📊 Google Sheets Live Integration (Zero Setup)
Designed for live spreadsheets collaborated on by multiple faculty advisors.

#### Step 1: Set Google Sheet Sharing Permission
1. Open your target Google Sheet.
2. Click the blue **Share** button in the upper-right corner.
3. Under *General access*, change to **"Anyone with the link"** and ensure the role is set to **"Viewer"**.

#### Step 2: Load the Sheet into the Assistant
1. In the Assistant, switch to **📊 Google Sheets** ➔ **⚡ Direct Tab / Link (Zero Setup)**.
2. Paste the Google Sheet URL or Spreadsheet ID, **OR** select your open Google Sheet tab from the dropdown.
3. Click **📥 Load Google Sheet (All Tabs)**.
4. The Assistant queries the Google Visualization API (`/gviz/tq`) and loads all worksheet tabs and student counts in milliseconds.

#### Step 3: Run Verification & Export
1. Click **▶ Start Verification**.
2. The Assistant processes every worksheet tab, smart-skips cleared students, and updates clearance statuses.
3. Upon completion:
   - **Multi-Tab Excel Workbook**: Automatically downloads `[SheetTitle]_updated_[timestamp].xlsx` containing all worksheets and updated columns.
   - **1-Click Clipboard Pasting (`📋 Copy Column`)**: Click the copy button next to any worksheet tab. Then select the top cell in your Google Sheet and press <kbd>Ctrl+V</kbd> to paste the updated status column immediately!
   - **2-Column ID + Status Copy**: Click `📋 Copy ID + Status (2-Col)` to copy tab-delimited values for side-by-side reconciliation.

---

## ⚙️ Advanced Settings & Custom Endpoints

If the institution updates the Google Apps Script Advising Portal URL in the future:
1. Click **⚙️ Settings** in the header.
2. Enter the new URL into the **Advising Portal Web App Endpoint** field.
3. Click **Save Settings**. The Assistant will immediately link to the new endpoint.
4. Click **Reset Default** anytime to restore the factory university URL.

---

## 🔒 Security & Data Privacy Assurance

- **100% Client-Side Execution:** All parsing and portal queries run strictly inside your local browser instance.
- **Zero External Telemetry:** No student IDs, names, or clearance results are ever transmitted to third-party servers.
- **Offline File Processing:** Excel parsing is powered by the local, bundled `xlsx.full.min.js` library with no external network calls required.
- **Read-Only Google Sheet Access:** Direct Google Sheet reading requires only Viewer permissions, ensuring your master sheets cannot be inadvertently overwritten.

---

## ❓ Frequently Asked Questions (FAQ)

#### Q1: Why does the Assistant show "Advising Portal Tab Required"?
**A:** The Assistant checks records by interacting with the official university Advising Portal form. The Advising Portal must be open in at least one browser tab. Click **"🌐 Open Portal in Browser"** to launch it immediately.

#### Q2: What happens if Chrome freezes or pauses during a large list?
**A:** Chrome throttles background extension popups when you click outside them or switch tabs. For lists larger than 50 students, click **"↗ Full Tab"** in the top header. In Full Tab mode, Chrome treats the Assistant as an active window that never pauses.

#### Q3: Can I re-run an Excel sheet without re-checking students who already paid?
**A:** Yes! The Assistant automatically inspects the `Payment Completed` column. If a row already contains `"Cleared"`, it is preserved and skipped, saving significant time.

#### Q4: What columns does the Assistant add to my Excel file?
**A:** The Assistant only adds or updates a single column: **`Payment Completed`** (`Cleared`, `Contact Accounts`, or `Student not found`). All original columns and ordering are strictly preserved.

---

## 📦 File Architecture

```
EDUPaymentChecker/
├── manifest.json             # Manifest V3 extension configuration
├── popup.html                # Professional interface (popup & full tab)
├── popup.js                  # Core automation engine, GViz reader, Excel processor
├── content.js                # Secure in-frame communication bridge
├── background.js             # Extension service worker
├── google_sheets_bridge.js   # Optional enterprise Apps Script bridge code
├── xlsx.full.min.js          # Bundled SheetJS Excel parser (offline)
├── README.md                 # Documentation & User Manual
└── EDUPaymentChecker.zip     # Compressed distribution package
```

---
*Developed for East Delta University (EDU) Academic Advising & Registration Administration.*
