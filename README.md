# Multimodal Sentiment Analysis in Bangla (Image + Text)

This project performs **Bangla sentiment/emotion classification** from **images + captions** using:

- **ViT (Vision Transformer)** → Image features (768-dim)
- **LSTM + Embedding** → Text features
- **Dense Classifier** → 7 emotion classes

Dataset used:  
`/kaggle/input/sentiment-analysis-in-bangla/1704054_Dataset/`

---

## 🔥 Sentiment Labels
- happy  
- sad  
- angry  
- disgust  
- fear  
- surprise  
- other  

---

## 📂 Dataset Structure

Kaggle Dataset Used:

/kaggle/input/sentiment-analysis-in-bangla/1704054_Dataset/
│── Images/
│ ├── 205.jpg
│ ├── 2151.jpg
│ ├── ...
│
│── train.csv
│── val.csv
│── test.csv

markdown
Copy code

### ✔ train.csv Structure:

| image_name | Captions | Label_Sentiment | Label |
|-----------|----------|------------------|--------|
| 205.jpg | নির্বোধ দেখার... | other | 6 |

---

## 📥 Data Loading & Preprocessing

### 🖼 Image Preprocessing
- Read image using **OpenCV**
- Convert BGR → RGB
- Resize to **224×224**
- Feed into **ViT Feature Extractor**

### 📝 Text Preprocessing
- Tokenization using **Keras Tokenizer**
- Vocabulary Size = **10,000**
- Padding Length = **30**

### 📊 Label Distribution (Train Data)
happy 861
other 716
sad 621
angry 477
surprise 410
fear 400
disgust 348


## 🧠 Model Architecture

pgsql
Copy code
    IMAGE INPUT                          TEXT INPUT
(224x224 → ViT) (Caption → Tokens)

Copy code
   │                                         │
   ▼                                         ▼
ViT Feature Extractor Embedding → LSTM
(CLS Token → 768-dim) (128-dim)

scss
Copy code
                 ┌──────────────────────────┐
                 │   CONCATENATION LAYER    │
                 └──────────────────────────┘
                            │
                            ▼
                   Dense(256) → Dense(128)
                            │
                            ▼
               Output Layer (7 sentiment classes)
yaml
Copy code

✔ No missing values  
✔ 3,833 training samples  
✔ 414 validation samples  



