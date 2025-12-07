# User-Level Mental Health Prediction via Hybrid Linguistic and Semantic Modeling

**Report Link:** [View Full Report](https://docs.google.com/document/d/1GjV_qR8GxePBSsDxqobrM3V4zWFdzF0r/edit?usp=sharing&ouid=111477489402121972489&rtpof=true&sd=true)

## Course Information
**Deep Learning and Applications (UEC642)**

**Submitted to:**  
Dr. Deepak Kumar Rakesh  
Electronics and Communication Engineering Department  
Thapar Institute of Engineering and Technology, Patiala  
July-December 2025

## Team Members
- **Ronit Parakh** (102215228)
- **Jayant Khandelwal** (102215158)
- **Aditya Sachdeva** (102215206)
- **Karan Veer Singh** (102215196)

## Abstract

The COVID-19 pandemic significantly intensified global mental health challenges, driving individuals to seek support through pseudonymous online platforms like Reddit. While these platforms offer a wealth of data for computational analysis, existing methods often focus on aggregate trends or simple sentiment analysis, failing to capture the nuance of specific mental health conditions at the user level.

This study presents a reproducible and modular classification pipeline for identifying mental health-related subreddit participation based on a single Reddit post per user. We introduce a novel hybrid feature set that combines sparse lexical representations (TF-IDF), handcrafted psycholinguistic features (LIWC, readability), and dense transformer-based sentence embeddings (MPNet). We evaluate three distinct modeling approaches: a baseline linear classifier (SGD), and two deep-learning-augmented models (XGBoost and Multilayer Perceptron). Experimental results on a multi-class dataset spanning 28 subreddits demonstrate that the transformer-enhanced models substantially outperform the baseline, achieving 83% accuracy with the MLP model.

## Problem Statement

Detecting mental health signals from social media text is challenging due to the informal nature of the language, the overlap in vocabulary between related conditions (e.g., anxiety vs. depression), and the scarcity of labeled data. Most prior work operates at the "post level," treating every comment as an independent data point. This study addresses the more difficult task of **user-level classification**: determining which mental health community a user belongs to based on a single sample of their writing.

## Methodology

### Dataset
- **Source:** Reddit Mental Health Dataset
- **Classes:** 28 distinct subreddits (15 mental health support groups + 13 control groups)
- **Preprocessing:** User-level train/validation/test split (70/15/15) to prevent data leakage

### Feature Engineering
1. **Sparse Features (TF-IDF):** Unigrams and bigrams capturing condition-specific terminology
2. **Dense Linguistic Features:** 93 handcrafted metrics from LIWC dictionary and readability scores
3. **Transformer Embeddings (MPNet):** 768-dimensional semantic vectors using all-mpnet-base-v2

### Models Evaluated
1. **Baseline (SGD):** Linear classifier with L1 regularization
2. **XGBoost (Hybrid):** Gradient boosted trees with all feature types
3. **MLP (Hybrid):** Feed-forward neural network (512→256→28) with dropout

## Results

| Model | Accuracy | Macro-F1 | Weighted-F1 |
|-------|----------|----------|-------------|
| Baseline (SGD) | 60.00% | 0.43 | 0.60 |
| XGBoost (Hybrid) | 82.00% | 0.75 | 0.82 |
| **MLP (Hybrid)** | **83.00%** | **0.75** | **0.82** |

The MLP model achieved the highest accuracy, demonstrating that neural networks effectively capture complex non-linear interactions between semantic embeddings and psycholinguistic markers.

## Key Findings

- Transformer-enhanced models significantly outperform lexical baselines (23% accuracy improvement)
- Distinct communities (e.g., r/fitness, r/legaladvice) achieved F1-scores > 0.90
- Semantic overlap between related conditions (e.g., r/depression vs. r/suicidewatch) remains a challenge
- Hybrid approach combining interpretable linguistic features with deep semantic embeddings provides both performance and stability

## Conclusion

This project successfully demonstrated the efficacy of hybrid NLP modeling for user-level mental health classification. By fusing traditional psycholinguistic features with state-of-the-art MPNet transformer embeddings, we achieved robust performance with 83% accuracy. Future work will focus on addressing class imbalance through data augmentation and exploring temporal analysis to track user mental health trajectories over time.

## References

- Low, D. M., et al. (2020). Natural Language Processing Reveals Vulnerable Mental Health Support Groups and Heightened Health Anxiety on Reddit During COVID-19. *Journal of Medical Internet Research*.
- Gkotsis, G., et al. (2016). The language of mental health problems in social media. *Proceedings of the Third Workshop on Computational Linguistics and Clinical Psychology*.
- Song, K., et al. (2020). MPNet: Masked and Permuted Pre-training for Language Understanding. *NeurIPS*.
- Reimers, N., & Gurevych, I. (2019). Sentence-BERT: Sentence Embeddings using Siamese BERT-networks. *EMNLP*.
- Patel, R., et al. (2021). Analysis of mental and physical disorders associated with COVID-19 in online health forums.
