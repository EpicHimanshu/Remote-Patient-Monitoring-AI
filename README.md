# 🩺 Remote Patient Monitoring System for Chronic Care

This repository contains the foundational core of an AI-driven healthcare tracking system. It focuses on health data simulation, handling missing biological vitals, and flagging high-risk patient metrics.

### 🛠️ Core Implementation
- **Data Engineering:** Used `Pandas` and `NumPy` for structured medical data manipulation.
- **Data Quality:** Implemented median imputation to handle random missing sensor metrics.
- **Feature Extraction:** Engine engineered a logical `High_Risk_Flag` based on critical medical thresholds (e.g., Systolic BP > 140 or HR > 100 BPM).

### 📈 Next Steps
- Implement a `Scikit-Learn` Classification Model (like KNN or Random Forest) to automate risk level predictions.
