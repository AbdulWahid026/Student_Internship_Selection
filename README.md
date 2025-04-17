# 🌟 Internship Selection Classifier (NLP-based)

This project uses Natural Language Processing (NLP) and a lightweight BERT model to predict whether a student should be selected for a tech internship based on their open-ended application responses.

## 📊 Project Overview

- **Goal**: Automate the classification of internship applications based on textual responses from applicants.
- **Model**: Fine-tuned `bert-base-uncased` from HuggingFace Transformers.
- **Data**: Custom dataset with responses to questions like:
  - Why do you want to intern?
  - Describe your tech/non-tech experience.
  - What are your goals?
  - Any other comments.

## 🧠 Features

- Text preprocessing with lemmatization and stopword handling.
- Combined multiple free-text columns into a single input.
- Handled label normalization (`yes`, `no`, `declined` → binary labels).
- Early stopping, dropout regularization, and scheduler for training stability.
- Model saving and inference-ready prediction pipeline.

## ✅ Performance

- **Test Accuracy**: **89%**
- **F1 Score**: Balanced between "Selected" and "Not Selected" classes.
- Good performance across both precision and recall.

## 🔍 Example Input for Inference

You can test the model with new applicant responses like:

```python
sample = {
    "why_internship": "I want to explore the tech world and gain practical experience.",
    "tech_experience": "Basic Python and HTML knowledge.",
    "non_tech_experience": "Volunteered at a local NGO and ran events.",
    "goals": "Improve my coding skills and contribute to real-world projects.",
    "other_comments": "Open to learning and working in diverse teams."
}
```

## 📦 How to Use

1. Clone the repo.
2. Install requirements from `requirements.txt`.
3. Run `inference.py` to test the model on custom data.
4. Trained `.pt` model file included for direct loading.
