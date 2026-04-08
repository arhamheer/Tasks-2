# Getting Started Guide - DevelopersHub AI/ML Internship Tasks

## Prerequisites

- Python 3.8 or higher
- pip (Python package installer)
- 8GB+ RAM recommended
- GPU (optional, for faster training)

## Setup Instructions

### 1. Create Project Directories

All task directories are already created with the following structure:
```
potti/
├── task_1_bert_news_classifier/
├── task_2_ml_pipeline_churn/
├── task_3_multimodal_housing/
├── task_4_rag_chatbot/
└── task_5_llm_ticket_tagging/
```

### 2. Create and Activate Virtual Environment

**On Linux/Mac:**
```bash
python3 -m venv venv
source venv/bin/activate
```

**On Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

### 3. Install Dependencies for Each Task

Navigate to each task folder and install requirements:

```bash
# For Task 1
cd task_1_bert_news_classifier
pip install -r requirements.txt

# For Task 2
cd ../task_2_ml_pipeline_churn
pip install -r requirements.txt

# And so on for other tasks...
```

### 4. Running Jupyter Notebooks

Each task includes a Jupyter notebook with complete implementation:

```bash
# Install Jupyter (if not already installed)
pip install jupyter

# Start Jupyter
jupyter notebook

# Open the notebook for the task you want to work on
# e.g., task_1_notebook.ipynb
```

## Task-Specific Instructions

### Task 1: BERT News Classifier
- Dataset: Automatically downloaded from Hugging Face
- Model: bert-base-uncased (will be downloaded)
- Output: Trained model saved in `bert_news_classifier/` folder
- Deployment: Streamlit app can be created from the notebook

### Task 2: ML Pipeline Churn Prediction
- Dataset: Automatically downloaded from GitHub
- Models: LogisticRegression + RandomForest
- Output: Pipeline saved as `churn_prediction_pipeline.pkl`
- Can be directly loaded for inference

### Task 3: Multimodal Housing Price Prediction
- Dataset: Synthetically generated (with option to use real data)
- Model: Custom MultimodalHousingModel (ResNet50 + Tabular)
- Output: Model state saved as `multimodal_housing_model.pth`
- GPU recommended for faster training

### Task 4: RAG Chatbot with LangChain
- Knowledge Base: Sample documents provided (expandable)
- Embeddings: sentence-transformers (auto-downloaded)
- Storage: FAISS vector store
- Deployment: Streamlit web interface can be created

### Task 5: LLM Support Ticket Tagging
- Dataset: Synthetically generated
- Models: Zero-shot, Few-shot classification
- Inference: Uses facebook/bart-large-mnli
- Output: Predictions saved in JSON

## Running Individual Tasks

### Quick Start
```bash
# 1. Navigate to task folder
cd task_1_bert_news_classifier

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run notebook
jupyter notebook task_1_notebook.ipynb
```

## GPUAcceleration (Optional)

For tasks 1 and 3 (which use deep learning):

**Check GPU availability:**
```python
import torch
print(torch.cuda.is_available())
print(torch.cuda.get_device_name(0))
```

**Install GPU support:**
```bash
# For NVIDIA GPU
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

## Troubleshooting

### 1. Package Installation Issues
```bash
# Update pip
pip install --upgrade pip

# Clear pip cache
pip cache purge

# Install with no cache
pip install --no-cache-dir -r requirements.txt
```

### 2. CUDA/GPU Issues
```bash
# Verify PyTorch installation
python -c "import torch; print(torch.__version__); print(torch.cuda.is_available())"

# Fall back to CPU
# Modify code: device = torch.device('cpu')
```

### 3. Memory Issues
- Reduce batch size in notebooks
- Use smaller models or datasets
- Process data in smaller chunks

### 4. Slow Download Speeds
- Pre-download large models and datasets
- Use offline mode where available
- Check internet connection

## GitHub Setup

### Initialize Git Repository
```bash
cd /path/to/potti
git init
git add .
git commit -m "Initial commit: AI/ML internship tasks setup"
```

### Create GitHub Repository
1. Go to github.com and create a new repository
2. Name it something like "DevelopersHub-AI-ML-Internship"
3. Add remote:
```bash
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git branch -M main
git push -u origin main
```

## Submission Checklist

For each completed task:
- [ ] Jupyter notebook with all sections completed
- [ ] README.md with approach and results
- [ ] All visualizations generated and saved
- [ ] Model/pickle files saved
- [ ] Code quality: well-commented, clear structure
- [ ] Results summary file created
- [ ] Pushed to GitHub

## Timeline

- **12 April 2026:** Recommended completion of first task
- **19 April 2026:** Recommended completion of second task  
- **26 April 2026:** Recommended completion of third task
- **28 April 2026:** **FINAL SUBMISSION DEADLINE**

## Resources

### Documentation
- [Hugging Face Transformers](https://huggingface.co/docs/transformers/)
- [scikit-learn Pipeline API](https://scikit-learn.org/stable/modules/compose.html#pipeline)
- [LangChain Documentation](https://python.langchain.com/)
- [PyTorch Documentation](https://pytorch.org/docs/stable/index.html)

### Useful Tutorials
- [Transfer Learning with BERT](https://huggingface.co/docs/transformers/training)
- [ML Pipelines Best Practices](https://scikit-learn.org/stable/modules/pipeline.html)
- [Multimodal Learning](https://arxiv.org/abs/2301.04856)
- [RAG Implementation](https://python.langchain.com/docs/use_cases/qa_structured_sources)

## Support

For issues or questions:
1. Check task-specific README files
2. Review notebook comments
3. Search documentation links
4. Check error messages carefully
5. Test with smaller datasets first

---

**Good luck with your AI/ML internship tasks!**

Last updated: April 7, 2026
