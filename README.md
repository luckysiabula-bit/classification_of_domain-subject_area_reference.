#  Project Summary: Automated Domain/Subject Area Classification  

## 1. Business Understanding  
- **Problem**: Manual classification of documents is slow, costly, and error-prone.  
- **Objective**: Build an automated system to classify documents into predefined subject areas with ≥80% accuracy.  
- **Goals**:  
  - Reduce manual workload by 70%  
  - Improve retrieval speed and user satisfaction  
  - Ensure precision & recall ≥0.75  

---

## 2. Data Understanding  
- **Dataset**: BBC News articles (1,490 rows, 3 columns: `ArticleId`, `Text`, `Category`).  
- **Balance**: 5 categories (sport, business, politics, entertainment, tech) – relatively balanced.  
- **Findings**: No missing values, clean data, article length ~90–3345 words.  

---

## 3. Data Preparation  
- **Cleaning**: Lowercasing, removing punctuation/numbers, stopword removal.  
- **Feature Engineering**:  
  - `text_length` = number of words  
  - `avg_word_length` = mean word size  
- **Encoding**: Target labels encoded numerically.  
- **Transformation**: TF-IDF vectorization (max_features=5000).  

---

## 4. Modeling  
- Tried multiple models: **Logistic Regression, Naive Bayes, Decision Tree**.  
- Combined **TF-IDF + numeric features**.  
- **Best Model**: Logistic Regression (balanced accuracy + speed).  

---

## 5. Evaluation  
- **Accuracy**: ~81% (meets success criteria ≥80%).  
- **Classification Report**:  
  - Precision & Recall above 0.75 for all classes.  
  - Best performance: *Tech (0.91 precision)*.  
  - Strong results overall with minor confusions (business ↔ tech).  
- **Confusion Matrix**: Most predictions along the diagonal → good generalization.  

---

## 6. Deployment  
- **Final Model**: Logistic Regression + TF-IDF + numeric features.  
- **Deployment options**:  
  - API (Flask/FastAPI)  
  - Dashboard (Streamlit/Dash)  
  - Batch pipeline for auto-tagging new articles  
- **Maintenance**: Retrain periodically, monitor drift, update preprocessing rules.  

---

##  Key Insights  
- Text preprocessing and TF-IDF greatly boosted accuracy.  
- Engineered features (length, avg word size) added useful signals.  
- Logistic Regression gave reliable performance without heavy computation.  
