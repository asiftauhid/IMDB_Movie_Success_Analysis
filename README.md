# IMDb Movie Success Analysis

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![pandas](https://img.shields.io/badge/pandas-1.5%2B-green.svg)](https://pandas.pydata.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.1%2B-red.svg)](https://scikit-learn.org/)

A comprehensive data science project analyzing factors that contribute to movie success on IMDb, focusing on films with 100-1000 reviews.

## Project Overview

This project investigates **what factors contribute to a popular movie's success on IMDb** by analyzing the relationship between movie ratings and various features including:

- **Director Experience**: Impact of director's filmography on ratings
- **Genre**: How different genres perform differently
- **Runtime**: Effect of movie duration on audience ratings
- **Lead Actor Experience & Popularity**: Influence of star power
- **Actor-Director Collaboration**: Impact of repeated creative partnerships

We deliberately selected films with **100 to 1000 votes** to represent moderately to quite popular titles - visible enough to reflect genuine audience opinion, but not dominated by large fanbases or franchise-driven hype.

## Research Questions & Hypotheses

### Main Research Question
**What factors contribute to a popular movie's success on IMDb that received 100 to 1000 reviews?**

### Hypotheses Tested

1. **Genre Effect**: Movies in certain genres (e.g., Drama, Thriller) receive higher average ratings than others
2. **Runtime Effect**: Longer runtimes tend to correlate with higher ratings (within reasonable bounds)
3. **Director Experience**: More experienced directors produce higher-rated films
4. **Actor Influence**: More experienced and popular lead actors contribute to higher ratings
5. **Collaboration Effect**: Recurring actor-director partnerships produce higher-rated films

## Dataset

This project uses **IMDb's official datasets** (updated regularly):

- `title.basics.tsv.gz` - General movie information (title, runtime, genre)
- `title.ratings.tsv.gz` - User ratings and vote counts
- `title.crew.tsv.gz` - Director and writer information
- `title.principals.tsv.gz` - Cast and crew details

**Dataset Source**: [IMDb Non-Commercial Datasets](https://datasets.imdbws.com/)

### Data Scope
- **Initial dataset**: ~9.6 million titles
- **Filtered to movies**: ~636,768 films
- **After cleaning**: ~371,468 movies with complete information
- **Final analysis set**: Movies with 100-1000 votes

## Technologies & Libraries

### Core Libraries
- **Python 3.8+**
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computations
- **matplotlib** - Data visualization
- **seaborn** - Statistical visualizations

### Statistical Analysis
- **scipy** - Statistical tests (ANOVA, correlation, t-tests)
- **statsmodels** - Post-hoc tests (Tukey HSD), VIF analysis

### Machine Learning
- **scikit-learn** - Regression modeling, train-test split, evaluation metrics

## Prerequisites

### Installation

1. **Clone this repository**
```bash
git clone https://github.com/asiftauhid/IMDB_Movie_Success_Analysis.git
cd IMDB_Movie_Success_Analysis
```

2. **Install required packages**
```bash
pip install -r requirements.txt
```

### Download IMDb Datasets

Download the following files from [IMDb Datasets](https://datasets.imdbws.com/) and place them in a folder called `IMDB_Dataset/`:

- `title.basics.tsv.gz`
- `title.ratings.tsv.gz`
- `title.crew.tsv.gz`
- `title.principals.tsv.gz`

## Usage

### Running the Analysis

1. **Open the Jupyter Notebook**
```bash
jupyter notebook IMDB_Data_Analysis.ipynb
```

2. **Update the data directory path** in the notebook (Cell 8):
```python
data_dir = "/path/to/your/IMDB_Dataset/"
```

3. **Run all cells** to reproduce the complete analysis

### Analysis Pipeline

The notebook follows this structure:

1. **Data Loading & Inspection** - Import IMDb datasets
2. **Data Cleaning** - Filter movies, handle missing values, remove outliers
3. **Exploratory Data Analysis (EDA)** - Visualize distributions and relationships
4. **Feature Engineering** - Create experience metrics, collaboration indicators
5. **Statistical Testing** - ANOVA, correlation tests, post-hoc analysis
6. **Predictive Modeling** - Linear regression and Ridge regression
7. **Results & Interpretation** - Summarize findings

## Key Findings

### 1. Genre Effect 
- **ANOVA Result**: F = 1676.19, p < 0.001 (highly significant)
- Genres like **Biography, Documentary, and Drama** consistently score higher
- **Comedy and Horror** tend to have lower average ratings
- Genre accounts for meaningful variation in audience perception

### 2. Runtime Effect 
- Longer movies (within 30-240 minutes) correlate positively with ratings
- Optimal range appears to be **90-150 minutes**
- Very short (<60 min) and extremely long (>180 min) films tend to score lower

### 3. Director Experience 
- **ANOVA Result**: F = 7.74, p = 3.1 × 10⁻⁶ (highly significant)
- Directors with **10+ films** achieve higher average ratings
- Experience brings improved storytelling, technical skill, and industry trust

### 4. Lead Actor Experience 
- **ANOVA Result**: F = 5.82, p = 0.0001 (significant)
- More experienced actors contribute to higher-rated films
- Star power and performance quality both matter

### 5. Actor-Director Collaboration 
- Repeated collaborations show **higher average ratings**
- Creative chemistry and mutual understanding enhance film quality

### Regression Model Performance
- **Ridge Regression R² (Test)**: ~0.XX (model explains XX% of rating variance)
- **Most important features**: Genre dummies, director experience, runtime interactions
- **RMSE**: ~0.XX rating points (average prediction error)

## Visualizations

The project includes:
- Distribution plots for runtime, ratings, and experience metrics
- Box plots comparing genres and experience categories
- Correlation heatmaps
- Scatter plots with regression lines
- ANOVA and post-hoc test visualizations

## Project Structure

```
imdb-movie-analysis/
│
├── IMDB_Data_Analysis.ipynb    # Main analysis notebook
├── Report.pdf                  # Detailed project report
├── README.md                   # This file
├── requirements.txt            # Python dependencies
├── .gitignore                 # Git ignore rules
│
└── IMDB_Dataset/              # Data folder (not tracked in git)
    ├── title.basics.tsv.gz
    ├── title.ratings.tsv.gz
    ├── title.crew.tsv.gz
    ├── title.principals.tsv.gz
    └── movies_ratings_dirs_actors.csv

NOTE: If the file is not opening in GitHub (since the .ipynb file is huge), please consider downloading it and opening it locally.
