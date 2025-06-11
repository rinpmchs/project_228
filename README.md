# Research of Criminal Cases and Identification of their Important Characteristics

This project explores the use of Natural Language Processing (NLP) and Machine Learning (ML) to analyze Russian court decisions under **Article 228 of the Criminal Code** (drug-related offenses). It aims to extract structured legal features from unstructured court texts and identify statistical patterns in sentencing.

---

## Authors

- Morozova Yulia Dmitrievna (DSBA, HSE)
- Sheredeko Arina Yanovna (DSBA, HSE)
- Khugaeva Dana Arturovna (AMI, HSE)

Supervised by: Ilya Munerman, Faculty of Computer Science, HSE

---

## Repository Structure

- `data/` — Datasets with raw and enriched court data (including predicted features)
- `dev/` — Code for data preprocessing, feature extraction, analysis, and visualization
- `README.md` — Project description and documentation

---

## Project Goal

To build a scalable pipeline for the automated extraction of legally important features from Russian court decisions and analyze patterns in judicial outcomes using ML tools.

---

## Key Tasks

1. **Data Collection & Cleaning**
   - Parsed 300,000+ court decisions (2015–2024)
   - Reduced to 10,000 representative cases after preprocessing

2. **Feature Extraction**
   - Used regular expressions for numeric data (e.g., drug weight, sentence duration)
   - Applied LLMs (ruBERT) for classification tasks:
     - Type of punishment (`result_type`)
     - Drug amount category (`drug_amount`)
     - Mitigating factors (`mitigating_factors`)

3. **Manual Annotation**
   - Created a gold standard of 150 manually labeled cases to evaluate model accuracy

4. **Visualization**
   - Used Tableau for interactive dashboards showing spatial, gender, and punishment trends

5. **Statistical Analysis**
   - Tested hypotheses on punishment severity, gender bias, and effect of drug quantity using regression models

---

## Extracted Features

The following legal characteristics were extracted:

- `result_type`: imprisonment, fine, probation, etc.
- `sentence_years`, `months`, `days`, `hours`
- `is_suspended`: binary flag
- `fine_amount`, `fine_is_fixed`
- `drug_weight`, `drug_amount`, `drug_type`, `drug_purpose`
- `mitigating_factors`, `aggravating_factors`
- `location`: lat/lon coordinates for visualization

---

## Results

- LLM model accuracy (on gold dataset):
  - `result_type`: F1 = 0.95
  - `drug_amount`: F1 = 0.94 (2 classes)
  - `mitigating_factors`: F1 = 0.09 (poor performance due to data imbalance)
- Regex-based extraction of drug weight: 94% accuracy

**Key findings:**
- Larger drug weights reduce chances of lenient sentences (statistically significant)
- Weak/no evidence that gender affects sentence severity (in simplified model)
- Data suggests possible procedural manipulation around drug weight thresholds (e.g., spikes at 1g, 100g, 200g)

---

## Future Directions

- Expand the annotated training set for underperforming features
- Improve multi-label classification (e.g., mitigating/aggravating factors)
- Explore clustering, fairness metrics, and decision prediction models
- Use more powerful LLMs (GPT-4, Mistral, etc.)

---

## Dataset

Due to legal sensitivity and large size, only processed samples are included in this repository. Raw data collected via the open-source parser “Если быть точным”.
