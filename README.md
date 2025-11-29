# 🛡️ File Integrity Monitor (FIM)

A browser-based security tool designed to detect unauthorized file changes, deletions, or additions within a local directory. This project demonstrates core Cybersecurity concepts including **hashing**, **baselining**, and **integrity verification** entirely on the client side.

## 📖 Overview

File Integrity Monitoring is an internal control process that validates the integrity of operating system and application software files. This tool creates a cryptographic "fingerprint" of a directory structure and compares it against a future state to detect anomalies.

**Key Features:**
* **SHA-256 Hashing:** Uses the Web Crypto API to generate secure hashes for file verification.
* **Baseline Generation:** Creates a JSON snapshot of the directory state (paths and hashes).
* **Change Detection:** Identifies:
    * 🟡 **Modified Files:** Content has changed (hash mismatch).
    * 🟢 **New Files:** Files added since the baseline.
    * 🔴 **Deleted Files:** Files removed since the baseline.
* **Privacy First:** All processing happens locally in the browser. No files are uploaded to any server.
* **Modern UI:** Responsive design built with Tailwind CSS.

## 🚀 How to Run

Since this is a client-side application, no backend installation is required.

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/your-username/file-integrity-monitor.git](https://github.com/your-username/file-integrity-monitor.git)
    ```
2.  **Open the Application:**
    * Navigate to the folder.
    * Double-click `index.html` to open it in your web browser (Chrome, Edge, or Brave recommended for `webkitdirectory` support).
    * *Note: Ensure you have an internet connection so the Tailwind CSS script can load.*

## ⚙️ How It Works (Usage)

### Step 1: Create a Baseline
1.  Click **"Select Directory to Create Baseline"**.
2.  Choose a folder from your computer.
3.  The tool calculates the SHA-256 hash for every file.
4.  Click **"Download Baseline.json"** to save your trusted state.

### Step 2: Simulate an Attack / Changes
1.  Go to the folder you selected.
2.  **Modify** a text file, **delete** an image, or **add** a new script.

### Step 3: Run Integrity Check
1.  Refresh the web page (or simply move to the next section).
2.  Upload the `baseline.json` file you downloaded earlier.
3.  Select the **same directory** again under "Select Directory to Check".
4.  Click **"Run Integrity Check"**.
5.  View the report highlighting exactly what changed.

## 🛠️ Technical Stack

* **Frontend:** HTML5, Vanilla JavaScript (ES6+)
* **Styling:** Tailwind CSS (via CDN)
* **Cryptography:** JavaScript Web Crypto API (`crypto.subtle.digest`)
* **File Handling:** HTML5 File API & `webkitdirectory`

## 🧩 Code Structure

* **Hashing Logic:** The `calculateHash()` function reads the file buffer and returns a hex string using SHA-256.
* **Comparison Algorithm:** Iterates through the current directory state and compares it against the JSON object keys and values from the baseline to categorize changes.

## 🔮 Future Enhancements

* Add support for excluding specific file types (e.g., `.log` files).
* Implement different hashing algorithms (MD5, SHA-512) for performance comparison.
* Export the Scan Result report as a PDF.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
