# bug-free-journey

# 🎧 WMCodec-M2: Robust Audio Watermarking Red-Teaming & Defense System

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/YOUR_REPO_NAME/blob/main/WMCodec_Evaluation.ipynb)
[![Python 3.12](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/)
[![PyTorch 2.8](https://img.shields.io/badge/pytorch-2.8%2Bcu126-orange.svg)](https://pytorch.org/)
[![License MIT](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)

> **FIT5230 Milestone 3 Project - Champions of the World**
> A comprehensive security evaluation, advanced adversarial attack, and test-time defense framework for deep-learning-based Audio Watermarking (`WMCodec`).

---

## 🌟 Overview

This project builds a fully functional verification and security testing pipeline for the **WMCodec** audio watermarking system. Going beyond standard robustness tests, we implement state-of-the-art **Adversarial Red-Teaming Techniques** to systematically blindside decoders, balanced with adaptive **Test-Time Augmentation (TTA) and Notch-Filtering Defenses** to shield watermarks against aggressive distortions.

### 🛠️ Key Systems & Contributions
1. **End-to-End Evaluation Pipeline**: Auto-preprocessing (24kHz mono resampling and peak normalization), watermark embedding inference, and synchronized bit alignment.
2. **RHDE-Inspired Adversarial Attacker**: Combines **Band-Limited Audio "Stickers" (bursts/chirps)**, **Differential Evolution (DE) global search**, and **Projected Gradient Descent (PGD) optimization** to destroy watermarks under strict psychoacoustic constraints.
3. **Adaptive Test-Time Defense (Light Defense)**: Implements test-time augmentation (TTA) with soft-logits voting and a **Confidence-Driven Adaptive Notch Filter** to successfully recover watermarks from heavily corrupted channels.
4. **Deception & Misdirection Mechanics (Bonus Marks)**: Features covert tactical functions to mislead adversarial attribution and mitigate red-teaming bypasses.

---

## 🚀 Getting Started (Colab Workflow)

### 1. Installation & Environment Setup
Clone the core neural codec framework, install high-fidelity metrics suites (`pesq`, `pystoi`), and retrieve the pre-trained production model weights from HuggingFace via Git LFS:

```bash
# Clone evaluation core
!git clone [https://github.com/tianjingwen2000/WMCodec-M2.git](https://github.com/tianjingwen2000/WMCodec-M2.git)
!pip install -r WMCodec-M2/WMCodec/requirements.txt

# Fetch Pre-trained Checkpoints via LFS
!git lfs install
!git clone [https://huggingface.co/zjzser/WMCodec](https://huggingface.co/zjzser/WMCodec) WMCodec_hc

### 2. Operational Pipeline
The notebook is segmented into cleanly organized execution zones:
* **Section 1-2**: Environment configuration, model initialization, and high-fidelity target audio sampling standardizations.
* **Section 3**: Multi-channel Benchmark Attack Simulation (Reverb, Resampling down to 16kHz, MP3 bit-rate compression, Gaussian noise insertion) with automatic evaluation summaries.
* **Section 4**: Step-by-step Interactive Black-Box Evaluation suite mapping extracted bits against baseline ground-truth configurations using shifting tolerances.
* **Section 5-6**: Advanced Adversarial Synthesis (`Audio Sticker` implementation) and Confidence-Driven Anti-Adversarial filtering topologies.

---

## Security Metrics & Results Analysis
The evaluation core enforces synchronized string alignment using a $\pm64$-bit translation sliding window to account for temporal drift/clipping, calculating optimized Bit Error Rates (BER) and Extraction Accuracies (ACC).

### Benchmark Resilience Matrix
* **Intact Threshold**: $\text{ACC} \ge 0.95$ and $\text{BER} \le 0.05$ define successful watermark survival.
* **Vulnerabilities Discovered**: While `WMCodec` exhibits robust defense properties against standardized Gaussian noise and subtle resampling, high-frequency reverberation patterns and lossy low-bitrate MP3 conversions degrade local frame synchronization, calling for test-time intervention.

### Advanced Adversarial Attacks (Section 5)
By embedding an optimized band-limited noise "sticker" into high-energy speech regions using **Differential Evolution**, the red team successfully drives decoder cross-entropy loss to its maximum, inducing total decoding failure while retaining optimal perceptual audio quality ($>35\text{dB}$ SNR).

### Defensive Countermeasures Performance (Section 6)
Our **Confidence-Driven Test-Time Defense** counteracts both standard signal degradation and deliberate adversarial attacks:
* **Soft-Logits TTA Voting** restores frame phase coherence under minor time-stretch and pitch-shift attacks.
* **Adaptive Notch Filtering** scans the spectral bands and isolates the exact center frequencies of adversarial stickers, dropping the BER back below the detection limit and neutralizing advanced threats.

> 📝 **Note**: Visual evaluation summaries, bar charts, and verdict distribution pie charts are dynamically generated inside the `results_demo/` workspace upon notebook execution.

---

## 🕵️‍♂️ Covert Red-Teaming Tactics & Misuse Mitigation Report

### 1. Covert Misdirection & Attribution Confusion
To align with competitive engineering mechanics, the adversarial synthesis suite supports **Attribution Spoofing**. When constructing adversarial audio stickers, the system can selectively implant fake boundary artifacts mimicking the compression fingerprints of common third-party codecs (e.g., standard Fraunhofer MP3 boundaries). This effectively misleads automated defensive forensics into attributing the exploit to standard compression degradation rather than targeted optimization.

### 2. Misuse Mitigation Plan (Dual-Use Assessment)
Because high-efficiency adversarial stickers can bypass neural copyright detection, this repository enforces strict defensive compliance:
* **Red-Teaming Boundaries**: All gradient-refinement operations inside `pgd_refine` require explicit programmatic alignment with an immutable baseline ground-truth structure (`.wm.json`), preventing the tool from being used to forge arbitrary signatures.
* **Defensive Co-design**: The release of the advanced attacker is directly coupled with the `defend_adaptive_notch` module, guaranteeing that copyright owners can immediately neutralize these specific attack vectors at inference time.

---

## 👥 Team Collaboration & Contribution
* **Team Members**: Developed collaboratively within our AI graduate team at Monash University (FIT5230 Project Group).
* **Workload Split**: Distributed equally across core architectural engineering, adversarial red-teaming R&D, defensive signal processing, and reporting/visualization automation.

---

## 📜 License
This project is licensed under the **MIT License** - see the `LICENSE` file for details.
