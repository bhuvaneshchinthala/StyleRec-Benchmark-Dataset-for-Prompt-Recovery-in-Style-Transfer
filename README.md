🌐 Telugu Style Transfer Using Deep Learning (PyTorch + Hugging Face)

This project implements an automated style-transfer system for Telugu text transcripts, built using PyTorch and Hugging Face Transformers. The system rewrites any Telugu transcript into one of 9 different writing styles while preserving the original meaning. Styles include formal, informal, optimistic, pessimistic, motivational, harsh, polite, comedic, and neutral (customizable).

The project was developed using a dataset created from 500 Telugu videos, where transcripts were extracted, cleaned, structured, and annotated with target style labels. Multiple neural architectures were experimented with to identify the best-performing model for controlled style rewriting.

✨ Key Features

✔️ Telugu-language support with high-quality text style transformation

✔️ 9 customizable writing styles

✔️ 500+ video transcripts collected and processed

✔️ End-to-end automated pipeline (data → training → validation → inference)

✔️ Multiple model architectures:

Concatenation-based model

Difference vector model

Cross-encoder style-prediction model

✔️ Deep transformer backbones (RoBERTa / multilingual models)

✔️ Modern training workflow: AdamW, LR scheduling, early stopping

✔️ Multi-metric evaluation: Accuracy, F1 Macro, F1 Weighted, Precision, Recall

✔️ Achieves up to 70% validation accuracy depending on style distribution

🗂️ Dataset Overview

The dataset contains:

Original transcript extracted from Telugu videos

Target writing style (from 9 defined categories)

Ground-truth style-shifted transcript

All transcripts undergo:

Text extraction

Noise removal

Unicode cleanup

Missing field validation

Formatting into training structure

Example format:

{
  "original": "ఇది ఒక ఉదాహరణ వాక్యం.",
  "style": "formal",
  "target": "ఇది ఒక ఉదాహరణ వాక్యం అని చెప్పవచ్చు."
}

🧠 Model Architectures
1️⃣ Concatenation-Based Model

Combines original text + target style text

Feeds into RoBERTa encoder

Classifies the correct transformed output

2️⃣ Difference Vector Model

Computes embedding(x_target) − embedding(x_original)

Learns style-shift direction in embedding space

3️⃣ Cross-Encoder (Sentence Pair Classification)

Inputs: (original sentence, target-style sentence)

Learns pairwise similarity for better rewriting quality

Each architecture uses transformer backbones such as:

xlm-roberta-base

roberta-base

bert-base-multilingual-cased

All models are trained with stratified dataset splits for balanced evaluation.

🏋️ Training Pipeline

The notebook includes:

Train–val split with stratification

Tokenization using Hugging Face

Custom PyTorch datasets and dataloaders

AdamW optimizer

ReduceLROnPlateau scheduler

Early stopping based on validation loss

Gradient clipping to stabilize training

Evaluation Metrics

Accuracy

F1 Macro

F1 Weighted

Precision

Recall

📈 Results

Best model achieved ~70% validation accuracy

Macro-F1 highlights difficulty with underrepresented Telugu writing styles

Cross-encoder model performed best for style consistency

🧪 Inference Example
from model import StyleTransferModel

text = "ఇది ఈరోజు జరిగిన సంఘటన."
target_style = "optimistic"

output = model.generate(text, target_style)
print(output)

🎯 Applications

YouTube transcript rewriting

Social media content rewriting

Customer support tone adjustment

Script writing & dialogue tone modification

Educational content transformation

Assistive writing tools for Telugu creators
