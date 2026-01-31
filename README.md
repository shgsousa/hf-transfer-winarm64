# hf-transfer-qnn 🎡

**Ultra-fast Hugging Face Hub transfers for Windows ARM64 (Snapdragon X Elite/Plus).**

`hf-transfer-qnn` provides native, high-performance Python wheels for the [hf-transfer](https://github.com/huggingface/hf_transfer) library, specifically compiled for the **Windows ARM64** architecture. This library is a Rust-based alternative to the default `requests` backend in `huggingface_hub`, designed to maximize bandwidth during model downloads and uploads.

---

## 🚀 Why use this on Snapdragon?

Windows ARM64 users often face "dependency hell" when trying to install Rust-based AI tools. By using our pre-compiled wheels:
* **Maximized Bandwidth:** Move beyond the ~500MB/s Python cap and fully utilize high-speed Fiber or 5G connections on your Snapdragon laptop.
* **Native Efficiency:** Compiled with MSVC for ARM64, ensuring optimal execution on the Oryon CPU cores.
* **No Compiler Needed:** Skip the `rustc` and `maturin` setup; just install the wheel and go.

---

## 🛠 Installation

You can install the native wheel directly from our GitHub Releases:

```bash
pip install hf-transfer --extra-index-url [https://github.com/Snapdragon-AI-Stack/hf-transfer-qnn/releases/latest](https://github.com/Snapdragon-AI-Stack/hf-transfer-qnn/releases/latest)

```

---

## 📖 Usage

Once installed, you must enable the transfer acceleration via an environment variable.

### 1. Enable in your Shell

**PowerShell:**

```powershell
$env:HF_HUB_ENABLE_HF_TRANSFER = 1

```

**Command Prompt:**

```cmd
set HF_HUB_ENABLE_HF_TRANSFER=1

```

### 2. Use in Python

No code changes are required. The `huggingface_hub` library will automatically detect the accelerated backend.

```python
from huggingface_hub import snapshot_download

# This will now use the hf-transfer Rust backend
snapshot_download(repo_id="Snapdragon-AI-Stack/models", repo_type="model")

```

---

## 🏗️ Build & CI/CD

This repository uses GitHub Actions to automate the cross-compilation of wheels for:

* **Python Versions:** 3.10, 3.11, 3.12, 3.13
* **Platform:** Windows 11 ARM64 (`win_arm64`)

Check the [Actions tab](https://www.google.com/search?q=https://github.com/Snapdragon-AI-Stack/hf-transfer-qnn/actions) for the latest build logs and artifact generation.

---

## ⚖️ License & Credits

* Original library by [Hugging Face](https://github.com/huggingface/hf_transfer).
* ARM64 build infrastructure provided by the [Snapdragon-AI-Stack](https://www.google.com/search?q=https://github.com/Snapdragon-AI-Stack).
* Distributed under the **Apache License 2.0**.
