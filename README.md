# Can We See It Coming?
## Predicting Graduation Outcomes of Nigerian Engineering Students from Early Academic Performance

> Final Project — Kujenga Course

---

## 📺 Video Walkthrough

🔗 **[Watch the project walkthrough on YouTube](https://youtu.be/cRxr_NHZhbA)**

*A short walkthrough of the dataset, methodology, and findings — recommended viewing before exploring the notebook.*

---

## 🎯 The Story Behind This Project

I am a final-year engineering student in Nigeria. Over the past few years, I have watched the people around me — coursemates, friends, juniors — go through the same degree programme I am in. Some thrived. Some struggled quietly. A few disappeared before final year, and nobody seemed to see it coming until the results came out at the end.

That is the question that started this project: **was the outcome already visible in their early grades, and did anyone bother to look?**

If we could see the warning signs by the end of second year — when there is still time to act, still time to support, still time to change the trajectory — we might be able to help students before failure becomes irreversible.

---

## 🧠 Research Question

> **By the end of Year 2, can we predict the graduation outcome of a Nigerian engineering undergraduate using only their early academic performance?**

### Why this matters

- The tertiary dropout rate in Nigerian universities is approximately **20–22%**, largely due to financial difficulties and academic struggle.
- The graduate unemployment rate in Nigeria reached **33% in 2023**, with many engineering graduates forced into jobs completely outside their field of training.
- Engineering programmes in Nigeria run for **5 years**, meaning the personal and financial cost of late-stage failure is enormous.

When a Nigerian engineering student fails, they don't just lose time — they lose five years of their life, significant family financial investment, and often their confidence in continuing technical careers. Identifying at-risk students *early enough to intervene* is not an academic exercise. It is a question with real human stakes.

---

## 📊 Dataset

**Source:** Odukoya, J. A., Popoola, S. I., Atayero, A. A., Omole, D. O., Badejo, J. A., John, T. M., & Olowo, O. O. (2018). *Learning analytics: Dataset for empirical evaluation of entry requirements into engineering undergraduate programs in a Nigerian university.* **Data in Brief, 17**, 998–1014. [https://doi.org/10.1016/j.dib.2018.02.025](https://doi.org/10.1016/j.dib.2018.02.025)

| Detail | Value |
|---|---|
| **University** | Covenant University, Ota, Nigeria |
| **Sample size** | 1,841 engineering undergraduates |
| **Admission years** | 2002/2003 – 2009/2010 |
| **Departments** | 7 (Chemical, Civil, Computer, Electrical & Electronics, Information & Communication, Mechanical, Petroleum) |
| **Variables** | Year of Entry, GPA Years 1–5, Final CGPA, Class of Degree |

The dataset (`nigerian_universities_academics.xlsx`) is included in this repository for full reproducibility.

---

## 🛠️ Methods

This project applies two core techniques from the Kujenga course:

### Week 1 — Linear Regression
Three regression models, fitted in sequence to compare predictive strength:

1. **Model A:** Year 1 GPA → Final CGPA
2. **Model B:** Year 2 GPA → Final CGPA
3. **Model C:** Early GPA *(average of Year 1 and Year 2)* → Final CGPA

R² values are compared to identify the strongest early predictor.

### Week 3 — Two-Sample t-test
Welch's t-test is used to compare early GPA between two outcome groups:
- **Strong outcome:** First Class or Second Class Upper graduates
- **Weak outcome:** Second Class Lower or Third Class graduates

The t-test runs separately for Year 1 GPA, Year 2 GPA, and combined Early GPA, with α = 0.05.

---

## 📈 Key Findings

| Predictor | R² (variance explained) | t-test p-value |
|---|---|---|
| Year 1 GPA alone | **0.6159** (~62%) | p < 0.001 |
| Year 2 GPA alone | **0.8078** (~81%) | p < 0.001 |
| Early GPA (Y1 + Y2)/2 | **0.8192** (~82%) | p < 0.001 |

**The bottom line:** By the end of Year 2, early academic performance explains roughly **82%** of the variation in final graduation outcomes. The signal is real, measurable, and available early enough to act on. The pattern holds significantly across all 7 engineering departments.

---

## 📁 Repository Structure

```
.
├── README.md                                  
├── nunsi_nigeria_final_project.ipynb          # The full Jupyter notebook
├── nigerian_universities_academics.xlsx       # The dataset
└── plots/                                     # Generated visualizations
    ├── plot1_cgpa_distribution.png
    ├── plot2_class_by_department.png
    ├── plot3_year1_vs_year2.png
    ├── plot4_mean_by_outcome.png
    └── plot5_regressions.png
```

---

## 🚀 How to Run This Project

### Option 1: View the notebook online
The notebook in this repository is **already executed** with all plots and tables populated. You can read it directly on GitHub without running anything.

### Option 2: Run it locally

**Prerequisites:** Python 3.8 or higher

1. **Clone this repository:**
   ```bash
   git clone https://github.com/nunsiomi/kujenga_final_project.git
   cd kujenga_final_project
   ```

2. **Launch Jupyter:**
   ```bash
   jupyter notebook nunsi_nigeria_final_project.ipynb
   ```

3. **Run all cells:** `Cell → Run All` (or `Shift + Enter` through each cell)

The dataset file `nigerian_universities_academics.xlsx` must be in the same directory as the notebook for it to load correctly.

---

## 📦 Dependencies

```
pandas
numpy
matplotlib
seaborn
scipy
openpyxl
jupyter
```

---

## 🗺️ Notebook Roadmap

1. **Introduction & Personal Note** — Why this question matters
2. **The Nigerian Engineering Education Crisis** — Context and statistics
3. **Research Question and Hypotheses** — What we are testing
4. **Dataset Description** — Source, scope, and variables
5. **Setup** — Library imports
6. **Loading the Data** — Reading all 7 department sheets
7. **Data Cleaning** — Six cleaning steps (column typos, year format, class standardization, GPA range checks, missing values, feature engineering)
8. **Exploratory Data Analysis** — 4 visualizations
9. **Hypothesis Testing** — Two-sample t-test
10. **Predictive Modelling** — Three linear regressions
11. **Robustness Check** — Department-level validation
12. **Findings Summary** — What we discovered
13. **Limitations** — Honest caveats about scope and generalizability
14. **Conclusion** — What this means and what comes next

---

## ⚠️ Limitations

- **Single institution:** All data comes from one private Nigerian university. Patterns at federal universities may differ.
- **Older cohort:** Data spans 2002–2010 admissions. Curricula and student conditions have shifted since then.
- **No contextual variables:** Socioeconomic background, family circumstances, internet/power access, and mental health data are absent.
- **Survivorship bias:** Students who dropped out before completing 5 years are not in the dataset.
- **Correlation, not causation:** Early GPA *predicts* Final CGPA — it does not *cause* it.
- **Linear methods only:** No advanced ML; the course covered linear techniques.

---

## 🔮 Future Work

- Replicate the analysis with data from a federal Nigerian university (e.g., FUTA, UNILAG, ABU)
- Add contextual variables (financial aid, accommodation, JAMB scores)
- Build a logistic regression that outputs a calibrated *probability* of being at-risk
- Pilot a small intervention programme triggered by the early-warning model

---

## 📚 References

1. Odukoya et al. (2018). *Learning analytics: Dataset for empirical evaluation of entry requirements into engineering undergraduate programs in a Nigerian university.* **Data in Brief**, 17, 998–1014.
2. Nigeria National Bureau of Statistics — *Education Statistics.*
3. Veriv Africa (2024). *Nigeria's Graduate Employability Crisis.*
4. ZipDo Education Reports (2025). *Nigeria Education Statistics.*

---

## 👤 Author

**Nunsi Shiaki**
Final-year Engineering Student, Nigeria
Kujenga Course Cohort 2025

---

## 📄 License

The code in this repository is released under the MIT License. The dataset is the work of Odukoya et al. (2018) and is published under the **CC BY 4.0** license — please cite the original paper if you use it.

---

*"The takeaway: We can see it coming. The only remaining question is whether we choose to."*
