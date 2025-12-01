# Retail Price Optimization Engine

A machine learning pipeline that predicts retail prices and identifies key pricing drivers using gradient boosting regression.

## Overview

This project builds an end-to-end price prediction system that:
- Predicts total retail prices based on product and market features
- Identifies the top pricing drivers for business interpretability
- Compares multiple ML models to find the best performer
- Exports results for Power BI visualization

## Pipeline

1. **Load Data** - Imports retail pricing data from Excel
2. **Preprocess** - Cleans data and selects numeric features
3. **Feature Selection** - Uses ANOVA F-test to identify top 5 features
4. **Model Training** - Trains three models (Linear Regression, Random Forest, Gradient Boosting)
5. **Evaluation** - Compares models using MAE and R² metrics
6. **Export** - Saves best model and performance metrics

## Key Features Used

The algorithm automatically selects the top 5 most relevant features:
- `qty` - Quantity sold
- `unit_price` - Base unit price
- `customers` - Customer count
- `s` - Seasonal factor
- `lag_price` - Previous period price

## Model Performance

| Model | MAE | R² Score |
|-------|-----|----------|
| Linear Regression | 411.15 | 0.8335 |
| Random Forest | 103.13 | 0.9490 |
| **Gradient Boosting** | **120.34** | **0.9612** |

The Gradient Boosting model achieves the best R² score of 0.9612, explaining 96% of price variance.

## Requirements

```
pandas
numpy
scikit-learn
joblib
```

## Usage

1. Place `retail_price.xls` in the project directory
2. Run all cells in the notebook
3. The best model is saved as `best_model.pkl`
4. Performance metrics are exported to `model_performance_comparison.csv`

## Outputs

- `best_model.pkl` - Trained Gradient Boosting model
- `model_performance_comparison.csv` - Model comparison metrics
- Power BI compatible data exports

## Dataset

The dataset includes 30 features covering:
- Product attributes (weight, photos, descriptions)
- Pricing data (unit price, freight, competitor prices)
- Temporal features (month, year, weekday, holiday)
- Market factors (customer count, volume, scores)
