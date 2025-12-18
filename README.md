# Spotify Song Popularity Prediction

## Abstract
We model Spotify song popularity using audio features and metadata from a 114k‑track dataset, applying **LASSO, PCA, CART, Random Forest, and XGBoost** to evaluate which features drive mainstream success. By comparing linear and nonlinear approaches, we find that nonlinear ensemble methods — particularly Random Forest and XGBoost trained on LASSO‑selected features — achieve the strongest predictive performance, significantly improving **ROC‑AUC** and **recall** over the baseline.  
Key drivers of popularity include **loudness, danceability, instrumentalness, duration, and genre**, suggesting that both sonic and stylistic characteristics play meaningful roles. These results demonstrate that machine learning can provide actionable insight for artists, producers, and streaming platforms in anticipating and shaping song popularity.

---

## Project Description and Motivation
This project explores **what drives mainstream musical success** by modeling Spotify song popularity from audio features and metadata.

- **Artists & Producers**: Experiment with song features correlated with popularity to maximize audience appeal.  
- **Streaming Platforms**: Improve recommendation systems by identifying features that drive popularity.  
- **Record Labels**: Allocate marketing resources toward tracks with higher predicted success.  

---

## Dataset and Learning Problem
- **Source**: Spotify Tracks Dataset (Kaggle)  
- **Size**: ~114,000 songs  
- **Columns**:  
  `track_id, artists, album_name, track_name, popularity, duration_ms, explicit, danceability, energy, key, loudness, mode, speechiness, acousticness, instrumentalness, liveness, valence, tempo, time_signature, track_genre`

- **Target Variable**: `popularity` (0–100 scale)  
- **Learning Problem**: Predict whether a song is in the **top 10% popularity** based on features.  

### Challenges
- Duplicate tracks  
- Irrelevant columns (e.g., `track_id`, `album_name`)  
- Encoding categorical features  
- Multicollinearity (e.g., energy vs. loudness vs. danceability)

### Preprocessing
- Drop missing values & duplicates  
- Remove irrelevant columns  
- Encode categorical features (`explicit`, `key`, `mode`, `time_signature`, `track_genre`)  
- Feature selection (LASSO) & transformation (PCA)  

---

## Methodology

### 1. Baseline Model: LASSO Regression
- Simple, interpretable coefficients  
- Identifies positively/negatively correlated features  

### 2. Feature Selection & Transformation
- **LASSO**: Selects important features, reduces noise, mitigates multicollinearity  
- **PCA**: Transforms correlated features into principal components  

### 3. Advanced Models
- **CART**: Simple decision tree, interpretable relationships  
- **Random Forest**: Handles noisy features, stable importance rankings  
- **XGBoost**: Boosting method, strongest predictive performance  

### Evaluation
- Train/Test Accuracy  
- ROC‑AUC  
- Classification Report  
- Confusion Matrix  
- Feature Importances  

## Dashboard
We built an interactive **Dash app** that allows users to:
- Input song feature parameters  
- Generate predicted popularity probabilities   

The dashboard code is included at the bottom of the spotify_code notebook

## How to Run
- Download the spotify_code notebook and spotify_dataset.csv
- Run the code from top to bottom
- Dashboard can be accessed at port 8052 (http://127.0.0.1:8052/)
