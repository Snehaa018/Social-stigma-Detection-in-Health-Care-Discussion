# 🧠 Social Stigma Detection in Health Discussions

> Detecting stigma in health conversations, one post at a time: four NLP techniques, one Stigma Risk Score.

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![spaCy](https://img.shields.io/badge/spaCy-NLP-09a3d5?logo=spacy&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikitlearn&logoColor=white)
![Colab](https://img.shields.io/badge/Notebook-Google%20Colab-F9AB00?logo=googlecolab&logoColor=white)

## 📌 Overview

Online health forums are where people talk openly about depression, addiction, schizophrenia and more. They are also where harmful, stigmatising language spreads. This project builds an NLP pipeline that reads a post and tells you **how likely it is to be stigmatising**, by combining four complementary techniques into a single **Stigma Risk Score**.

## ✨ Features

| # | Technique | Tool | What it contributes |
|---|-----------|------|---------------------|
| 1 | **Sentiment Analysis** | VADER | Flags negative tone (weak signal, +1) |
| 2 | **Text Classification** | TF-IDF + Logistic Regression | Classifies posts as `stigma` / `support` / `info` (strong signal, +2) |
| 3 | **Semantic Analysis** | spaCy word vectors + cosine similarity | Catches paraphrased stigma that uses different words (strong signal, +2) |
| 4 | **Named Entity Recognition** | spaCy + custom health lexicons | Extracts people, orgs, conditions and drugs; anonymises patient names |

The signals are combined into a score out of 5:

- 🔴 **High risk** (score ≥ 4): likely stigmatising
- 🟡 **Medium risk** (score 2–3): possible stigma
- 🟢 **Low risk** (score < 2): likely safe

## 🖼️ Screenshots

### Sentiment classification
![Sentiment results](<img width="1127" height="601" alt="image" src="https://github.com/user-attachments/assets/6079b77c-8a76-417d-8db9-b2f77990e2a1" />
)

### Text classification results
![Classification report](<img width="983" height="618" alt="image" src="https://github.com/user-attachments/assets/fd0c4d30-a0b8-42ff-a6c6-2b1abe82271b" />
)

### Semantic stigma detection
![Semantic detection](<img width="672" height="737" alt="image" src="https://github.com/user-attachments/assets/6572f7f8-28ad-4fdf-8dce-667ca85e2c9b" />
)

### Named Entity Recognition and anonymisation
![NER and anonymisation](<img width="792" height="547" alt="image" src="https://github.com/user-attachments/assets/649fae01-0600-4949-a3ac-ffff9a0e90dd" />
)

### Full pipeline: Stigma Risk Score
![Combined pipeline](<img width="1592" height="698" alt="image" src="https://github.com/user-attachments/assets/cf97de0d-d638-42ec-8d72-46cad30b3efe" />
), (<img width="1590" height="683" alt="image" src="https://github.com/user-attachments/assets/12357a60-ef6d-40b3-b77f-fe073c32336c" />)


## 🚀 Getting Started

### Run in Google Colab
Open `SocialStigmaDetectionInHealthCareDiscussion.ipynb` in Colab and run all cells. The first cell installs everything.

### Run locally
```bash
git clone https://github.com/Snehaa018/<repo-name>.git
cd <repo-name>

pip install vaderSentiment textblob scikit-learn spacy
python -m spacy download en_core_web_md

jupyter notebook SocialStigmaDetectionInHealthCareDiscussion.ipynb
```

## 🧪 Example

```python
analyse_post("People with schizophrenia are violent and should be locked away from the public.")
```

```
1️⃣  Sentiment      : NEGATIVE
2️⃣  Classification : STIGMA
3️⃣  Semantics      : Flagged
🎯 STIGMA RISK SCORE : 5/5
📌 VERDICT           : 🔴 HIGH RISK — Likely stigmatising
```
<!-- Replace with your real output from the notebook -->

## 🗂️ Project Structure

```
├── SocialStigmaDetectionInHealthCareDiscussion.ipynb
├── screenshots/
│   ├── 01_sentiment.png
│   ├── 02_classification.png
│   ├── 03_semantics.png
│   ├── 04_ner.png
│   └── 05_pipeline.png
└── README.md
```

## ⚠️ Limitations

- The dataset is a small, hand-written sample (20 posts across 3 classes), so this is a **proof of concept**, not a production-ready detector.
- Semantic matching uses averaged word vectors against a few reference sentences, so very subtle or context-dependent stigma can be missed.
- The risk score uses fixed, hand-chosen weights rather than learned ones.

## 🔮 Future Work

- Train on a larger real-world health-forum dataset
- Fine-tune a transformer model (e.g. BERT) for classification
- Learn the score weights instead of fixing them
- Build a simple web demo (Streamlit / Gradio)

## 👩‍💻 Author

**Sneha** — BCA (AI/ML) student, Galgotias University
[GitHub](https://github.com/Snehaa018)
