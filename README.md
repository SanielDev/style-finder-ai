# 👗 Style Finder: AI-Powered Fashion Analysis Web App

**Style Finder** is an AI-driven, multimodal Retrieval-Augmented Generation (RAG) system that analyzes fashion images and provides catalog-style clothing insights in real time. Built using computer vision, vector similarity search, and the Meta LLaMA 3.2 90B Vision Instruct model, this project delivers intelligent recommendations and analysis of fashion items inspired by Taylor Swift’s iconic wardrobe.

![Style Finder Demo](https://user-images.githubusercontent.com/your-gif-or-image.gif)

---

## 🚀 Features

- 🖼️ Upload a fashion image and receive a full catalog-style analysis
- 🤖 Combines ResNet50 + Vision LLM (LLaMA 3.2) for multimodal reasoning
- 🔎 Finds visually similar outfits via cosine similarity search
- 🛍️ Returns real product names, prices, and purchase links
- 💬 Generates markdown-formatted descriptions using Watsonx LLM
- 🧠 Built using modular, scalable architecture (CV + RAG + LLM)
- 🌐 Interactive interface with [Gradio](https://www.gradio.app/)

---

## 📷 Sample Use Case

> Upload an image of an outfit. The system identifies its visual elements (color, pattern, material), compares it to a Taylor Swift-inspired dataset, and outputs:
>
> - Garment descriptions
> - Outfit style (e.g. casual, formal)
> - Similar purchasable items with prices & links

---

## 🧠 Tech Stack

| Component        | Tool/Library                                  |
|------------------|-----------------------------------------------|
| 👁️ Computer Vision | ResNet50 (TorchVision)                        |
| 🧠 LLM Model       | Meta LLaMA 3.2 Vision Instruct via IBM Watsonx |
| 🔍 Retrieval       | Cosine similarity with Scikit-Learn           |
| 🧾 UI Interface    | Gradio Blocks UI                              |
| 🧪 Dataset         | Curated from [TaylorSwiftStyle.com](https://taylorswiftstyle.com/) |
| 🗂️ File Format     | Pre-encoded `.pkl` with image embeddings      |

---

## 🛠️ Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/style-finder-ai.git
cd style-finder-ai
```
### 2. Create a Virtual Environment

```bash
python3.11 -m venv venv
source venv/bin/activate   # For Mac/Linux
# OR
venv\Scripts\activate      # For Windows
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Create a .env File
```bash
API_KEY=your_ibm_api_key
PROJECT_ID=your_project_id
REGION=us-south
```

### 5. Download the Dataset
```bash
curl -o swift-style-embeddings.pkl https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/95eJ0YJVtqTZhEd7RaUlew/processed-swift-style-with-embeddings.pkl
```

---

## 🚦 Run the App Locally
```bash
python app.py
```

---

## How it works?
### 🧠 Multimodal RAG Pipeline — Step-by-Step Workflow

1️⃣ **Image → Vector Embedding (ResNet50)**  
📷 User uploads a fashion image  
🔍 Passed through **pretrained ResNet50**  
📐 Extracts high-dimensional **feature embeddings**  
🧬 Output: A unique vector representation of the image

↓

2️⃣ **Vector Similarity Search (Scikit-learn + `.pkl`)**  
📦 Precomputed `.pkl` file contains embeddings of **Taylor Swift-inspired outfits**  
🧮 **Cosine similarity** measures closeness to user image embedding  
🔍 Top-N **visually similar outfits** are retrieved  
📋 Metadata includes: title, price, description, and shopping links

↓

3️⃣ **Structured Prompt Construction (Markdown + Metadata)**  
🛠️ Metadata of matched items is formatted using **Python helper functions**  
🧾 Output is a **structured markdown prompt** (like a product catalog)  
🧠 Serves as **contextual memory** for the LLM

↓

4️⃣ **Multimodal Reasoning with LLaMA 3.2 Vision Instruct (Watsonx.ai)**  
📤 Input to LLM includes:  
   - 🖼️ User Image  
   - 📄 Markdown Context  
   - ✍️ Task prompt:  
     _"Describe the style of this outfit, name the clothing pieces, and suggest similar alternatives."_  
🤖 **LLaMA 3.2 Vision Instruct** processes both text + image  
🧠 Generates **catalog-style response** via multimodal reasoning

↓

5️⃣ **Real-Time Output via Gradio**  
🌐 Output is displayed in an **interactive Gradio web app**  
✨ Shows:  
   - Style description  
   - Clothing names, prices, and links  
   - 👗 Alternative outfit suggestions
 
### 📌 Credits

- 💡 Original concept by **IBM watsonx Multimodal AI Labs**
- 🧠 LLM model: **Meta LLaMA 3.2 90B Vision Instruct** via [Watsonx.ai](https://www.ibm.com/watsonx)
- 👗 Dataset inspired by [TaylorSwiftStyle.com](https://taylorswiftstyle.com)
- 💻 Built and customized by **Saniel Bhattarai**