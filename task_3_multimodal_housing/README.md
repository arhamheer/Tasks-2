# Task 3: Multimodal Housing Price Prediction

## Overview

This task builds a sophisticated machine learning system that combines multiple data modalities (images and tabular data) to predict house prices. Using a real Southern California housing dataset with 15,474 properties and authentic house photographs, this project demonstrates practical multimodal learning applied to a real-world real estate valuation problem.

The system extracts features from different sources (CNN for images, normalization for tabular data) and fuses them for enhanced price predictions. This approach mirrors production systems used by major real estate platforms and financial institutions for automated property valuation.

## Problem Statement

Given a house photograph and property data (bedrooms, bathrooms, square footage), predict the market selling price for Southern California residential properties. This real-world regression problem combines two complementary data sources: visual features from authentic house photos (reflect condition, aesthetics, architecture) and numerical features from property records (size, configuration, structure).

The model learns to value properties based on both what the house looks like and its structural characteristics, mimicking how real estate professionals combine visual inspection with property specifications.

## What You'll Learn

- **Multimodal Architecture:** Combining different data types in one model
- **CNN Feature Extraction:** Using pre-trained networks (ResNet50) to extract image features
- **Feature Fusion:** Combining image and tabular features effectively
- **Transfer Learning:** Leveraging pre-trained computer vision models
- **Regression with Deep Learning:** Continuous value prediction
- **PyTorch Workflow:** Custom dataset classes, models, and training loops
- **Real Estate Domain:** Understanding housing price factors

## Dataset Details

- **Name:** Southern California Housing Dataset (SoCal2)
- **Source:** Real property listings from multiple Southern California cities and regions
- **Size:** 15,474 property records with matching house photographs
- **Location Coverage:** Diverse regions across Southern California (Salton City, Brawley, Imperial, Calexico, Frazier Park, Tehachapi, etc.)

**Image Data:**
- Total images: 15,474 property photos
- Format: JPEG files
- Location: `archive/socal2/socal_pics/`
- Preprocessing: Resized to 224x224 pixels for CNN processing
- Real house photos showing varied architectural styles and conditions

**Tabular Features:** (6 attributes)
- `bed` (bedrooms): 1-8 rooms per property
- `bath` (bathrooms): 1-6 bathrooms per property
- `sqft` (square footage): 700-6,700 sq ft ranges
- `street`: Street address for reference
- `city` (citi): City/region name in Southern California
- `n_city`: Numeric region code

**Target Variable:**
- `price`: House selling price in USD
- Range: $201,900 - $2,000,000+
- Distribution: Right-skewed (typical real estate market)
- Mean: ~$633,000

**Data Split:**
- Training: 70% (10,832 samples)
- Validation: 15% (2,321 samples)
- Testing: 15% (2,321 samples)
- All with corresponding house images and features

## Technical Architecture

### Components Used

1. **PyTorch** - Deep learning framework with custom models
2. **Torchvision** - Pre-trained CNN models (ResNet50)
3. **scikit-learn** - Preprocessing, scaling, and regression models
4. **Pandas & Numpy** - Data manipulation
5. **Pillow** - Image loading and preprocessing
6. **Matplotlib & Seaborn** - Result visualization

### Model Architecture

The system uses a two-stream architecture:

```
Image Stream:
  House Photo (3, 224, 224)
         |
    ResNet50 (pretrained, 15 layers frozen)
         |
    Feature Extraction: (512 features)
         |
         v
    [Feature Fusion - Concatenation]
         ^         ^
    Tabular   Image
    Features  Features
    (3D)      (512D)
         |
    Multi-layer FC Network
         |
    Price Prediction (millions USD)
```

Two indReal Data Loading
- Load `socal2.csv` containing 15,474 property records
- Access house photos from `socal2/socal_pics/` directory
- Map image IDs to actual house photographs
- Filter out records with missing images
- Verify data quality and price distribution

### 2. Feature Engineering
- **Image Features:** Normalize input to 224x224 pixels
- **Tabular Features:** Normalize bedrooms, bathrooms, square footage
  - Beds: divide by 8 (max expected)
  - Baths: divide by 6 (max expected)
  - Sqft: divide by 8,000 (max expected)
- **Price Normalization:** Divide by 1,000,000 for training stability
- All features scaled to [0-1] range

### 3. Image Feature Extraction
- Load pre-trained ResNet50 model (trained on ImageNet)
- Pass each property photo through ResNet50
- Extract 512-dimensional feature vector per image
- Captures visual characteristics: condition, architecture, landscaping, quality

### 4. Tabular Feature Processing
- Extract bed, bath, sqft from CSV
- Normalize using max values (bed/8, bath/6, sqft/8000)
- Creates 3-dimensional feature vector per property
- Scales structural/size characteristics appropriately

