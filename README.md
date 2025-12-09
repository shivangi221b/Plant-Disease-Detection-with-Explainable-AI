# 🌱 Plant Disease Detection with Explainable AI

**EfficientNetB3 | GRAD-CAM | LIME | Gemini/Llama2/Mistral Treatment Recommendations**

This project provides an AI-powered plant disease diagnosis system with Explainable AI (XAI) visualizations and a fully interactive Streamlit UI. It runs locally, using a single .py file that includes model loading, inference, GRAD-CAM/LIME explanations, and LLM integration.

**Local Installation Guide for Windows & macOS**

This repository provides a complete end-to-end pipeline for plant disease classification, including:

- Automatic dataset download & preprocessing
- Fine-tuned EfficientNetB3 classifier (92.3% accuracy)
- Real-time inference through a Streamlit UI
- Visual explanations using GRAD-CAM & LIME
- AI-generated treatment recommendations via LLMs (Gemini, Llama2, Mistral)
- A single .py file that runs the entire application locally

---

## **Features**

- ✅ EfficientNetB3 deep learning model for plant disease classification (38 disease classes)
- ✅ GRAD-CAM image & text explanations (0.08s inference)
- ✅ LIME image & text explanations (3-5s inference)
- ✅ Beautiful Streamlit UI for interactive uploads with button-driven workflow
- ✅ Multiple LLM backends: Gemini 2.5 Flash (cloud), Llama2 (local), Mistral (local)
- ✅ Side-by-side image/heatmap visualization
- ✅ Top-5 disease predictions with confidence scores
- ✅ Fully standalone .py script (no separate API calls needed)

---

## **⚠️ IMPORTANT NOTES BEFORE RUNNING**

### **API Key Setup (Required for LLM Features)**

This project uses Large Language Models to generate treatment recommendations. You **must configure your API keys** before running:

#### **Option 1: Gemini 2.5 Flash (Recommended - Free Tier)**
1. Go to [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Create a free API key
3. In `plant_disease_detection.py`, update line:
   ```python
   os.environ['GEMINI_API_KEY'] = 'YOUR_API_KEY_HERE'
   ```

#### **Option 2: Llama2 & Mistral (Local - No API Key Needed)**
1. Install [Ollama](https://ollama.ai/)
2. Download models locally:
   ```bash
   ollama pull llama2
   ollama pull mistral
   ```
3. Start Ollama server:
   ```bash
   ollama serve
   ```
4. Keep the terminal running while using the app

### **⏱️ Performance Warning**

- **First-time startup:** 2-5 minutes (model loading)
- **Each analysis:** 1-2 minutes per image
- **LLM inference is the bottleneck** (especially Llama2/Mistral on CPU)
- *Note: Latency optimization is a priority for future versions.*

---

## **How to Run Locally**

### **1. Prerequisites**

- Python 3.10 – 3.12
- Git (optional, for cloning repo)
- The following files in the same folder:
  - `plant_disease_detection.py`
  - `best_model.pth` (pre-trained model weights)
  - `requirements.txt` (dependencies list)

### **2. 🛠️ Installation**

**Step 1 — Clone or Download Repository**
```bash
git clone <repo-url>
cd plant-disease-detection
```

**Step 2 — Create Virtual Environment (Recommended)**
```bash
python -m venv venv
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
```

**Step 3 — Install Dependencies**
```bash
pip install -r requirements.txt
```

### **3. 📁 Project Folder Structure**

```
project/
│── plant_disease_detection.py
│── best_model.pth
│── requirements.txt
│── README.md
│
├── data/
│   └── plant_village/
│       └── images/
│           ├── Apple___Apple_scab/
│           ├── Potato___Late_blight/
│           └── ... (36 more disease folders)
│
└── models/
    └── fine_tuned/
        └── best_model.pth
```

### **4. ▶️ Running the Streamlit App**

Once installed, simply run:

```bash
streamlit run plant_disease_detection.py
```

- Streamlit will launch automatically in your browser at: `http://localhost:8501`
- **Wait 2-5 minutes for initial model loading** (first time only)
- Upload a leaf image to get started

---

## **Usage Workflow**

1. **Upload Image** — Click file uploader to select a JPG/PNG/BMP leaf image
2. **View Results** — See disease prediction, confidence score, heatmap, and treatment recommendations
3. **Select LLM** — Choose between Gemini (cloud), Llama2 (local), or Mistral (local) from sidebar
4. **Review Top-5** — Expand to see alternative predictions with confidence scores

---

## **Troubleshooting**

### **Issue: "GEMINI_API_KEY not found"**
- **Solution:** Add your Gemini API key to the code (see API Key Setup section above)

### **Issue: "Ollama not running"**
- **Solution:** Start Ollama with `ollama serve` in a separate terminal before running the app

### **Issue: Very slow inference (30+ seconds)**
- **Solution:** Check if you're using Llama2 on CPU (slow). Switch to Gemini (cloud) or use GPU if available

### **Issue: Model file not found**
- **Solution:** Ensure `best_model.pth` is in the same directory as the .py file, or download from the GitHub releases
