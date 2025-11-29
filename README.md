# 🔽 Pixeldrain to Google Drive Downloader

A professional, high-speed Google Colab notebook that downloads files from Pixeldrain directly to your Google Drive using Google's cloud infrastructure. Built with best practices, modular code, and comprehensive error handling.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/NeelPatra/pixeldrain-gdrive-downloader/blob/main/Pixeldrain_Downloader.ipynb)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.7+](https://img.shields.io/badge/python-3.7+-blue.svg)](https://www.python.org/downloads/)

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| ⚡ **High-Speed Downloads** | Uses aria2c with 16 parallel connections for maximum speed |
| ☁️ **Direct to Google Drive** | No local storage needed - downloads straight to your Drive |
| 🔗 **Smart URL Conversion** | Automatically converts Pixeldrain URLs to direct API links |
| ✅ **URL Validation** | Validates links before downloading to prevent errors |
| ⏳ **Real-Time Progress** | Live download progress with detailed status updates |
| ⚠️ **Error Handling** | Comprehensive error messages with troubleshooting guides |
| 🧩 **Modular Design** | Clean, maintainable code structure for easy modifications |
| 📘 **Full Documentation** | Every function documented with examples |

---

## 🔧 How It Works

```mermaid
graph LR
    A[Paste Pixeldrain Link] --> B[Validate URL]
    B --> C[Convert to Direct Link]
    C --> D[Download with aria2c]
    D --> E[Save to Google Drive]
    E --> F[Download Complete!]
```

1. **Mount Google Drive** - Connects Colab to your Google Drive
2. **Validate URL** - Checks if the link is a valid Pixeldrain URL
3. **Convert Link** - Transforms web URL to direct API download link
4. **Download** - Uses aria2c with optimized settings for speed
5. **Save** - File is saved directly to your Google Drive folder

---

## ✅ Prerequisites

Before you start, make sure you have:

- ✅ A Google account with Google Drive access
- ✅ Sufficient Google Drive storage space
- ✅ A valid Pixeldrain download link
- ✅ Internet connection

**No installation required!** Everything runs in Google Colab (free cloud service).

---

## 🚀 Quick Start Guide

### Step 1: Open the Notebook

Click the "Open in Colab" badge at the top of this README, or:

