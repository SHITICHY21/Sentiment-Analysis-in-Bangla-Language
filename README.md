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

## 📁 Dataset Format
image_name | Captions | Label_Sentiment | Label
205.jpg | ... | other | 6
