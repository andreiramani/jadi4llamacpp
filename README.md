![logo](jadi4llamacpp_02.png)

## Limitations
This project currently provides **binary builds only for Microsoft Windows**. Other operating systems (Linux, macOS, etc.) are not supported at this time.

## Overview
This project is part of my personal use case. I often experiment with various LLM applications on **Microsoft Windows OS** with **NVIDIA CUDA GPU** support. One of the tools I use heavily is **llama.cpp**, since it provides one of the simplest and lightest ways to run LLMs locally on Windows.
Unfortunately, llama.cpp sometimes fails to load certain "Eastern" LLM models (such as **Qwen** or **DeepSeek-like** like formats), even when using the most recent source code.  

To address this limitation, I pre-compiled **[jadi4llamacpp](https://github.com/andreiramani/jadi4llamacpp)** - to ensures my llama.cpp binary can fully recognize and work with Qwen-like, DeepSeek-like, and similar model formats.

## Goal
- Extend llama.cpp compatibility with additional model formats (bridging "Eastern" and "Western" llm model :).
- (Specifically) Provide a reliable way to run Qwen and DeepSeek-like variant models locally on Windows.
- Keep the workflow simple and lightweight, just like the original llama.cpp.

## [Releases](https://github.com/andreiramani/jadi4llamacpp/releases)
Currently provide two versions:
- **WS (Workstation)**: Designed for desktop and laptop with CPU-only or NVIDIA CUDA GPUs.  
- **DC (Data Center)**: An experimental build intended for data center–grade NVIDIA CUDA GPUs.

The WS version is my primary release for everyday local use, while the DC version is an experiment to explore compatibility and performance on high-end, server-class hardware.

## GPU Compute Compiler Selection
For each version, I carefully selected the **GPU compute compiler targets** to ensure **optimal performance** across different GPU series.  

It’s worth noting that some compute capability versions are identical between consumer and enterprise GPUs (for example: **7.5, 8.6, 8.9, 12.0**).

## Maintenance
I cannot guarantee continuous maintenance of these releases. As long as I actively use **llama.cpp**, I will try to provide periodic updates - especially for the **WS (Workstation)** version.  

The **DC (Data Center)** build is more of an experiment, and honestly, I doubt anyone would seriously run llama.cpp on a data center–grade GPU under bare-metal Windows Server (though if someone does, that would be quite impressive!).

## How-To

### If you are familiar with llama.cpp on Windows
1. Download the release (choose the version that best fits your setup).  
2. Extract the files into your existing **llama.cpp** folder.  
3. When prompted with the overwrite dialog, select **Yes**.  
4. If you are unsure, make a backup of your existing `.exe` and `.dll` files before overwriting.

### If you are new to llama.cpp
1. Extract the **[jadi4llamacpp](https://github.com/andreiramani/jadi4llamacpp)** release into a folder of your choice.  
2. Download a **GGUF model**:
   - For **CPU inference** only, avoid using very large models. As a general recommendations: choose smaller precision (like 4-bit), and the model size should not exceed **one third of your system RAM**.  
   - For **CUDA GPU inference**, ensure the model size is smaller than your GPU’s VRAM capacity.  
3. For easier setup, place the model file in the same folder where you extracted **[jadi4llamacpp](https://github.com/andreiramani/jadi4llamacpp)**.  
4. Open a **Command Prompt** in the [jadi4llamacpp](https://github.com/andreiramani/jadi4llamacpp) folder and run one of the following:

   - **CLI interactive mode**:  
     ```bash
     llama-cli -m <your-gguf-file>
     ```

   - **Browser-based mode**:  
     ```bash
     llama-server -m <your-gguf-file> --port <port-number>
     ```
     Then open your browser and go to:  
     ```
     http://127.0.0.1:<port-number>
     ```
     to access the llama.cpp interface.

## NVIDIA GPU Support List

<details>
<summary>🖥️ WS (Workstation) Version</summary>

Supported desktop and laptop GPUs with NVIDIA CUDA:

- **Quadro RTX Series**  
  - RTX 8000, RTX 6000, RTX 5000, RTX 4000, RTX 3000  
  - Quadro T2000, NVIDIA T1200, T1000, T600, T500, T400  

- **GeForce GTX / TITAN**  
  - GeForce GTX 1650 Ti  
  - NVIDIA TITAN RTX  

- **GeForce RTX 20 Series**  
  - RTX 2080 Ti, RTX 2080, RTX 2070, RTX 2060  

- **NVIDIA RTX A Series**  
  - RTX A6000, A5000, A4000, A3000, A2000  

- **GeForce RTX 30 Series**  
  - RTX 3090 Ti, RTX 3090, RTX 3080 Ti, RTX 3080  
  - RTX 3070 Ti, RTX 3070, RTX 3060 Ti, RTX 3060  
  - RTX 3050 Ti, RTX 3050  

- **NVIDIA RTX Ada Series**  
  - RTX 6000 Ada, RTX 5000 Ada, RTX 4500 Ada  
  - RTX 4000 Ada, RTX 4000 SFF Ada, RTX 2000 Ada  

- **GeForce RTX 40 Series**  
  - RTX 4090, RTX 4080, RTX 4070 Ti, RTX 4070  
  - RTX 4060 Ti, RTX 4060, RTX 4050  

- **NVIDIA RTX PRO Blackwell (Workstation)**  
  - RTX PRO 6000 (Workstation Edition, Max-Q Edition)  
  - RTX PRO 5000 Blackwell  
  - RTX PRO 4500 Blackwell  
  - RTX PRO 4000 Blackwell, RTX PRO 4000 SFF Edition  
  - RTX PRO 2000 Blackwell  

- **GeForce RTX 50 Series**  
  - RTX 5090, RTX 5080, RTX 5070 Ti, RTX 5070  
  - RTX 5060 Ti, RTX 5060, RTX 5050  

</details>

---

<details>
<summary>🏢 DC (Data Center) Version</summary>

Supported data center–grade NVIDIA GPUs:

- **Ampere Series**  
  - A100, A40, A30, A10, A16, A2  

- **L Series**  
  - L4, L40, L40S  

- **Hopper / Grace Hopper Series**  
  - GH200, H200, H100  

- **Blackwell Series**  
  - GB300, B300, GB200, B200  

- **NVIDIA RTX PRO Blackwell (Server)**  
  - RTX PRO 6000 Blackwell Server Edition  

</details>

## Other Docs
Please read from [llama.cpp wiki's](https://github.com/ggml-org/llama.cpp/wiki)
