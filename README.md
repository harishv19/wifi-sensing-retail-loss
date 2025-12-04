Wi-Fi Sensing for Smarter, Non-Intrusive Retail Loss Prevention
ISB Data Science Summit 2025 – Poster Presentation

Authors: A. Subramanian, Harish Vasudevan
Contact: subramanian.a@purplestraw.com

📝 Overview

Retail shrinkage continues to be a growing challenge, while traditional security systems—CCTV, RFID, guards—are often intrusive, expensive, or inefficient.

This project explores how Wi-Fi Channel State Information (CSI) can detect suspicious activity, item lifting, and unauthorized access without cameras, using ambient Wi-Fi signals.

This repository complements our poster presented at the ISB Data Science Summit 2025.

🎯 Objective

Develop an AI-driven Wi-Fi sensing system to:

Detect abnormal motion near high-value items

Distinguish browsing vs. pick-and-replace vs. lift-and-walk-away

Monitor stockroom access

Trigger real-time alerts

Operate non-intrusively using existing Wi-Fi infrastructure

🛰 How Wi-Fi Sensing Works

Human movement disturbs Wi-Fi signals. These variations in CSI amplitude and phase contain patterns that AI can analyze to detect actions.

Pipeline
1. Wi-Fi CSI Capture

Commodity routers / Raspberry Pi / Intel 5300

Capture per-subcarrier amplitude & phase

2. Preprocessing

Noise filtering

Phase sanitization

PCA / STFT to generate spectrograms

3. AI/ML Models

CNN + LSTM classifiers

Anomaly detection for rare events (e.g., item lifting)

4. Inference

Real-time action detection

Alert generation for suspicious activity

🏬 Retail Use-Cases

Detect lift-and-take events from shelves

Identify after-hours intrusions

Monitor high-value product displays

Differentiate normal browsing from potential theft

Reduce false alarms vs PIR motion sensors

Provide a privacy-preserving alternative to CCTV

🔧 Prototype Roadmap
Phase 1 — CSI Capture

Nexmon CSI on Raspberry Pi

Intel 5300 CSI tool

Controlled-environment trials

Dataset creation (browse, pick, lift)

Phase 2 — Feature Extraction

STFT-based spectrograms

PCA / ICA

Doppler energy features

Subcarrier variance tracking

Phase 3 — Modeling

CNN for pick-vs-lift classification

One-class anomaly detectors

Temporal segmentation using LSTMs/Transformers

Phase 4 — Retail Simulation

High-value display mockup

Testing in crowded vs empty aisles

Edge inference + optional fused sensors (load cell)

📊 Dataset Structure (Planned)
/data
   /raw_pcap
   /video_gt
   /processed
   labels.csv
   metadata.json


raw_pcap: raw CSI packets
video_gt: ground-truth videos
processed: CSI matrices & spectrograms
labels.csv: per-trial annotations

🖥 Quick Start (Prototype)
# 1. Capture CSI (Nexmon Example)
sudo tcpdump -i wlan0 udp port 5500 -w trial001_csi.pcap

# 2. Parse CSI
python parse_csi.py --pcap trial001_csi.pcap --out trial001.csv

# 3. Train Model
python train_model.py --data data/processed --epochs 20


(Placeholder scripts — the final pipeline will evolve.)

🧠 Intuition: The Airplane Analogy

Just as a flying airplane transfers momentum to the ground through moving air—detectable with highly sensitive sensors—
human motion disturbs the Wi-Fi field, and CSI captures these disturbances.

AI models learn to classify these subtle patterns, enabling activity recognition without cameras or wearables.

🔗 References & Background
Poster PDF (ISB 2025)
The AI Advantage: Utilizing Wi-Fi Sensing for Retail Loss Prevention
IEEE 802.11bf (Wi-Fi Sensing Standard)
Nexmon CSI Tool
Intel 5300 CSI Tool
Origin Wireless / Linksys Aware

📬 Contact
For collaboration or discussion:
📧 subramanian.a@purplestraw.co
