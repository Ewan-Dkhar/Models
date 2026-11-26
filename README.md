# Core ML Models — visual lecture + runnable examples

A short, junior-friendly introduction to the classic supervised and unsupervised ML models:
linear/polynomial regression, Ridge/Lasso, logistic regression, k-NN, Naive Bayes, SVMs,
decision trees, random forests, GBDTs, K-Means, DBSCAN, and PCA.

## What is in this repo

| File | Use |
| --- | --- |
| `index.html` | Interactive 22-slide deck. Open it in a browser; arrow keys / space navigate, `N` toggles notes, `F` toggles fullscreen. No build step. |
| `ml_models_lecture.pptx` | Editable source of the static slide deck. |
| `ml_models_lecture.pdf` | Static handout, exported from the PPTX. |
| `ml_models_examples.ipynb` | 10 runnable toy-dataset examples matching slides 5–20. |
| `assets/` | Diagrams used by the HTML and PPTX decks. |
| `preview/` | PNG snapshots of the 22 slides. |

## Suggested teaching flow

1. Present from `index.html` (or the PDF), one section at a time.
2. After each section, open the matching notebook section and change one hyperparameter
   (`degree`, `alpha`, `k`, `max_depth`, `eps`) to see what happens.
3. Use the final cheat-sheet slide (21) to recap when to reach for each model.

## Running the notebook

Works in local Jupyter, Google Colab, or Kaggle. No external data files are needed — all
examples use Scikit-Learn's built-in toy datasets.

```bash
pip install -U "scikit-learn>=1.4" matplotlib xgboost
jupyter notebook ml_models_examples.ipynb
```

The version floor matters: `root_mean_squared_error` needs scikit-learn >= 1.4 and
`KMeans(n_init="auto")` needs >= 1.2. `xgboost` is optional — that cell reports a friendly
message if it is missing. Run the cells top to bottom; later examples reuse variables from
earlier ones. `k`, `alpha`, and `max_depth` are chosen for demonstration, not tuned — tune
them on a validation split or cross-validation and keep the test set for the final check.

## Maintenance notes

- The diagrams and both slide decks were generated as artifacts; the generator scripts are
  not included in this repo. Edit `index.html` and `ml_models_lecture.pptx` directly.
- After editing the PPTX, regenerate the PDF with:
  `libreoffice --headless --convert-to pdf --outdir . ml_models_lecture.pptx`
- `preview/` images are snapshots; re-capture them if the deck's layout changes.
- Keep the HTML, PPTX, and notebook copy in sync when correcting an explanation.
