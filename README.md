# jsScraper
![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Repo Size](https://img.shields.io/github/repo-size/exe249/jsScraper)
![Last Commit](https://img.shields.io/github/last-commit/exe249/jsScraper)
![Issues](https://img.shields.io/github/issues/exe249/jsScraper)

> 🔍 A comprehensive, Python-based JavaScript scraping and archiving tool built on Playwright. Designed for security researchers, bug bounty hunters, developers, and analysts to extract, filter, and save JavaScript files (external & inline) from any target website.

---

## 🚀 Overview

**jsScraper** allows you to scan web pages for JavaScript files — both external and inline — and archive them with options to:

* Filter out common libraries and tracking scripts
* Deduplicate using SHA-256 hashes
* Crawl internal pages
* Collect cross-origin resources (optional)
* Generate verbose output logs
* Process entire URL lists

Its powerful combination of **asynchronous scraping**, **Playwright automation**, and **smart filtering** makes it suitable for recon, compliance, forensics, and competitive intelligence.

---

## ⚙️ Features

| Feature                   | Description                                                            |
| ------------------------- | ---------------------------------------------------------------------- |
| 📂 External JS Collection | Captures all loaded `.js` files on target page                         |
| 🧠 Inline Script Parsing  | Extracts `<script>` blocks from HTML content                           |
| ✂️ Filtering Engine       | Removes tracking scripts, analytics, and known libraries using regex   |
| 🔄 Deduplication          | Saves only unique scripts based on SHA-256 hash                        |
| 🌐 Crawling               | Optional crawling of internal links up to specified depth              |
| 🏁 Cross-Origin Capture   | Capture JS from third-party domains if required                        |
| 🪵 Logging                | Verbose log file (`verbose.log`) and clean CLI logging                 |
| 🧪 Batch Mode             | Accepts a list of target URLs from file                                |

---

## 🧰 Requirements

* Python 3.8+
* Dependencies:

  * `playwright`
  * `validators`
  * `beautifulsoup4`

### 🔧 Setup Instructions

```bash
git clone https://github.com/exe249/jsScraper.git
cd jsScraper
pip install -r requirements.txt
playwright install
```

---

## 🧪 Usage Examples

### 📄 Basic Usage

```bash
python jsScraper.py https://example.com
```

### 🔁 From URL File

```bash
python jsScraper.py --url-file urls.txt
```

### ⚙️ Full Options

```bash
python jsScraper.py https://example.com \
  --output output_dir \
  --filter strict \
  --min-size 200 \
  --crawl \
  --max-depth 2 \
  --cross-origin \
  --clear \
  --verbose
```

---

## 🧾 CLI Arguments

| Argument         | Description                                                           |
| ---------------- | --------------------------------------------------------------------- |
| `url`            | Target website to scrape (e.g., [https://site.com](https://site.com)) |
| `--url-file`     | Path to file with list of URLs (overrides `url`)                      |
| `-o, --output`   | Output directory (default: `getJsOutput`)                             |
| `--filter`       | Filtering mode: `strict` (default) or `relaxed`                       |
| `--min-size`     | Minimum file size in bytes (default: 150)                             |
| `--crawl`        | Enable crawling of internal links                                     |
| `--max-depth`    | Max depth for crawling (default: 2)                                   |
| `--cross-origin` | Include third-party JS                                                |
| `--clear`        | Clear output folder before writing new data                           |
| `-t, --timeout`  | Page timeout in seconds (default: 60)                                 |
| `-r, --delay`    | Delay between downloads in seconds (default: 0.5)                     |
| `-v, --verbose`  | Enable verbose logging (saved to `verbose.log`)                       |

---

## 📁 Output Structure

Files are saved as:

```
<output_dir>/<domain>/<filter_mode>/
  ├── example_com_main_f3ab23d4.js
  ├── example_com_inline_1a2b3c4d.js
  ├── ...
  └── verbose.log
```

Each JS file is uniquely named using:

* Domain
* Path
* Content hash (SHA-256, first 8 chars)

---

## 🧠 Use Cases

### 🔐 Security Research

* Extract inline secrets, endpoints, or tokens
* Identify outdated/vulnerable JS libraries
* Use in bug bounty / recon workflows

### 🧾 Web Archiving / Forensics

* Archive all JS on a domain for future analysis
* Identify scripts used in past attacks or shady behavior

---

## 📋 Filtering Modes

* **strict**: Blocks most common analytics, CDNs, libraries
* **relaxed**: Allows more JS through (themes, plugins, etc)

Custom patterns can be added to `UNINTERESTING_JS_STRICT` and `UNINTERESTING_JS_RELAXED` in the script.

---

## 📦 requirements.txt

```txt
playwright
validators
beautifulsoup4
```

---

## 🛡 License

**MIT License** — Free to use, modify, and redistribute. See `LICENSE` for details.

---

## 🤝 Contributing

Contributions are welcome — whether it's a feature idea, bug fix, optimization, or doc update!

### 🚀 Ways to Contribute

- Open a pull request with your improvements
- Create an issue for bug reports or suggestions
- Discuss new ideas via issues or discussions

### 💡 Feature Ideas (Open for Contribution)

- 🔍 Plugin engine (e.g., secrets detection, URL extraction, JS analysis)
- 🎨 JS beautification / deobfuscation support
- 📊 JSON-based summary reports
- 🐳 Docker wrapper for easy deployment


---

## 👨‍💻 Author

Developed by **[249BUG](https://github.com/exe249)** — built for recon professionals, security analysts, and digital investigators.