1. Go to [Google Colab](https://colab.research.google.com/)
2. Click `File` → `Open notebook`
3. Go to the `GitHub` tab
4. Paste: `NeelPatra/pixeldrain-gdrive-downloader`
5. Select `Pixeldrain_Downloader.ipynb`

### Step 2: Run Setup Cell

```python
# Cell 1: Setup Cell
# Click the ▶ play button or press Shift + Enter
```

This will:
- Connect to your Google Drive (you'll need to authorize)
- Create a download folder: `Pixeldrain_Downloads`
- Install aria2c downloader

**⏱️ Takes about 20-30 seconds**

### Step 3: Paste Your Link

```python
# Cell 2: Download Cell
# Find this line and replace with your link:
url = "https://pixeldrain.com/u/YOUR_FILE_ID"
```

### Step 4: Download!

Click the ▶ play button on Cell 2 and watch the magic happen!

**Your file will be saved to:**
```
Google Drive > My Drive > Pixeldrain_Downloads
```

---

## 📚 Detailed Usage Instructions

### Understanding the Two Cells

#### **Cell 1: Setup Cell** (Run once per session)
- Mounts Google Drive
- Creates download folder
- Installs aria2c
- Sets up the environment

#### **Cell 2: Download Cell** (Run for each download)
- Validates your Pixeldrain URL
- Converts to direct download link
- Downloads the file
- Shows progress and results

### Downloading Multiple Files

To download multiple files:

1. Keep the Setup cell running (don't restart)
2. Change the `url` in Cell 2
3. Run Cell 2 again
4. Repeat for each file!

### Customizing Download Location

Edit this line in **Cell 1**:

```python
download_folder = "/content/drive/MyDrive/YOUR_CUSTOM_FOLDER"
```

Example:
```python
download_folder = "/content/drive/MyDrive/My_Downloads/Pixeldrain"
```

---

## 📄 Sample Output

### Successful Download:
```
======================================================================
🔽 PIXELDRAIN TO GOOGLE DRIVE DOWNLOADER
======================================================================

🛠️ Starting setup process...

[1/3] Connecting to Google Drive...
  ✅ Google Drive connected successfully!

[2/3] Setting up download folder...
  🎯 Target: /content/drive/MyDrive/Pixeldrain_Downloads
  ✅ Download folder is ready!

[3/3] Installing aria2c (High-Speed Download Engine)...
  ⏳ This may take 10-20 seconds...
  ✅ aria2c installed successfully!

======================================================================
✅ SETUP COMPLETE! All systems ready.
======================================================================

[Step 1/3] Validating URL...
  ✅ Valid Pixeldrain URL!
  🆔 File ID: abc123

[Step 2/3] Converting to direct download link...
  ✅ Conversion complete!

[Step 3/3] Downloading file...
  🛠️ Starting high-speed download with aria2c...

======================================================================
✅ DOWNLOAD COMPLETE!
======================================================================
```

---

## 🗂️ Project Structure

```
pixeldrain-gdrive-downloader/
│
├── Pixeldrain_Downloader.ipynb    # Main notebook (2 cells)
│   ├── Cell 1: Setup Cell
│   └── Cell 2: Download Cell
│
├── README.md                      # Documentation (this file)
├── LICENSE                        # MIT License
└── .gitignore                     # Git ignore rules
```

---

## ⚙️ Advanced Configuration

### Adjusting Download Speed Settings

In **Cell 2**, modify these parameters:

```python
cmd = [
    "aria2c",
    "-x", "16",    # Connections (1-16) - Higher = faster but more bandwidth
    "-s", "16",    # Segments (1-16) - Higher = faster for large files
    "-k", "1M",    # Chunk size (1M, 5M, 10M) - Larger = fewer requests
    # ... other settings
]
```

**Recommended Settings:**

| File Size | Connections | Segments | Chunk Size |
|-----------|-------------|----------|------------|
| < 100 MB  | 8           | 8        | 1M         |
| 100MB-1GB | 16          | 16       | 1M         |
| > 1 GB    | 16          | 16       | 5M         |

### Adding Custom Features

The modular code structure makes it easy to add features:

**Want to add batch downloads?** Add a new function:
```python
def batch_download(url_list, output_path):
    for url in url_list:
        main(url, output_path)
```

**Want to add file size checking?** Create a new function:
```python
def check_file_size(url):
    # Your code here
    pass
```

---

## ⚠️ Troubleshooting

### Common Issues and Solutions

#### ❌ "Invalid Pixeldrain URL" Error

**Problem:** The URL format is incorrect

**Solution:**
```python
# ✅ Correct format:
url = "https://pixeldrain.com/u/abc123"

# ❌ Wrong formats:
url = "pixeldrain.com/u/abc123"           # Missing https://
url = "https://pixeldrain.com/abc123"    # Missing /u/
url = "https://pixdrain.com/u/abc123"    # Typo in domain
```

#### ❌ "Download Failed" Error

**Possible causes:**
1. File no longer exists on Pixeldrain
2. Not enough Google Drive storage
3. Network connection issues

**Solution:**
- Check the link in your browser first
- Free up Google Drive space
- Try restarting the runtime: `Runtime` → `Restart runtime`

#### ❌ "Permission Denied" Error

**Solution:**
1. Restart runtime: `Runtime` → `Restart runtime`
2. Run Setup cell again
3. Re-authorize Google Drive access

#### ❌ "aria2c not found" Error

**Solution:**
Run the Setup cell first! aria2c is installed in Cell 1.

---

## 欄 Contributing

Contributions make the open-source community amazing! Any contributions are **greatly appreciated**.

### How to Contribute

1. **Fork** the repository
2. **Create** a feature branch
   ```bash
   git checkout -b feature/AmazingFeature
   ```
3. **Commit** your changes
   ```bash
   git commit -m 'Add some AmazingFeature'
   ```
4. **Push** to the branch
   ```bash
   git push origin feature/AmazingFeature
   ```
5. **Open** a Pull Request

### Ideas for Contributions

- ✨ Add batch download support
- ✨ Add download history tracking
- ✨ Add email notifications on completion
- ✨ Improve UI/UX
- ✨ Improve documentation
- ✨ Fix bugs
- ✨ Add new features

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

**What this means:**
- ✅ Commercial use allowed
- ✅ Modification allowed
- ✅ Distribution allowed
- ✅ Private use allowed
- ⚠️ No warranty provided
- ⚠️ License and copyright notice must be included

---

## 🙇‍♂️ Acknowledgments

This project uses the following open-source tools:

- **[aria2c](https://aria2.github.io/)** - Lightning-fast download utility
- **[Pixeldrain](https://pixeldrain.com/)** - Free file hosting service
- **[Google Colab](https://colab.research.google.com/)** - Free cloud computing platform
- **[Python](https://www.python.org/)** - Programming language

Special thanks to:
- The aria2 development team
- Google Colab team
- The open-source community

---

## 📊 Statistics

![Python](https://img.shields.io/badge/Python-3.7+-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Active-success)
![Maintained](https://img.shields.io/badge/Maintained-Yes-brightgreen)

---

## 📬 Contact & Support

### Have Questions?

- Check the [FAQ section](#troubleshooting) first
- Found a bug? [Open an issue](https://github.com/NeelPatra/pixeldrain-gdrive-downloader/issues)
- Have a feature idea? [Start a discussion](https://github.com/NeelPatra/pixeldrain-gdrive-downloader/discussions)
- Email: abhranilpatra1@gmail.com

---

## ⭐ Show Your Support

If this project helped you, please consider:

- ⭐ **Starring** this repository
- 🔀 **Forking** it to make your own version
- 🔁 **Sharing** it with others who might find it useful
- 🗪 **Leaving feedback** in the discussions

Your support means a lot and helps me continue improving this project!

---

## 📋 Changelog

### [1.0.0] - 2024-11-28

**Added:**
- Initial release
- Single file download functionality
- URL validation
- Error handling with troubleshooting guides
- Progress tracking
- Modular code structure
- Comprehensive documentation

---

<div align="center">

**Made with ❤️ by Abhranil Patra**

*If this project helped you, consider giving it a ⭐!*

[⬆ Back to Top](#-pixeldrain-to-google-drive-downloader)

</div>
