# Agentic Multi-Modal Intelligence for Real-Time Disaster Prediction, Situational Awareness & Response

MSc Data Analytics project by **Syed Arshadul Haque (UP2280648)**  

This project presents an end-to-end, AI-driven pipeline that transforms raw **drone video footage** into **actionable intelligence** for real-time disaster response. The system performs scene detection, human detection, caption generation, summarization, disaster-type classification, and supports interactive Q&A.

---

## ✨ Key Features
- **Scene Detection & Key-Frame Extraction:** Detects distinct video segments using PySceneDetect.  
- **Human Detection:** Employs YOLOv5 and YOLOv8 variants (n/m/l) for efficient survivor identification.  
- **Scene Captioning:** Generates contextual captions with Google Gemini 1.5 Flash.  
- **Summary Synthesis:** Merges captions into a coherent disaster narrative.  
- **Disaster Classification:** Uses Random Forest, Decision Tree, Multinomial NB, and fine-tuned BERT / RoBERTa models to categorize events such as floods, earthquakes, or cyclones.  
- **Interactive Chat:** Enables LLM-based conversation over analyzed results for rapid insights.

---

## 🗺️ System Architecture
1. **Input Layer:** Drone video (H.264 format recommended).  
2. **Pre-Processing:** Scene detection followed by key-frame extraction.  
3. **AI Processing:**  
   - Human detection via YOLO models  
   - Frame-level captioning with Gemini 1.5 Flash  
   - Summary generation  
   - Disaster classification using traditional ML and fine-tuned transformers  
4. **Interaction Layer:** Chatbot for operator Q&A and situational decision support.

---

## 📊 Data Overview
- **Sources:** Public drone videos and curated textual datasets pairing disaster descriptions with labeled types.  
- **Evaluation Metrics:** Accuracy, precision, recall, and F1-score for classifiers; qualitative validation for detection and captioning outputs.

---

## 🧪 Models and Modules
- **Scene Detection:** PySceneDetect  
- **Human Detection:** YOLOv5, YOLOv8 (n/m/l)  
- **Captioning & Summarization:** Gemini 1.5 Flash (multimodal)  
- **Text Classification:** Random Forest, Decision Tree, Multinomial NB, BERT, and RoBERTa  
- **Chat Interface:** Gemini-based conversational layer leveraging summary context

---

## ✅ Novel Contributions
- Integrates multiple AI capabilities—vision, language, summarization, and dialogue—into one cohesive pipeline.  
- Supports **edge deployment** on UAVs to minimize risk to human responders.  
- Provides **real-time situational awareness** within the critical first 72 hours of a disaster.

---

## 🔍 Evaluation Highlights
- Comparative benchmarks for YOLO variants and all five classifiers (including BERT and RoBERTa).  
- Visual analyses using accuracy charts and confusion matrices.  
- Requirement validation, limitations, and future improvements thoroughly discussed.

---

## ⚖️ Ethics, Legal & Professional Aspects
- Ethics approval secured.  
- Adherence to GDPR and responsible AI principles.  
- Focus on safe data handling and ethical deployment in disaster contexts.

---

## 🛣️ Future Roadmap
- Model compression and quantization for edge inference.  
- Expanded and synthetic multimodal datasets.  
- Active learning loops and GIS integration for location-aware insights.  

---

## 📚 Citation
If you use this work, please cite:

**Haque, S. A. (2025).** *Agentic Multi-Modal Intelligence for Real-Time Disaster Prediction, Situational Awareness and Response.* MSc Data Analytics, University of Portsmouth.
