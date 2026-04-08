# Task 1: News Topic Classifier Using BERT

## Overview

This task implements a deep learning-based text classification system using BERT (Bidirectional Encoder Representations from Transformers), a state-of-the-art transformer model from Hugging Face. The system learns to classify news headlines into four distinct topic categories using transfer learning techniques.

The project demonstrates how to leverage pre-trained language models for efficient NLP tasks, reducing training time while achieving high accuracy. This is a practical example of modern NLP workflows used in production systems for content categorization, news aggregation, and automated tagging.

## Problem Statement

Given a collection of news headlines, automatically classify each headline into one of four predefined categories: **World**, **Sports**, **Business**, or **Technology**. This is a multi-class text classification problem solving a real-world use case in content management and recommendation systems.

## What You'll Learn

- **Transfer Learning:** How to fine-tune pre-trained transformer models instead of training from scratch
- **NLP Pipeline:** Complete workflow from data loading to model inference
- **Tokenization:** Understanding how BERT tokenizes and processes text
- **Model Evaluation:** Comprehensive metrics including accuracy, precision, recall, and F1-score
- **Hyperparameter Tuning:** Optimizing learning rate, batch size, and epochs
- **Model Deployment:** Converting trained models for production inference

## Dataset Details

- **Name:** AG News Dataset
- **Source:** Hugging Face Datasets library (automatically downloaded)
- **Size:** 120K training samples + 7.6K test samples
- **Categories:** 4 classes (World, Sports, Business, Technology)
- **Format:** Headlines as text with category labels
- **Processing:** Tokenized to 128 tokens using BERT tokenizer

The dataset is automatically downloaded from Hugging Face during notebook execution, eliminating the need for manual data preparation.

## Technical Architecture

### Components Used

1. **PyTorch** - Deep learning framework for model training
2. **Transformers (Hugging Face)** - Pre-trained BERT model and tokenizer
3. **Datasets (Hugging Face)** - AG News dataset loader
4. **scikit-learn** - Evaluation metrics and utilities
5. **Pandas & Numpy** - Data manipulation and numerical operations
6. **Matplotlib & Seaborn** - Visualization of results

### Model Architecture

The system uses:
- **Base Model:** `bert-base-uncased` (12 layers, 768 hidden units, 110M parameters)
- **Pre-training:** Trained on English Wikipedia and BookCorpus
- **Fine-tuning:** Added classification head (768 -> 4 classes)
- **Learning Strategy:** Fine-tune all layers with appropriate learning rate

## Workflow / Implementation Steps

### 1. Data Loading and Preprocessing
- Load AG News dataset from Hugging Face
- Tokenize headlines using BERT tokenizer (converts text to token IDs)
- Create training, validation, and test splits
- Build PyTorch DataLoaders for batch processing

### 2. Model Preparation
- Load pre-trained `bert-base-uncased` model
- Replace classification head for 4-class prediction
- Move model to GPU if available
- Configure optimizer (Adam) and loss function (CrossEntropyLoss)

### 3. Training Loop
- Iterate through training data for multiple epochs
- Forward pass: headlines -> BERT model -> logits -> probabilities
- Calculate loss and backpropagate
- Update weights using Adam optimizer
- Validate on validation set after each epoch
- Save best model based on validation performance

### 4. Evaluation and Metrics
- Test on held-out test set
- Calculate metrics:
  - **Accuracy:** Percentage of correct predictions
  - **F1-Score:** Harmonic mean of precision and recall (macro and weighted)
  - **Precision & Recall:** Per-class performance metrics
  - **Confusion Matrix:** Visual breakdown of predictions vs actual
  - **Classification Report:** Detailed per-class metrics

### 5. Results Visualization
- Plot training/validation loss curves
- Create confusion matrix heatmap
- Display classification report
- Show sample predictions with confidence scores

## What Gets Saved

After execution, the notebook produces:
- **Trained Model:** The fine-tuned BERT model weights
- **Tokenizer:** Configuration for reproducing tokenization
- **Evaluation Metrics:** Accuracy, F1-scores, confusion matrix
- **Visualizations:** Loss curves, confusion matrix, classification report
- **Sample Predictions:** Real examples with model confidence scores

## Expected Performance

- **Accuracy:** 92-95% (model correctly classifies most headlines)
- **F1-Score:** 91-94% (balanced performance across categories)
- **Training Time:** 10-20 minutes (with GPU) to 1-2 hours (CPU)
- **Inference Time:** <100ms per headline

## Key Technologies & Libraries

| Technology | Purpose | Version |
|-----------|---------|---------|
| PyTorch | Neural network framework | 2.0.0 |
| Transformers | BERT model and utilities | 4.30.0 |
| Datasets | Data loading and processing | 2.13.0 |
| scikit-learn | Metrics and utilities | 1.3.0 |
| Pandas | Data manipulation | 2.0.0 |
| Numpy | Numerical operations | 1.24.0 |
| Matplotlib/Seaborn | Visualization | 3.7.0/0.12.0 |

## Installation and Execution

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Run the notebook:
   ```bash
   jupyter notebook task_1_notebook.ipynb
   ```

3. Execute cells sequentially to:
   - Load and preprocess data
   - Train the model
   - Evaluate performance
   - View results and visualizations

## Practical Applications

- **Content Categorization:** Automatically tag news articles for CMS
- **News Aggregation:** Route news to appropriate sections in apps
- **Content Recommendation:** Recommend similar news based on category
- **Spam Detection:** Extend to identify non-news content
- **Multi-language:** Adapt model for news in other languages

## References

- BERT Paper: [BERT: Pre-training of Deep Bidirectional Transformers](https://arxiv.org/abs/1810.04805)
- Hugging Face Transformers: https://huggingface.co/docs/transformers/
- AG News Dataset: https://huggingface.co/datasets/ag_news
- Fine-tuning Guide: https://huggingface.co/docs/transformers/training

## Troubleshooting

- **GPU Memory Error:** Use `batch_size=8` instead of 16 in the notebook
- **Slow on CPU:** Consider using Google Colab with GPU acceleration
- **Data Download Issues:** Check internet connection and Hugging Face accessibility

---

**Task Type:** Classification  
**Difficulty:** Intermediate  
**Setup Date:** April 7, 2026  
**Expected Duration:** 1-2 hours
