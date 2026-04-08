# DevelopersHub AI/ML Engineering Internship Tasks - Complete Suite

A comprehensive collection of 5 advanced AI/ML projects demonstrating modern machine learning techniques, from NLP transformers to multimodal learning and LLM applications.

## Project Overview

This repository contains hands-on implementations of real-world AI/ML problems, progressing from foundational concepts to cutting-edge techniques. Each task is self-contained with complete implementations, data handling, and detailed explanations.

**Timeline:** Due Date - 28th April, 2026  
**Status:** All 5 tasks completed and ready for execution  
**Requirement:** Complete at least 3 out of 5 tasks (All 5 provided)

---

## Tasks at a Glance

### Task 1: BERT News Classifier
**NLP & Transfer Learning**

Fine-tune the BERT transformer model to classify news headlines into 4 categories (World, Sports, Business, Technology). Learn transfer learning by adapting a pre-trained language model to your specific task.

- **What:** Multi-class text classification
- **How:** BERT fine-tuning with PyTorch
- **Data:** AG News Dataset (120K+ headlines)
- **Expected Result:** 92-95% accuracy
- **Duration:** 1-2 hours
- **Difficulty:** Intermediate

[More Details](./task_1_bert_news_classifier/README.md)

---

### Task 2: ML Pipeline for Churn Prediction
**Production-Ready ML Engineering**

Build an end-to-end scikit-learn pipeline to predict customer churn. Learn best practices for model development including preprocessing, hyperparameter tuning, and model persistence—all in a single reproducible pipeline.

- **What:** Binary classification with pipeline architecture
- **How:** scikit-learn Pipeline + GridSearchCV
- **Data:** Telco Customer Churn Dataset (7000+ records)
- **Expected Result:** 80-85% accuracy, AUC > 0.85
- **Duration:** 1-1.5 hours
- **Difficulty:** Intermediate

[More Details](./task_2_ml_pipeline_churn/README.md)

---

### Task 3: Multimodal Housing Price Prediction
**Advanced Deep Learning Architecture**

Combine image and tabular data to predict house prices. Extract CNN features from house photos and fuse them with structured data, demonstrating how modern AI systems handle multiple data modalities simultaneously.

- **What:** Regression with multimodal fusion
- **How:** PyTorch + ResNet50 + GradientBoosting
- **Data:** Synthetic housing dataset with images
- **Expected Result:** R² > 0.85, MAE < $50K
- **Duration:** 1.5-2 hours
- **Difficulty:** Advanced

[More Details](./task_3_multimodal_housing/README.md)

---

### Task 4: RAG Chatbot with LangChain
**Conversational AI & Knowledge Retrieval**

Build a context-aware chatbot using Retrieval-Augmented Generation. Instead of relying solely on training data, the system retrieves relevant documents and uses them to generate accurate, conversational responses. This is the architecture behind many modern AI assistants.

- **What:** Conversational AI with semantic search
- **How:** LangChain + LLM + FAISS embeddings
- **Data:** Custom knowledge base + conversation history
- **Expected Result:** Semantic search accuracy > 85%, <3s response time
- **Duration:** 2-3 hours
- **Difficulty:** Advanced

[More Details](./task_4_rag_chatbot/README.md)

---

### Task 5: LLM-Based Support Ticket Tagging
**Prompt Engineering & LLM Classification**

Automatically categorize support tickets using three approaches: zero-shot, few-shot, and fine-tuned LLM methods. Understand how modern language models enable efficient text classification without traditional training data.

- **What:** Multi-approach text classification
- **How:** Prompt engineering + LLM APIs
- **Data:** Synthetic support ticket corpus
- **Expected Result:** Zero-shot 70-75%, Few-shot 80-85%, Fine-tuned 88-92%
- **Duration:** 1.5-2.5 hours
- **Difficulty:** Intermediate

[More Details](./task_5_llm_ticket_tagging/README.md)

---

## Technology Stack

### Core ML/AI Libraries
- **PyTorch** (v2.0.0) - Deep learning framework
- **Transformers** (v4.30.0) - Pre-trained NLP models via Hugging Face
- **scikit-learn** (v1.3.0) - Classic ML algorithms

### Data Processing
- **Pandas** (v2.0.0) - Data manipulation and analysis
- **Numpy** (v1.24.0) - Numerical operations
- **Torchvision** (v0.15.0) - Computer vision utilities

### Advanced AI
- **LangChain** (v0.0.250) - LLM orchestration framework
- **Sentence Transformers** (v2.2.2) - Semantic embeddings
- **FAISS** (v1.7.4) - Vector similarity search

### Deployment & Interface
- **Streamlit** (v1.26.0) - Web app framework
- **Jupyter** - Interactive notebooks

### Utilities
- **Matplotlib & Seaborn** - Visualization
- **scikit-learn** - Metrics and evaluation

---

## Project Structure

