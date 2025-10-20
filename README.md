```markdown
# Agentic Multi-Modal Intelligence for Real-Time Disaster Prediction, Situational Awareness & Response

MSc Data Analytics project by **Syed Arshadul Haque (UP2280648)**.  
This repo outlines an end-to-end, AI-driven pipeline that turns raw **drone video** into **actionable intelligence** for disaster response: scene/key-frame extraction → human detection → scene captioning → consolidated summarization → disaster-type classification → interactive Q&A. :contentReference[oaicite:0]{index=0}

---

## ✨ Key Features
- **Scene Detection & Key-Frames:** Extracts unique segments from raw video (PySceneDetect). :contentReference[oaicite:1]{index=1}  
- **Human Detection (on-edge capable):** YOLOv5 / YOLOv8 (n/m/l) across key frames for rapid survivor triage. :contentReference[oaicite:2]{index=2}  
- **Scene-wise Captioning:** Google Gemini 1.5 Flash generates rich, disaster-aware descriptions. :contentReference[oaicite:3]{index=3}  
- **Summary Synthesis:** Consolidates frame captions into one disaster summary. :contentReference[oaicite:4]{index=4}  
- **Disaster Classification:** RF, Decision Tree, Multinomial NB, and fine-tuned **BERT/RoBERTa** on a curated text dataset (e.g., Flood, Earthquake, Cyclone). :contentReference[oaicite:5]{index=5}  
- **Chat Interface:** LLM-powered Q&A over the analyzed video content for fast, context-aware insight. :contentReference[oaicite:6]{index=6}

---

## 🗺️ System Architecture (High Level)
1. **Input Layer:** Drone video (H.264 recommended).  
2. **Pre-Processing:** Scene detection → key-frame extraction.  
3. **AI Processing:**
   - Human detection (YOLOv5 / YOLOv8n/m/l)
   - Frame-level captions (Gemini 1.5 Flash)
   - Consolidated video-level summary
   - Disaster-type classification (TF-IDF + ML; fine-tuned BERT/RoBERTa)  
4. **Interaction Layer:** Chatbot (Gemini-powered) for operator queries. :contentReference[oaicite:7]{index=7}

---

## 📊 Data
- **Primary Source:** Public drone videos (e.g., YouTube) for scenes & frames.  
- **Text Dataset:** Curated `(disaster_description, disaster_label)` pairs for training/testing classifiers.  
- **Evaluation:** Accuracy/precision/recall/F1 for classifiers; qualitative checks for detection/captioning. :contentReference[oaicite:8]{index=8}

---

## 🧪 Models & Modules
- **Scene Detection:** PySceneDetect.  
- **Detectors:** YOLOv5; YOLOv8 (n/m/l) — speed/accuracy trade-offs documented.  
- **Captioning/Summary:** Google Gemini 1.5 Flash (multimodal).  
- **Classifiers:** RandomForest, DecisionTree, MultinomialNB, fine-tuned **BERT** & **RoBERTa**.  
- **Chat:** Gemini-backed Q&A using scene captions + summary context. :contentReference[oaicite:9]{index=9}

---

## ✅ What This Solves (Why It’s Novel)
- Integrates **video parsing + detection + captioning + summarization + classification + Q&A** into one practical pipeline for **first 72-hour** response windows.  
- Designed for **edge deployment** on UAVs (efficiency + safety), reducing reliance on risky manned surveys. :contentReference[oaicite:10]{index=10}

---

## 🚀 Quickstart (Reference)
> Exact code paths and notebooks are referenced in the report; adapt these commands to your repo structure.

1. **Prepare video**
   ```bash
   # Ensure H.264 for reliable processing
   ffmpeg -i input.mp4 -vcodec libx264 -crf 18 -preset fast input_h264.mp4
   ```
2. **Detect scenes & extract key frames**
   ```bash
   python tools/scene_detect.py --video input_h264.mp4 --out frames/
   ```
3. **Run human detection**
   ```bash
   python tools/detect_yolo.py --frames frames/ --model yolov8n  # or yolov5/yolov8m/yolov8l
   ```
4. **Generate captions & summary (Gemini)**
   ```bash
   python tools/caption_and_summarize.py --frames frames/ --out summary.json
   ```
5. **Classify disaster type**
   ```bash
   python models/classify.py --summary summary.json --checkpoint checkpoints/bert_finetuned.pt
   ```
6. **Launch chatbot**
   ```bash
   python apps/chatbot.py --context summary.json
   ```
:contentReference[oaicite:11]{index=11}

---

## 📁 Suggested Repo Structure
```
.
├─ tools/
│  ├─ scene_detect.py
│  ├─ detect_yolo.py
│  └─ caption_and_summarize.py
├─ models/
│  ├─ train_traditional_ml.py
│  ├─ finetune_bert.py
│  ├─ finetune_roberta.py
│  └─ classify.py
├─ apps/
│  └─ chatbot.py
├─ data/
│  ├─ raw_video/
│  ├─ frames/
│  └─ text_dataset/
└─ checkpoints/
```
:contentReference[oaicite:12]{index=12}

---

## 🔍 Evaluation Snapshot
- Comparative results for YOLO variants (human detection) and five classifiers (incl. BERT/RoBERTa); bar-chart comparison and confusion-matrix analyses included in the report’s Results section.  
- Requirements evaluation (functional & non-functional), limitations, and future work are summarized in Chapters 8–9. :contentReference[oaicite:13]{index=13}

---

## ⚖️ Ethics, Legal & Professional
- Ethics approval obtained; GDPR/PII awareness; responsible AI and deployment considerations documented. :contentReference[oaicite:14]{index=14}

---

## 🛣️ Roadmap (Future Work)
- Edge acceleration (quantization/pruning for on-drone inference)  
- Larger/augmented multimodal datasets (incl. synthetic imagery)  
- Active learning from field feedback; expanded disaster classes; geospatial fusion (GIS). :contentReference[oaicite:15]{index=15}

---

## 📚 Citation
If you use this work, please cite the dissertation:
> Haque, S. A. (2025). *Agentic Multi-Modal Intelligence for Real-Time Disaster Prediction, Situational Awareness, and Response* (MSc Data Analytics). University of Portsmouth. :contentReference[oaicite:16]{index=16}
```
