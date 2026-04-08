# Task 5: Auto Tagging Support Tickets Using LLM

## Overview

This task demonstrates using modern Large Language Models (LLMs) to automatically categorize support tickets without traditional supervised training. By employing prompt engineering techniques across three approaches (zero-shot, few-shot, and fine-tuned), this project shows the evolution of LLM-based classification from simple prompts to optimized solutions.

This reflects industry trends where companies move from manual tagging to LLM-based automation, reducing costs by 80%+ while improving consistency. Companies like Zendesk, Intercom, and Help Scout use similar approaches to automate ticket routing and categorization.

## Problem Statement

Given free-form text descriptions of customer support tickets, automatically assign one or more relevant tags/categories (e.g., Billing, Technical, Account, General) to route tickets to appropriate teams. This is critical for support efficiency, SLA tracking, and team workload distribution.

## What You'll Learn

- **Prompt Engineering:** Crafting effective prompts for LLMs
- **Zero-shot Classification:** Direct classification without training examples
- **Few-shot Learning:** In-context learning with examples in prompts
- **Fine-tuning:** Training LLMs for specific domains (optional)
- **Label Ranking:** Predicting multiple labels with confidence scores
- **Evaluation Metrics:** Accuracy, precision, recall, F1-score for multi-label classification
- **Cost Optimization:** Balancing accuracy with API costs
- **Prompt Templates:** Reusable prompt patterns

## Dataset Details

- **Type:** Support ticket corpus (free-form text)
- **Size:** Generated synthetically (typically 100-500 examples)
- **Features:** Ticket description (1-500 words of text)
- **Categories:** Predefined tags (e.g., Billing, Technical, Account, General, Other)
- **Labels:** Multi-class classification (single best category)
- **Characteristics:**
  - Informal language (typos, abbreviations)
  - Mixed urgency levels
  - Varies by length and detail
  - Real-world ambiguity

Example ticket:
```
"My internet was down all morning! The router didn't respond and 
I couldn't connect. Tech support wasn't available. Very frustrated!"
Category: Technical
```

## Technical Architecture

### Components Used

1. **Transformers (Hugging Face)** - Pre-trained LLMs and utilities
2. **LangChain** - LLM chains and prompt templates
3. **OpenAI/Hugging Face APIs** - LLM inference
4. **Torch** - Model loading and utilities
5. **scikit-learn** - Evaluation metrics
6. **Pandas** - Data handling
7. **Python-dotenv** - Configuration management

### Three Approaches Compared

| Approach | Training | Time | Accuracy | Cost |
|----------|----------|------|----------|------|
| **Zero-shot** | None | <1 hour | 70-75% | Lowest |
| **Few-shot** | None | 1-2 hours | 80-85% | Low |
| **Fine-tuned** | Yes | 2-4 hours | 88-92% | Medium |

## Workflow / Implementation Steps

### Approach 1: Zero-Shot Classification

**Concept:** Ask LLM to classify without any examples, relying on its training knowledge

**Implementation:**
```
Prompt Template:
  "You are a support ticket classifier. Classify this ticket into one category.
  
  Categories: Billing, Technical, Account, General, Other
  
  Ticket: {ticket_text}
  
  Category:"
```

**Process:**
- Create basic prompt template
- Send each ticket to LLM API
- Extract predicted category
- Calculate confidence (if available)
- Evaluate accuracy against ground truth

**Performance:** Fast but less accurate (70-75%)

### Approach 2: Few-Shot Learning

**Concept:** Include example tickets in the prompt to improve understanding

**Implementation:**
```
Prompt Template:
  "You are a support ticket classifier. Use the examples below to understand 
   the categories, then classify the new ticket.
   
  Examples:
  - "My card was charged twice!" -> Billing
  - "Website is down, can't access" -> Technical
  - "Update my password" -> Account
  
  Ticket: {ticket_text}
  
  Category:"
```

**Process:**
- Select 3-5 representative examples per category
- Build few-shot prompt with examples
- Send to LLM with new ticket
- Extract and track predictions
- Compare with zero-shot results

**Performance:** Better accuracy (80-85%) with same inference pipeline

### Approach 3: Fine-tuning (Optional)

**Concept:** Train/adjust LLM weights specifically for ticket classification

**Implementation:**
- Prepare training data (tickets + categories)
- Fine-tune open-source model (e.g., BERT, DistilBERT via Hugging Face)
- Create specialized model for this domain
- Deploy for inference

**Performance:** Best accuracy (88-92%) but requires training

### Post-Processing and Top-3 Prediction

After classification:
- Extract probabilities/confidence scores
- Rank all categories by confidence
- Return top 3 predictions with scores
- Store for analysis and feedback

```python
Example Output:
Ticket: "My password won't reset"
Top 3 predictions:
  1. Account (92% confidence)
  2. Technical (6% confidence)
  3. Billing (2% confidence)
```

### 4. Evaluation Metrics

