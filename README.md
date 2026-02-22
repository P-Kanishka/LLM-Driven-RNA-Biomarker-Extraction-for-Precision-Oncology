# LLM-Driven RNA Biomarker Extraction for Precision Oncology

## 📘 Project Overview
This project implements a **Zero-Shot Extractive Question-Answering (QA)** pipeline designed to automate the abstraction of complex transcriptomic data from unstructured molecular pathology reports. 

Unlike traditional Clinical NLP which relies on rigid, dictionary-based Named Entity Recognition (NER), this system utilizes a transformer-based foundation model to dynamically interrogate clinical narratives. It is specifically engineered to identify and structure **Actionable RNA Biomarkers**—such as pathogenic gene fusions and mRNA overexpression—which are critical for modern precision oncology and pharmacogenomics.



## 🛠️ Technical Architecture
* **Core Model:** `deepset/roberta-base-squad2` (Fine-tuned for robust extractive logic and unanswerable question detection).
* **Methodology:** Zero-shot learning (no task-specific retraining required for new biomarkers).
* **Data Handling:** Structured processing of multi-omics terminology (e.g., EML4-ALK fusions, HER2 amplification).
* **Safety Layer:** Programmatic confidence thresholding to intercept low-probability model outputs.

## 🛡️ Trustworthy AI & Clinical Safety
In alignment with the principles of **Trustworthy AI**, this pipeline does not provide "black box" answers. It includes a clinical safety intercept:
1.  **Confidence Scoring:** Every extracted biomarker is assigned a probability score based on start/end logit products.
2.  **Manual Review Trigger:** Any extraction falling below the **10% confidence threshold** (Span Probability < 0.10) is automatically flagged as `⚠️ INCONCLUSIVE`.
3.  **Edge-Case Handling:** The system was validated against a test suite including degraded RNA samples and incomplete reports to ensure it fails safely rather than hallucinating diagnoses.



*Figure 1: Analytics showing model certainty across a simulated patient cohort. Red dashed line indicates the safety threshold for manual human oncologist review.*

## 🚀 Key Features
* **Precision Oncology Focus:** Specifically targets biomarkers like *PD-L1*, *ALK*, and *HER2*.
* **Extractive Span Attribution:** Provides the exact text snippet from the report used for the diagnosis.
* **Scalable Architecture:** Designed for integration into High-Performance Computing (HPC) workflows for large-scale clinical cohort analysis.

---

