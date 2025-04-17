# 🧠 NLP-Based Internship Selection System

This project uses **Natural Language Processing (NLP)** and **BERT** to automate and enhance the selection of students for a technical internship. It classifies whether a student **should be selected or not** based on their application responses, and also provides **scoring and ranking** — including **detailed scoring for each input field** (like *tech experience*, *goals*, etc.), helping applicants understand which parts of their responses were most impactful.

---

## 📌 Features

- ✅ BERT-based binary classification model
- 🧼 Preprocessing with lemmatization and stopword removal
- 📤 Train-validation-test split with stratification
- 🔢 **Per-field scoring system** to show applicant strengths/weaknesses
- 📊 Accuracy: **89%** on test data
- 📈 Confidence scores and overall ranking
- 💾 Save/load model (`.pt` file) for easy inference
- 🧪 Interactive prediction interface for student submissions

---

## 🧾 Data Fields Used

The following fields from student applications are used and scored individually:

| Column Name          | Description |
|----------------------|-------------|
| `why_internship`     | Why the applicant wants this internship |
| `tech_experience`    | Their technical background (if any) |
| `non_tech_experience`| Any non-tech experience |
| `goals`              | What they hope to achieve through the internship |
| `other_comments`     | Anything else they want to share |

Each of these fields is processed individually to generate a **score (0-1)** indicating its contribution to the selection prediction.

---

## 🧠 Scoring & Ranking System

After training, the model can output:

- **Final decision**: ✅ Selected / ❌ Not Selected  
- **Overall confidence score**: e.g., 0.89
- **Detailed per-field scoring**:
    ```json
    {
      "why_internship": 0.72,
      "tech_experience": 0.91,
      "non_tech_experience": 0.65,
      "goals": 0.88,
      "other_comments": 0.42,
      "final_score": 0.89,
      "prediction": "Selected"
    }
    ```

This transparency allows students to reflect on which parts of their application stood out and which areas might need improvement.

---

## 📈 Model Performance (Test Set)

| Metric        | Score |
|---------------|-------|
| Accuracy      | **89%**   |
| F1 Score      | 0.89  |
| Precision     | 0.88  |
| Recall        | 0.90  |

---

## 📤 Installation

```bash
pip install -r requirements.txt
```

---

## 🔮 Example Prediction

```python
# Provide individual text fields
example = {
    "why_internship": "I want to explore tech and build real-world projects.",
    "tech_experience": "Some Python and web dev, eager to learn more.",
    "non_tech_experience": "Volunteering, teamwork, and communication.",
    "goals": "Learn hands-on skills and work on social impact ideas.",
    "other_comments": "I'm very motivated and open to feedback."
}

# Returns per-field scores + final prediction
{
  "why_internship": 0.76,
  "tech_experience": 0.92,
  "non_tech_experience": 0.66,
  "goals": 0.81,
  "other_comments": 0.57,
  "final_score": 0.86,
  "prediction": "Selected"
}
```

---

## 💾 Save Model

```python
torch.save(model.state_dict(), "internship_model.pt")
```

To load it again:

```python
model.load_state_dict(torch.load("internship_model.pt"))
model.eval()
```

---

## 🧪 Future Work

- Web dashboard for real-time application scoring
- Field-level feedback tips based on score
- Bulk CSV scoring with exportable results
