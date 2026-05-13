# 🔍 Resume Screening System
### Future Interns — Machine Learning Task 3 (2026)

> An NLP-powered system that automatically screens, scores, and ranks job candidates against real job descriptions from the Monster.com dataset.

<br>

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-TF--IDF-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![spaCy](https://img.shields.io/badge/spaCy-NLP-09A3D5?style=for-the-badge&logo=spacy&logoColor=white)
![NLTK](https://img.shields.io/badge/NLTK-Text%20Processing-154F5B?style=for-the-badge)
![Streamlit](https://img.shields.io/badge/Streamlit-Web%20App-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data-150458?style=for-the-badge&logo=pandas&logoColor=white)

<br>

---

## 📌 Problem Statement

Hiring teams receive **hundreds of resumes** for a single job role. Manually reading each one is:

- ❌ Slow and time-consuming
- ❌ Inconsistent across reviewers
- ❌ Prone to bias and human error

This project solves that with an **ML-based resume screening system** that automatically reads, scores, and ranks candidates — just like real HR-tech tools used in industry.

---

## 🎯 What This System Does

| Feature | Description |
|---|---|
| 📄 Resume text cleaning | Removes noise, stop words, punctuation using NLTK |
| 🧠 Skill extraction | Extracts skills using spaCy NER + keyword dictionary |
| 📊 Similarity scoring | TF-IDF vectorisation + cosine similarity (scikit-learn) |
| 🏆 Candidate ranking | Weighted score: TF-IDF (60%) + Skill overlap (40%) |
| ❌ Skill gap detection | Shows exactly what skills a candidate is missing |
| 🌐 Web interface | Streamlit app with charts, radar graphs, and skill heatmaps |

---

## 🛠️ Tech Stack

```
Python 3.10+
│
├── 🔤 NLTK            — Tokenisation, stop-word removal, lemmatisation
├── 🧠 spaCy           — Named Entity Recognition (en_core_web_sm)
├── 📐 scikit-learn    — TF-IDF Vectoriser, Cosine Similarity
├── 🐼 Pandas          — Data handling and candidate ranking
├── 🌐 Streamlit       — Interactive web UI
└── 📊 Plotly          — Bar charts, radar charts, heatmaps
```

---

## 📁 Project Structure

```
resume_screening_system/
│
├── 📄 app.py                              ← Streamlit web application
├── 🧠 resume_screener.py                  ← Core NLP screening engine
├── 📂 load_data.py                        ← Monster.com CSV data loader
├── ▶️  run_demo.py                         ← Quick terminal demo
├── 📋 requirements.txt                    ← All Python dependencies
│
├── 📁 data/
│   └── monster_com-job_sample.csv         ← Place Kaggle CSV here
│
├── 📁 sample_data/
│   └── sample_resumes.json               ← 10 sample candidate profiles
│
└── 📁 notebooks/
    └── resume_screening_analysis.ipynb   ← Full analysis walkthrough
```

---

## ⚡ Quick Start

### Step 1 — Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/resume-screening-system.git
cd resume-screening-system
```

### Step 2 — Install all dependencies
```bash
pip install -r requirements.txt
python -m spacy download en_core_web_sm
```

### Step 3 — Add the dataset
Download the Monster.com CSV from Kaggle and place it inside the `data/` folder:

👉 [Monster.com Jobs Dataset — Kaggle](https://www.kaggle.com/datasets/PromptCloudHQ/us-jobs-on-monstercom)

```
data/
└── monster_com-job_sample.csv
```

### Step 4 — Run the project

**Option A: Web App (full UI)**
```bash
streamlit run app.py
```
Open your browser at `http://localhost:8501`

**Option B: Terminal Demo (quickest)**
```bash
python run_demo.py
```

**Option C: Jupyter Notebook**
```bash
jupyter notebook notebooks/resume_screening_analysis.ipynb
```

---

## 🧠 How It Works

```
  Job Description Text              Resume / Candidate Text
         │                                    │
         ▼                                    ▼
   ┌─────────────┐                    ┌─────────────┐
   │ Text Cleaning│                   │ Text Cleaning│
   │   (NLTK)    │                    │   (NLTK)    │
   └─────────────┘                    └─────────────┘
         │                                    │
         ▼                                    ▼
   ┌─────────────┐                    ┌─────────────┐
   │   Skill     │                    │   Skill     │
   │ Extraction  │                    │ Extraction  │
   │(spaCy + NLP)│                    │(spaCy + NLP)│
   └─────────────┘                    └─────────────┘
         │                                    │
         └─────────────┬──────────────────────┘
                       │
                       ▼
             ┌──────────────────┐
             │  TF-IDF Vectors  │
             │  (scikit-learn)  │
             └──────────────────┘
                       │
                       ▼
             ┌──────────────────┐
             │ Cosine Similarity│
             │     Scoring      │
             └──────────────────┘
                       │
              ┌────────┴─────────┐
              │ Weighted Formula │
              │ 60% TF-IDF Score │
              │ 40% Skill Match  │
              └────────┬─────────┘
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
    ✅ Strong      🟡 Consider   ❌ Not a
       Hire         (40–65%)      Match
      (≥ 65%)                    (< 40%)
```

---

## 📊 Scoring System

| Score | Verdict | Meaning |
|:---:|---|---|
| **65 – 100%** | ✅ Strong Hire | Excellent skills & language match with JD |
| **40 – 64%** | 🟡 Consider | Partial match, some skill gaps exist |
| **0 – 39%** | ❌ Not a Match | Insufficient match with job requirements |

**Score Formula:**
```
Final Score = (0.60 × TF-IDF Cosine Score) + (0.40 × Skill Overlap %)
```

---

## 📸 Features Preview

### 🖥️ Web App (Streamlit)
- **Tab 1 — Screen Candidates:** Add up to 10 candidates, select any job from the CSV, click Analyze
- **Tab 2 — Rankings:** Ranked list with match scores, skill pills, and hiring verdict per candidate
- **Tab 3 — Insights:** Bar chart, radar chart, and skill coverage heatmap
- **Tab 4 — About:** Full explanation of the system for non-technical users

### 📓 Jupyter Notebook Sections
1. Dataset loading & exploration
2. Text cleaning (NLTK demo)
3. Skill extraction (spaCy demo)
4. TF-IDF heatmap visualisation
5. Full candidate ranking pipeline
6. Detailed skill gap analysis
7. Bar charts + radar chart + skill coverage heatmap
8. CSV export of results
9. Plain-English explanation for recruiters

---

## 📂 Dataset

| Property | Detail |
|---|---|
| **Source** | [PromptCloudHQ — Monster.com Jobs (Kaggle)](https://www.kaggle.com/datasets/PromptCloudHQ/us-jobs-on-monstercom) |
| **Size** | ~22,000 real US job postings |
| **Key columns used** | `job_title`, `job_description`, `sector`, `location`, `salary` |
| **Sectors covered** | IT, Healthcare, Finance, Engineering, Media, Admin, and more |

---

## 🔭 Future Improvements

- [ ] BERT / sentence-transformers for deeper semantic similarity
- [ ] Experience years extraction and scoring
- [ ] Education level matching
- [ ] PDF resume upload support (PyMuPDF)
- [ ] Multi-role batch screening
- [ ] REST API endpoint using FastAPI
- [ ] Deploy to Streamlit Cloud / Hugging Face Spaces

---

## 🤝 Acknowledgements

- [Future Interns](https://www.linkedin.com/company/future-interns/) — for the internship task
- [PromptCloudHQ](https://www.kaggle.com/datasets/PromptCloudHQ/us-jobs-on-monstercom) — for the Monster.com dataset
- [spaCy](https://spacy.io), [NLTK](https://www.nltk.org), [scikit-learn](https://scikit-learn.org) — core NLP libraries

---

## 👤 Author

**Your Name**
- LinkedIn: [linkedin.com/in/yourprofile](https://linkedin.com/in/yourprofile)
- GitHub: [github.com/yourusername](https://github.com/yourusername)

> 📢 If you found this helpful, please ⭐ star the repo and tag [@FutureInterns](https://www.linkedin.com/company/future-interns/) on LinkedIn!

---

## 📄 License

This project is licensed under the **MIT License** — free to use, modify, and share.