Calculate comprehensive metrics:
- **Accuracy:** Percentage of correct predictions
- **Precision:** When predicting category X, how often correct
- **Recall:** Of actual category X tickets, how many identified
- **F1-Score:** Harmonic mean of precision and recall
- **Confusion Matrix:** Shows which categories are confused
- **Per-Category Performance:** Identify weak categories

### 5. Comparative Analysis

Compare approaches:
- Accuracy across zero-shot, few-shot, fine-tuned
- Speed (zero-shot fastest, fine-tuned slower)
- Cost (zero-shot cheap API calls, fine-tuned higher upfront)
- Failure analysis (which tickets misclassified)

### 6. Deployment Strategy

Choose best approach based on requirements:
- **Zero-shot:** Quick MVP, acceptable errors
- **Few-shot:** Balance speed and accuracy
- **Fine-tuned:** Maximum accuracy, more complex deployment

## What Gets Saved

After execution, the notebook produces:
- **Predictions:** CSV with tickets, predicted tags, confidence scores
- **Comparison Results:** Zero-shot vs few-shot vs fine-tuned metrics
- **Top-3 Predictions:** JSON with ranked category predictions
- **Confusion Matrices:** Per-approach confusion matrices
- **Evaluation Report:** Metrics summary and recommendations
- **Failed Cases:** Tickets the model struggled with
- **Cost Analysis:** Token count and estimated API costs

## Expected Performance

- **Zero-Shot Accuracy:** 70-75% (baseline)
- **Few-Shot Accuracy:** 80-85% (improved with examples)
- **Fine-Tuned Accuracy:** 88-92% (best results)
- **Top-3 Accuracy:** >95% (correct tag in top 3)
- **Processing Speed:** 1000s/minute (inference limited by API)
- **Per-Ticket Cost:** $0.001-$0.01 (depends on token count)

## Key Technologies & Libraries

| Technology | Purpose | Version |
|-----------|---------|---------|
| Transformers | LLM models and tokenizers | 4.30.0 |
| Torch | Model infrastructure | 2.0.0 |
| OpenAI | API for LLM access | 0.27.8 |
| LangChain | LLM chains and templates | 0.0.250 |
| Pandas | Data handling | 2.0.0 |
| Numpy | Numerical operations | 1.24.0 |
| scikit-learn | Metrics and evaluation | 1.3.0 |
| Datasets | Training data utilities | 2.13.0 |
| Matplotlib/Seaborn | Visualization | 3.7.0/0.12.0 |

## Installation and Execution

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Configure API access (optional, for OpenAI LLM):
   ```bash
   export OPENAI_API_KEY="your-api-key"
   ```

3. Run the notebook:
   ```bash
   jupyter notebook task_5_notebook.ipynb
   ```

4. Execute cells to:
   - Load ticket dataset
   - Run zero-shot classification
   - Run few-shot classification
   - Optionally fine-tune model
   - Compare all approaches
   - Generate evaluation reports

## Practical Applications

- **Support Ticket Routing:** Automatically route tickets to right team
- **Spam Detection:** Identify and filter spam or irrelevant tickets
- **SLA Management:** Prioritize urgent tickets (if urgency tag available)
- **Knowledge Base:** Route tickets to relevant FAQ solutions
- **Load Balancing:** Distribute tickets based on team capacity
- **analytics:** Understand ticket distribution and trends
- **Escalation Rules:** Flag complex tickets for human review
- **Feedback Loop:** Use predictions to improve models over time

## Prompt Engineering Best Practices

1. **Clarity:** Be explicit about what you want
   - Good: "Classify this ticket into EXACTLY one category"
   - Bad: "What's this about?"

2. **Examples:** Few-shot prompts provide context
   - Include diverse examples
   - Show edge cases
   - Format consistently

3. **Structure:** Organize prompt clearly
   - System role first
   - Examples second
   - New input last

4. **Constraints:** Limit LLM output
   - "Answer with only the category name"
   - Prevents hallucinations and extra text

5. **Iteration:** Test and refine prompts
   - Start simple, add examples as needed
   - Test edge cases
   - Measure accuracy after each change

## Cost Optimization

- **Zero-shot:** ~100 tokens per ticket, cheapest
- **Few-shot:** ~300 tokens per ticket (examples add tokens)
- **Batch Processing:** Process multiple tickets in one call
- **Local Models:** Use free open-source LLMs (LLaMA, Mistral) instead of API
- **Token Limits:** Trim examples if still accurate

Example: 100K tickets at $0.01/ticket = $1000 (zero-shot) vs $2000 (few-shot)

## Troubleshooting

- **Poor Accuracy:** Try few-shot or fine-tuning
- **Wrong Categories:** Refine prompt template
- **API Errors:** Check API keys, rate limits, token counts
- **Slow Processing:** Use batch APIs or lower ticket volume
- **Cost Issues:** Use local models or zero-shot exclusively
- **Inconsistent Results:** Set temperature=0 for deterministic results

---

**Task Type:** LLM-based Classification / Prompt Engineering  
**Difficulty:** Intermediate  
**Setup Date:** April 7, 2026  
**Expected Duration:** 1.5-2.5 hours