```
potti/
├── README.md                                    # This file
├── SETUP_GUIDE.md                              # Installation and setup instructions
├── PROJECT_MANIFEST.md                          # Detailed file manifest
├── requirements.txt                             # Python dependencies (combined)
├── .gitignore                                   # Git configuration
│
├── task_1_bert_news_classifier/
│   ├── README.md                               # Detailed task description
│   ├── requirements.txt                        # Task-specific dependencies
│   ├── task_1_notebook.ipynb                   # Complete implementation
│   └── bert_news_classifier/                   # Saved model artifacts
│       ├── config.json
│       ├── special_tokens_map.json
│       ├── tokenizer_config.json
│       └── vocab.txt
│
├── task_2_ml_pipeline_churn/
│   ├── README.md                               # Detailed task description
│   ├── requirements.txt                        # Task-specific dependencies
│   ├── task_2_notebook.ipynb                   # Complete implementation
│   └── results_summary.txt                     # Evaluation results
│
├── task_3_multimodal_housing/
│   ├── README.md                               # Detailed task description
│   ├── requirements.txt                        # Task-specific dependencies (FIXED)
│   └── task_3_notebook.ipynb                   # Complete implementation
│
├── task_4_rag_chatbot/
│   ├── README.md                               # Detailed task description
│   ├── requirements.txt                        # Task-specific dependencies
│   ├── task_4_notebook.ipynb                   # Complete implementation
│   ├── conversation_history.json               # Chat logs
│   └── results_summary.txt                     # Deployment results
│
└── task_5_llm_ticket_tagging/
    ├── README.md                               # Detailed task description
    ├── requirements.txt                        # Task-specific dependencies
    ├── task_5_notebook.ipynb                   # Complete implementation
    ├── top3_predictions.json                   # Model predictions
    └── results_summary.txt                     # Evaluation results
```

---

## Setup and Installation

### Prerequisites

- Python 3.10 or 3.11 with pyenv
- 8GB+ RAM (16GB recommended)
- GPU (optional but recommended for Tasks 1, 3, 4)
- 10GB+ free disk space

### Quick Start

1. **Clone or download the repository:**
   ```bash
   cd potti
   ```

2. **Install dependencies for all tasks:**
   ```bash
   pip install -r requirements.txt
   ```
   
   Or install task-specific dependencies:
   ```bash
   cd task_1_bert_news_classifier
   pip install -r requirements.txt
   ```

3. **Start Jupyter and run notebooks:**
   ```bash
   jupyter notebook task_1_notebook.ipynb
   ```

### Using pyenv (Recommended)

```bash
# Create project-specific Python environment
pyenv local 3.10.13
python -m venv venv
source venv/bin/activate

# Install all dependencies
pip install -r requirements.txt
```

For Task 3 specifically (Keras issue fixed):
```bash
cd task_3_multimodal_housing
pip install -r requirements.txt
# Now works without Keras compatibility issues
```

---

## Task Architecture & Learning Path

### Recommended Execution Order

1. **Start with Task 2** (30-90 min)
   - Foundation: Learn classic ML pipeline pattern
   - Small dependencies, works everywhere
   - Builds core concepts: preprocessing, model training, evaluation

2. **Move to Task 1** (1-2 hours)
   - NLP specialization: Learn transformers
   - Larger downloads (BERT model ~400MB)
   - Depends on concepts from Task 2

3. **Try Task 3** (1.5-2 hours)
   - Advanced architecture: Multimodal learning
   - Combines images + tabular data
   - Introduces PyTorch custom models
   - GPU highly recommended

4. **Explore Tasks 4 & 5** (2-3.5 hours each)
   - Cutting-edge AI: LLMs and prompting
   - Less traditional, more experimental
   - Can run independently
   - Best for understanding modern AI trends

### Complexity Progression

```
Beginner          Task 2 (scikit-learn)
    ↓
Intermediate      Task 1 (BERT) + Task 5 (Prompting)
    ↓
Advanced          Task 3 (Multimodal) + Task 4 (RAG)
```

---

## Running Individual Tasks

Each task is self-contained and can run independently.

### Task 1: News Classifier
```bash
cd task_1_bert_news_classifier
pip install -r requirements.txt
jupyter notebook task_1_notebook.ipynb
# Expected runtime: 10-40 min (depending on GPU)
```

### Task 2: Churn Pipeline
```bash
cd task_2_ml_pipeline_churn
pip install -r requirements.txt
jupyter notebook task_2_notebook.ipynb
# Expected runtime: 2-5 min
```

### Task 3: Housing Price (FIXED)
```bash
cd task_3_multimodal_housing
pip install -r requirements.txt  # Now keras-free and compatible
jupyter notebook task_3_notebook.ipynb
# Expected runtime: 5-15 min (or 1-2 min with GPU)
```

### Task 4: RAG Chatbot
```bash
cd task_4_rag_chatbot
pip install -r requirements.txt
# Set API key if using OpenAI
export OPENAI_API_KEY="your-api-key"
jupyter notebook task_4_notebook.ipynb
# Optional: streamlit run app.py
```

