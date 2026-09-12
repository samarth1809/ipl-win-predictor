# 🏏 IPL Team Win Prediction

A Google Colab notebook that predicts the winner of an IPL match using machine learning (Logistic Regression & Random Forest).

## Files
- `IPL_Team_Prediction.ipynb` — the main notebook

## How to Run
1. Go to [Google Colab](https://colab.research.google.com/).
2. Click **File → Upload notebook** and select `IPL_Team_Prediction.ipynb`.
3. Run the cells **in order, top to bottom** (or use **Runtime → Run all**).
4. When prompted in Section 2 ("Load Data"), you have two options:
   - **Upload a real dataset**: Download `matches.csv` from Kaggle's *IPL Complete Dataset (2008–2024)* and upload it when asked.
   - **Skip the upload**: Click Cancel on the file dialog, and the notebook will auto-generate synthetic sample data so you can still test the full pipeline.

## What the Notebook Does
1. **Load Data** — real dataset (uploaded) or synthetic sample data.
2. **Clean & Standardize Columns** — maps common column name variants (e.g. `Team1`, `WinningTeam`) to a consistent format.
3. **Feature Engineering** — builds:
   - Head-to-head win rate between the two teams
   - Team's recent form (last 5 matches)
   - Toss winner / toss decision
   - Encoded team and venue identifiers
4. **Train Models** — trains Logistic Regression and Random Forest, and picks the more accurate one.
5. **Evaluate** — prints accuracy, a classification report, a confusion matrix, and (for Random Forest) a feature importance chart.
6. **Predict a Custom Match** — a `predict_winner()` function where you plug in two teams, a venue, toss winner, and toss decision to get a win probability and predicted winner.

## Troubleshooting
| Problem | Fix |
|---|---|
| `from google.colab import files` fails | You must be running on colab.research.google.com, not a local Jupyter server |
| Upload cell hangs | Click Cancel in the file dialog to fall back to synthetic data |
| `KeyError` / missing columns after uploading a real CSV | Edit the `col_map` dictionary in Section 3 to match your CSV's actual column names |
| Low accuracy | Expected with synthetic data — use a real, larger dataset for meaningful results |

## Improving Accuracy
- Add player-level stats (batting/bowling averages, current form)
- Add powerplay/death-over run rates
- Add pitch report and weather conditions
- Try `XGBoost` or `GradientBoostingClassifier`
- Save the trained model with `joblib.dump(best_model, 'ipl_model.pkl')` to reuse it without retraining

## Requirements
Installed automatically in the first cell:
- pandas, numpy, scikit-learn, matplotlib, seaborn
