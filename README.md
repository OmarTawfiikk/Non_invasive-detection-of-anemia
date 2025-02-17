# Non_invasive-detection-of-anemia

## Overview
This project implements a two-phase diagnostic system for blood analysis:
- **Phase 1**: Binary anemia detection using conjunctiva, palm, and nail images  
- **Phase 2**: Hemoglobin (Hgb) level regression using late fusion technique  

Achieved state-of-the-art results with:
- **Phase 1**: 99.5% accuracy (palm), 99.4% (nails), 99.38% (conjunctiva)
- **Phase 2**: 93% R² score and 0.3 MSE for Hgb level prediction

---

## Architecture Overview
### Phase 1: Anemia Detection

- **Input**: Conjunctiva/Palm/Nail images
- **Technique**:
  - LAB color space conversion
  - Statistical feature extraction (mean, std, skewness, kurtosis)
  - Histogram-based features
  - Random Forest classification

### Phase 2: Hemoglobin Level Prediction

- **Input**: 217 original samples → 3225 after augmentation
- **Late Fusion Pipeline**:
  1. **Meta-Feature RF Model**: Demographic/clinical data
  2. **Color Feature RF Model**: Image-based color features
  3. **XGBoost Regressor**: Combines outputs from both RF models
- **Evaluation**: 10-fold cross-validation

---

## Key Features
### Phase 1 (Classification)
- Multi-modal image analysis (conjunctiva/palm/nails)
- Handcrafted color feature engineering
- High-performance Random Forest classifier
- 99.5% accuracy (palm), 99.4% (nails), 99.38% (conjunctiva)
 
### Phase 2 (Regression)
- Advanced data augmentation techniques
- Late fusion of clinical and image features
- Ensemble modeling with XGBoost
- State-of-the-art results:
  | Metric | Value |
  |--------|-------|
  | R²     | 93%   |
  | MSE    | 0.3   |

---

## Dataset Structure
### Phase 1
- **Conjunctiva**:  
  - Anemic: 2,576 images  
  - Non-anemic: 1,686 images  
- **Palm/Nail**: Similar structure

### Phase 2
- Original dataset: 217 samples
- After augmentation: 3,225 samples
- Features:
  - Image color features (LAB space)
  - Clinical meta-features (age, gender, hgb)

---

## Implementation
### Requirements
```bash
Python 3.7+
opencv-python==4.5.5.64
scikit-learn==1.0.2
xgboost==1.6.1
imbalanced-learn==0.9.1
Usage