### Task 5: Ticket Tagging
```bash
cd task_5_llm_ticket_tagging
pip install -r requirements.txt
jupyter notebook task_5_notebook.ipynb
# Expected runtime: 10-30 min
```

---

## Key Concepts Covered

### Machine Learning Fundamentals
- Classification vs Regression
- Train-test splits and cross-validation
- Hyperparameter tuning
- Evaluation metrics for different problem types
- Feature preprocessing and scaling

### Deep Learning
- Transfer learning with pre-trained models
- Transformer architecture and BERT
- Convolutional Neural Networks (ResNet)
- Custom model architectures in PyTorch
- Multi-task learning with multiple data modalities

### NLP Techniques
- Tokenization and embeddings
- Fine-tuning language models
- Semantic search and similarity
- Prompt engineering
- Few-shot and zero-shot learning

### Production Practices
- Pipeline architecture for reproducibility
- Model serialization and loading
- Evaluation frameworks and metrics
- Deployment considerations
- API integration (LangChain, OpenAI)

### Modern AI Topics
- Retrieval-Augmented Generation (RAG)
- Large Language Models (LLMs)
- Multimodal learning
- Semantic embeddings (FAISS)
- In-context learning

---

## Performance Expectations

| Task | Problem Type | Expected Accuracy | Training Time | GPU Benefit |
|------|:----------:|:---------------:|:------------:|:-----------:|
| Task 1 | Classification | 92-95% | 10-40 min | Very High |
| Task 2 | Classification | 80-85% | 2-5 min | Low |
| Task 3 | Regression | R²>0.85 | 5-15 min | Very High |
| Task 4 | Retrieval+Gen | >85% recall | Setup only | N/A |
| Task 5 | Classification | 70-92% | 10-30 min | Low |

---

## Troubleshooting Common Issues

### Keras Error in Task 3 (FIXED)
**Problem:** "Could not find a version that satisfies the requirement keras==2.13.0"

**Solution:** Updated requirements.txt removes unnecessary keras. PyTorch handles all image processing.

### GPU Memory Error
**Symptom:** `RuntimeError: CUDA out of memory`

**Solutions:**
- Reduce batch size (e.g., 8 instead of 16)
- Use CPU instead (slower but works)
- Use Google Colab with free GPU
- Reduce model size (use smaller pre-trained models)

### Slow on CPU
**Symptom:** Tasks 1, 3, 4 take 10+ minutes

**Solutions:**
- Use GPU if available
- Use Google Colab (free GPU)
- For testing: reduce dataset size
- Run smaller models

### API Key Issues (Task 4 & 5)
**Problem:** OpenAI API key not found

**Solution:**
```bash
export OPENAI_API_KEY="sk-..."
# Or create .env file with OPENAI_API_KEY=...
```

### Import Errors
**Problem:** `ModuleNotFoundError: No module named 'torch'`

**Solution:**
```bash
pip install -r requirements.txt
# Or specific package:
pip install torch==2.0.0
```

---

## Resources and References

### Documentation
- [PyTorch Official Docs](https://pytorch.org/docs/)
- [Hugging Face Transformers](https://huggingface.co/docs/transformers/)
- [scikit-learn Documentation](https://scikit-learn.org/stable/documentation.html)
- [LangChain Documentation](https://python.langchain.com/)

### Tutorials & Papers
- [BERT Paper](https://arxiv.org/abs/1810.04805)
- [Transfer Learning](https://cs231n.github.io/transfer-learning/)
- [Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)
- [RAG Explained](https://arxiv.org/abs/2005.11401)

### Datasets
- [Hugging Face Datasets Hub](https://huggingface.co/datasets)
- [Kaggle Datasets](https://www.kaggle.com/datasets)
- [Papers with Code](https://paperswithcode.com/datasets)

---

## What You'll Build

By completing these tasks, you'll have:

1. Fine-tuned production-grade NLP models
2. Professional ML pipelines with hyperparameter optimization
3. Advanced deep learning systems combining multiple data types
4. Modern retrieval-augmented AI applications
5. LLM-powered automation solutions

These are real-world applications used by Fortune 500 companies across finance, healthcare, e-commerce, and technology sectors.

---

## Version Information

- **Python:** 3.10.13 or 3.11.3 (via pyenv)
- **PyTorch:** 2.0.0
- **Transformers:** 4.30.0
- **scikit-learn:** 1.3.0
- **Setup Date:** April 7, 2026
- **Last Updated:** April 8, 2026

---

## Support and Questions

Refer to individual task README.md files for specific questions about that task. Each task includes:
- Detailed problem explanation
- Architecture diagrams
- Step-by-step workflows
- Troubleshooting guides
- References and further reading

---

**Status:** Ready for Implementation  
**Completion Target:** April 28, 2026
