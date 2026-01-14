# Tour Revenue Optimization - ML Project README

## Project Overview

This project is a **machine learning regression task** focused on predicting **Crowd Energy** levels for concert tour performances. The objective was to build a predictive model that could forecast crowd energy based on various performance and environmental factors, with potential applications in revenue optimization and event planning.

## Dataset

The project uses two main CSV files:

- **tour_logs_train.csv** - Training dataset with ~1950 concert gig records
- **tour_logs_test_input.csv** - Test dataset with ~500 gig records (without target labels)

### Features in the Dataset

| Feature                 | Description                                                      |
| ----------------------- | ---------------------------------------------------------------- |
| `Gig_ID`                | Unique identifier for each performance                           |
| `Venue_ID`              | Concert venue identifier (V_Alpha, V_Beta, V_Gamma, V_Delta)     |
| `Show_DateTime`         | Date and time of the performance                                 |
| `Day_of_Week`           | Day of week (0-6)                                                |
| `Volume_Level`          | Speaker volume (1-11, with data quality issues)                  |
| `Ticket_Price`          | Price per ticket (with currency symbols and formatting issues)   |
| `Crowd_Size`            | Number of attendees                                              |
| `Opener_Rating`         | Rating of the opening act (1-5)                                  |
| `Weather`               | Weather conditions (Clear, Cloudy, Rainy, Stormy)                |
| `Moon_Phase`            | Lunar phase (New Moon, Waxing Crescent, etc.)                    |
| `Band_Outfit`           | Costume type (Denim, Leather, Spandex, Velvet)                   |
| `Merch_Sales_Post_Show` | **TARGET**: Post-show merchandise sales (proxy for crowd energy) |

## Key Challenges & Data Quality Issues

The dataset contained multiple data quality problems that required extensive cleaning:

1. **Date Format Inconsistencies**

   - Multiple date formats: `2024-03-06 19:00:00`, `19/04/2024 06:00 PM`, `August 16, 2024`, `Morning`, `Evening`, `Late Night`
   - Required pattern detection and standardization

2. **Ticket Price Formatting**

   - Currency symbols: `$`, `£`, `€`
   - Variations: `Free`, `$43.35 (VIP: $65.03)`, `75.86 USD`
   - Numerical extraction needed

3. **Volume Level Anomalies**

   - Valid range: 1-11 (per singer's notes)
   - Invalid values (0, negative, >11) replaced with median value (11)

4. **Missing Values**

   - Multiple columns with NaN values
   - Required appropriate imputation strategies

5. **Crowd Size Outliers**
   - Some zero values that needed investigation

## Data Cleaning & Preprocessing Steps

### 1. Date Standardization

- Identified patterns using regex and converted all dates to consistent format
- Handled various date formats with pattern detection algorithm

### 2. Ticket Price Cleaning

- Removed currency symbols
- Extracted numeric values from complex formats
- Converted all to float

### 3. Volume Level Validation

- Replaced values outside [1-11] range with median (11)
- Applied as per domain expert notes

### 4. Feature Engineering

Extracted temporal features from `Show_DateTime`:

- `Hour` - Hour of day
- `Month` - Month number
- `Day_of_Month` - Day of month

### 5. Categorical Encoding

- One-hot encoded categorical variables: `Venue_ID`, `Weather`, `Moon_Phase`, `Band_Outfit`

## Libraries & Technologies Used

### Core Data Science Stack

- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computing
- **matplotlib & seaborn** - Data visualization

### Machine Learning

- **scikit-learn**
  - `RandomForestRegressor` - Main predictive model
  - `LinearRegression` - Baseline model
  - `train_test_split` - Dataset splitting
  - `GridSearchCV` - Hyperparameter tuning
  - `mean_squared_error`, `r2_score` - Model evaluation metrics

### Utilities

- **re** - Regular expressions for pattern matching in dates

## Model Development

### Approach

1. **Baseline Model**: Linear Regression
2. **Main Model**: Random Forest Regressor
3. **Optimization**: GridSearchCV for hyperparameter tuning

### Hyperparameters Tuned

- Number of trees (`n_estimators`)
- Tree depth (`max_depth`)
- Minimum samples to split (`min_samples_split`)
- Minimum samples per leaf (`min_samples_leaf`)
- Features per split (`max_features`)

### Model Performance

- **RMSE**: ~14 (approximately 14% average prediction variance)
- **R² Score**: Indicates good model fit
- Test predictions saved in predictions(actual).csv

## Key Findings & Insights

From the comprehensive analysis:

1. **Venue Impact** - Different venues show different crowd energy patterns
2. **Day of Week Effect** - Tuesday potentially shows lower crowd energy
3. **Volume Limit Impact** - Some venues have noise restrictions affecting crowd response
4. **Crowd Size Correlation** - Excessive crowd size may negatively impact energy
5. **Time of Day** - Night-time shows tend to have higher crowd energy potential
6. **Weather Influence** - Weather conditions affect crowd engagement

## Project Structure

```
.
├── tour_logs_train.csv              # Training data
├── tour_logs_test_input.csv         # Test data (unlabeled)
├── predictions(actual).csv          # Model predictions on test set
├── analysis_nodebook(final).ipynb   # Complete analysis & model development
├── findings_report.md               # Detailed findings
├── revenue_optimisation.md          # Revenue insights
├── README.md                        # This file
├── MlTaskLibraries/                 # Python virtual environment
└── .gitignore
```

## How to Run

1. **Install dependencies**:

   ```bash
   pip install pandas numpy matplotlib scikit-learn jupyter
   ```

2. **Open the notebook**:

   ```bash
   jupyter notebook analysis_nodebook(final).ipynb
   ```

3. **Run cells sequentially** to:
   - Load and clean data
   - Perform exploratory analysis
   - Train models
   - Generate predictions

## Output Files

- **predictions(actual).csv** - Model predictions for test dataset
- **findings_report.md** - Detailed analysis findings
- **revenue_optimisation.md** - Business recommendations

## Learning Outcomes

Through this project, I learned:

✅ **Data Cleaning & Preprocessing**

- Handling messy, real-world data
- Pattern detection using regex
- Missing value imputation strategies

✅ **Exploratory Data Analysis**

- Statistical analysis and visualization
- Correlation analysis
- Outlier detection

✅ **Machine Learning Workflow**

- Feature engineering and encoding
- Train-test splitting and validation
- Hyperparameter optimization using GridSearchCV

✅ **Random Forest Models**

- Tree-based ensemble methods
- Handling non-linear relationships
- Feature importance analysis

✅ **Model Evaluation**

- Regression metrics (RMSE, R², MAE)
- Cross-validation techniques

✅ **Business Application**

- Translating ML predictions to business insights
- Revenue optimization strategies

---

**Project Status**: ✅ Complete  
**Last Updated**: January 2026  
**Author**: Data Science Practitioner
