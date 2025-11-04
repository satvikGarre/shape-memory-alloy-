# NiTiCu Hysteresis Prediction Project

## Overview
This project predicts the hysteresis (difference between transformation temperatures Af and Ms) of Shape Memory Alloys (Ni-Ti-Cu compositions) using ensemble machine learning techniques. It builds and evaluates a stacking regressor composed of Random Forest, Gradient Boosting, and Support Vector Regression models, combined with Ridge Regression as the meta-model. The model is used to explore a finely gridded composition space, identifying optimal alloy compositions with minimal hysteresis.

***

## Features

- Loads and processes experimental alloy composition and transformation temperature data.
- Creates engineered features based on elemental ratios and temperature ranges to improve model performance.
- Trains an ensemble stacking regressor to predict hysteresis values.
- Generates a dense grid of new alloy compositions within specified element percentage bounds for prediction.
- Visualizes the composition distributions and predicted hysteresis through scatter plots and heatmaps.
- Identifies top candidate compositions predicted to have low hysteresis values.

***

## Requirements

- Python 3.x
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- openpyxl (for reading Excel files)

Install required packages (if needed) via pip:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn openpyxl
```

***

## Usage

1. **Input dataset**: Load your experimental data in an Excel file named `Dataset_Final.xlsx` formatted with columns for `Ni_content`, `Ti_content`, `Cu_content`, transformation temperatures (`Af`, `As`, `Ms`, `Mf`), and others.

2. **Feature Engineering**: The script calculates elemental ratios (`Ni/Ti`, `Ni/Cu`, `Ti/Cu`) and temperature ranges (`A_range = Af - As`, `M_range = Ms - Mf`).

3. **Model Training**:  
   - The script splits data into train/test sets.  
   - Trains a stacking regressor consisting of Random Forest, Gradient Boosting, SVR as base models, and Ridge Regression as the meta model.  
   - Reports mean absolute error (MAE) and R-squared (R²) on the test data.

4. **Prediction on New Compositions**:  
   - Creates a fine-grained grid of possible new alloy compositions with constraints on element percentages.  
   - Computes features for these new compositions and predicts hysteresis values using the trained model.

5. **Results and Visualization**:  
   - Prints the best predicted alloy compositions and top candidates minimizing hysteresis.  
   - Displays histograms of elemental content distributions.  
   - Creates scatter plots showing predicted hysteresis vs. individual element contents and ratios.  
   - Generates heatmaps showing predicted hysteresis across Ni-Ti, Ni-Cu, and Ti-Cu compositional spaces.

***

## File Structure

- `Dataset_Final.xlsx`: Input dataset with alloy compositions and experimental measurements.
- `niticu.py`: Python script implementing the full pipeline: data loading, feature engineering, model training, prediction, and visualization.
- Output plots: Histograms, scatter plots, and heatmaps for exploratory data analysis and model results.

***

## How to Run

Run the script `niticu.py` in your Python environment. Make sure the `Dataset_Final.xlsx` is in the working directory. The script will perform all steps from data processing to visualization automatically.

***

## Notes

- The current grid search considers compositions varying Ni from 25% to 55%, Ti from 40% to 55%, and Cu adjusted accordingly with a minimum Cu of 5%.
- A focused region around Cu ∼10.4% is included to explore critical composition ranges related to research findings.
- Model performance metrics (MAE, R²) are printed for evaluation on test data.
- This approach can be extended by including additional features or other alloying elements.

***

## Contact

For questions or collaboration, feel free to reach out or open an issue in the repository.

***