### 5. Feature Fusion
- Concatenate 512 image features + 3 tabular features = 515 total
- Pass fused features through multi-layer fully connected network
- Learn non-linear relationships between modalities
- Output: Single price prediction value (in millions USD)

### 6. Model Training
- Split into train/val/test (70/15/15)
- Train with Adam optimizer, learning rate 0.0001
- CosineAnnealing learning rate scheduler
- Early stopping with patience of 5 epochs
- MSE loss function
- Batch size of 32 for efficient GPU utilization

### 7. Evaluation Metrics
- **MAE:** Average prediction error in dollars
- **RMSE:** Root mean squared error (penalizes outliers)
- **MAPE:** Mean absolute percentage error for relative performance
- **R²:** What proportion of variance model explains
- **Predict vs Actual:** Visualize prediction accuracy across price rangeon in dollars
- **Root Mean Squared Error (RMSE):** Penalizes large errors more
- **R-squared (R2):** Proportion of variance explained (0-1 scale)
- **Residual Analysis:** Understanding prediction errors
- **Visualization:** Predicted vs Actual price scatter plots

## What Gets Saved

After execution, the notebook produces:
- **Trained Models:** 
  - `multimodal_housing_model.pth` - Final trained model
  - `multimodal_housing_model_best.pth` - Best checkpoint during training
- **Evaluation Metrics:** MAE, RMSE, MAPE, R-squared on test set
- **Performance Visualizations:**
  - `training_curves.png` - Training and validation loss over epochs
  - `predictions_vs_actual.png` - Predicted vs actual prices scatter plot
  - `residuals_analysis.png` - Residuals distribution and analysis
- **Results Summary:** 
  - `results_summary.txt` - Comprehensive model performance report
  - Configuration, metrics, and insights about real SoCal data performance

## Expected Performance

- **Mean Absolute Error (MAE):** $30,000-$60,000 (prediction accuracy in dollars)
- **RMSE:** $60,000-$100,000 (penalizes large errors)
- **Mean Absolute Percentage Error (MAPE):** 8-15% (percentage-based error)
- **R-squared:** 0.75-0.88 (model explains 75-88% of price variance)
- **Training Time:** 5-15 minutes (CPU) to 1-3 minutes (GPU)
- **Inference Time:** 50-200ms per property prediction

## Key Technologies & Libraries

| Technology | Purpose | Version |
|-----------|---------|---------|
| PyTorch | Neural networks and training | 2.1.2 |
| Torchvision | Pre-trained models & transforms | 0.16.2 |
| scikit-learn | Regression and preprocessing | 1.3.0 |
| Pandas | Data handling | 2.0.0 |
| Numpy | Numerical operations | 1.24.0 |
| Pillow | Image processing | 10.0.0 |
| Matplotlib/Seaborn | Visualization | 3.7.0/0.12.0 |
| tqdm | Progress bars | 4.65.0 |

## Installation and Execution

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Run the notebook:
   ```bash
   jupyter notebook task_3_notebook.ipynb
   ```

3. Execute cells sequentially to:
   - Load real Southern California housing data
   - Extract image features with ResNet50
   - Preprocess property tabular data
   - Fuse image and property features
   - Train multimodal neural network
   - Evaluate model on test set
   - Visualize results and predictions

## Practical Applications

- **Automated Valuation Models (AVMs):** Banks and lenders automatically assessing property values
- **Real Estate Listing Prices:** Zillow, Redfin, Realtor estimate home values
- **Property Investment Analysis:** Investors assessing investment opportunities
- **Tax Assessment:** County assessors valuing properties for taxation
- **Insurance Premiums:** Property-based insurance rate determination
- **Market Analysis:** Understanding price patterns across regions and property types
- **Appraisal Augmentation:** Supporting professional appraisers with data-driven baseline values
- **Portfolio Valuation:** Financial institutions valuing real estate holdings

## Key Multimodal Learning Concepts

1. **Feature Fusion:** Combining features from different modalities
2. **Transfer Learning:** Using ImageNet-trained ResNet50 for real estate images
3. **Domain Adaptation:** Applying computer vision to real estate domain
4. **Modality Weighting:** Different modalities have different importance
5. **Complementarity:** Image+Tabular > Either alone

## Troubleshooting

- **Out of Memory:** Reduce batch size or use smaller pre-trained model (ResNet18)
- **Slow Inference:** Batch process multiple images at once
- **Poor Results:** Ensure image data quality and alignment
- **Dataset Size:** Works best with 500+ samples (synthetic: 200 for demo)

---

**Task Type:** Regression / Multimodal Learning  
**Difficulty:** Advanced  
**Setup Date:** April 7, 2026  
**Expected Duration:** 1.5-2 hours
