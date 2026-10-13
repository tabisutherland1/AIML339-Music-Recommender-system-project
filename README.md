# Music Recommender System: Content-Based, Collaborative Filtering and Hybrid Methods

## Project Overview

This project looks into whether combining content-based and collaborative filtering improves music recommendation accuracy and diversity.

Three recommendation approaches are implemented and compared:

1. **Content-based filtering:** Recommends songs using cosine similarity between audio-feature vectors and a user's listening profile.
2. **Collaborative filtering:** Uses implicit-feedback Alternating Least Squares (ALS) to learn preferences from user–song listening interactions.
3. **Hybrid recommendation:** Uses logistic regression to combine the two recommendation scores, user listening-history size and an interaction between history size and the collaborative-filtering score.

The models are compared using Precision@10, Recall@10, nDCG@10 and intra-list diversity.

## Dataset

The project uses the Million Song Dataset and the Taste Profile subset.

- `Content_features.csv`: Extracted musical features for the 10,000-song subset, including tempo, loudness, duration, key, mode, time signature, pitch and timbre statistics.
- `interactions.csv`: User–song listening interactions associated with the subset.
- `train_triplets.txt.gz`: Compressed Taste Profile listening-history data used for collaborative filtering.
- `track_metadata.db`: Original Million Song Dataset metadata database, used to retrieve song titles, artists and identifiers. 

The large Taste Profile file is stored using Git LFS.

**Note:** The original Taste Profile data is larger than the content-feature subset. The final comparison is restricted to songs represented in both model catalogues.

## Installation

Clone the repository:

```bash
git lfs install
git clone https://github.com/tabisutherland1/AIML339-Music-Recommender-system-project.git
cd AIML339-Music-Recommender-system-project
git lfs pull
```

Install the required Python packages:

```bash
pip install numpy pandas matplotlib scikit-learn scipy implicit jupyter
```

Python 3.11.8 is required


## Running the Project

1. Ensure all required datasets are available at the paths expected by the notebook.
2. Open `code.ipynb` in Jupyter Notebook or VS Code.
3. Select the Python environment containing the required packages.
4. Run the setup and preprocessing cells.
5. Train the content-based and collaborative filtering models.
6. Train the hybrid model using validation interactions.
7. Execute the evaluation and visualisation cells.


## Experimental Configuration

The experiment uses a per-user training, validation and test split, with validation data used to train the hybrid fusion classifier.

The final experimental configuration, including the number of users, catalogue size, ALS hyperparameters and random seeds, is described in the accompanying report.

## Results

The draft experimental results indicate that collaborative filtering substantially outperforms content-based filtering, while the hybrid model performs similarly to collaborative filtering without a significant improvement.

These findings apply to the evaluated dataset, models and candidate-song catalogue.

**Note:** The final numerical results should be updated after the evaluation pipeline is verified.

## Limitations

The experiment is subject to several limitations:

- The shared catalogue is substantially smaller than the original Million Song Dataset.
- Content-based recommendations use precomputed audio features without genre or semantic tags.
- Listening-history data consists of implicit feedback rather than explicit ratings.
- The dataset does not represent recently released music.
- Evaluation uses offline historical interactions rather than feedback from actual listeners.
- Computational resources limit the size and number of experiments.

## Reproducibility

Random seeds, data splitting and model hyperparameters should be fixed and documented. The notebook should be executed from top to bottom in a clean Python environment.

Dataset files, dependencies and any additional metadata needed for execution must be obtained according to their respective usage and licensing conditions.


## Author

Tabi Sutherland

AIML339 — Victoria University of Wellington

300668009