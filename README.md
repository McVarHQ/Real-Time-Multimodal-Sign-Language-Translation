# Real-Time Multimodal Sign Language Detection

---

## 🔍 Overview

**Real-Time Multimodal Sign Language Detection** is a proof-of-concept prototype for **American Sign Language (ASL) translation**.  
The system leverages **ESP32-based wireless communication** with a **Raspberry Pi**, which runs a lightweight deep learning model to detect and translate ASL gestures in real-time.  

This project anticipates integration into wearable devices (e.g., **smartwatches, AR glasses**) for fluid and non-intrusive sign language translation.  
The key challenge addressed was designing and optimizing a model that is both **compact** and **accurate**, ensuring deployment feasibility on **resource-constrained SoCs**.

---

## 📜 Abstract

Sign language serves as a vital communication medium for the Deaf and Hard of Hearing (DHH) community. However, real-time and mobile sign-to-speech translation remains an open challenge.  

This project demonstrates a multimodal framework:  
- **Data Acquisition**: Leveraged WLASL dataset for word-level ASL recognition.  
- **Feature Extraction**: Used **pose landmarks** and skeletal keypoints from video sequences.  
- **Model Development**: Built and evaluated models combining temporal and spatial features, optimized for embedded deployment.  
- **Deployment**: The trained model was integrated on a Raspberry Pi prototype communicating with ESP32, demonstrating end-to-end wireless translation.  

The system proves the viability of **edge-deployable ASL recognition** and sets the groundwork for wearable sign language interpreters.

---

## ⚙️ Core Components

### 1. Dataset: WLASL
- Utilized **Word-Level American Sign Language (WLASL)** dataset.  
- Processed with subsets of **100, 300, 1000, and 2000 classes** (`nslt_*.json`).  
- Preprocessing steps included landmark extraction, missing data checks, and label formatting.  

### 2. Landmark Extraction
- Extracted **pose and hand landmarks** from ASL videos.  
- Generated intermediate representations for model training.  
- Landmarks stored in `.npz` and text formats (`labels.npz`, `final_labels.txt`).  

### 3. Model Development
- Built multimodal translation pipelines in:  
  - `mutemotion-wlasl-translation-model.ipynb`  
  - `Signer2.ipynb`  
- Employed **temporal sequence learning** for motion dynamics.  
- Optimized models for **low-memory footprint**, targeting ESP32-class hardware.  

### 4. Deployment & Communication
- **ESP32 module** captured data wirelessly.  
- **Raspberry Pi** processed inference using the trained model.  
- Designed for future portability to wearable form factors.  

---

## 🎥 Demonstration

Watch the prototype in action:  
[![21BAI1499 | Real Time Multimodal Sign Language Detection Demo](https://img.youtube.com/vi/StTqXEQ2l-Y/0.jpg)](https://www.youtube.com/watch?v=q9amnUtUOjI "21BAI1499 | Real Time Multimodal Sign Language Detection Demo")


---

## 📂 Repository Structure

```
SIGNER_COLAB/
│
├── 📁 wlasl-complete/
│   ├── 🐍 find_missing.py
│   ├── 📄 missing.txt
│   ├── 📋 nslt_100.json
│   ├── 📋 nslt_300.json
│   ├── 📋 nslt_1000.json
│   ├── 📋 nslt_2000.json
│   └── 📄 wlasl_class_list.txt
│
├── 📁 working/
│   ├── 📁 landmarks/
│   ├── 📄 final_labels.txt
│   ├── 📄 labels_2
│   ├── 📄 labels.npz
│   ├── 🎥 landmarks_test.mp4
│   ├── 📓 mutemotion-wasl-translation-model.ipynb
│   └── 📓 Signer2.ipynb
```

### 📋 Directory Overview

| Directory/File | Description |
|----------------|-------------|
| `wlasl-complete/` | WLASL (Word-Level American Sign Language) dataset files |
| `├── find_missing.py` | Python script to identify missing data |
| `├── missing.txt` | List of missing entries |
| `├── nslt_*.json` | NSLT datasets with different vocabulary sizes (100, 300, 1000, 2000) |
| `└── wlasl_class_list.txt` | Complete class list for WLASL dataset |
| `working/` | Active development and processing files |
| `├── landmarks/` | Extracted landmark data directory |
| `├── final_labels.txt` | Processed label files |
| `├── labels_2` & `labels.npz` | Label data in different formats |
| `├── landmarks_test.mp4` | Test video for landmark extraction |
| `└── *.ipynb` | Jupyter notebooks for model development |

---

## ✅ Key Highlights
- **Multimodal approach** using landmarks + video dynamics.  
- **Lightweight architecture** designed for **resource-constrained devices**.  
- **Prototype deployment** on ESP32 + Raspberry Pi.  
- Anticipates **wearable integration** (watch, AR glasses) for fluid real-time translation.  

---
