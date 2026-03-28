# F78DS Coursework 2 Review Feedback (H00479060)

## Overall judgement
Your notebook is already **good and close to a strong submission**. It has clear sectioning, interpretation-heavy markdown, and an evidence-based modelling flow from baseline DT to tuned DT with QWK improvement.

## What is already strong
- Clear report structure from introduction → EDA → modelling → evaluation → conclusion.
- You explicitly frame the task as **multi-class** and discuss labelled supervised learning.
- You used stratified train/test split (`stratify=y`) with reproducible seed.
- You evaluated with confusion matrix + **Quadratic Weighted Kappa**.
- You performed basic hyperparameter search (tree depth) and selected the best setting based on QWK.
- You included model limitations and realistic future-work discussion.

## Gaps / risks to improve before final submission

### 1) Reproducibility risk: file paths
Your code reads from `data/F78DS-Essay-Features.csv` and `data/F78DS-Essay-Features-Submission.csv`. If your marker runs the notebook in a folder where files are in project root, this can fail.

**Action**: either place data under `data/` in final submission package, or change code to robust path handling (e.g., `Path` checks/fallback).

### 2) Requirement coverage can be made more explicit
Although you mention key concepts, you should make them easy for markers to tick off quickly:
- Add one short subsection explicitly titled: **“Binary vs Multi-class Classification (for this task)”**.
- Add one short subsection explicitly titled: **“Do we need normalisation for Decision Trees?”** and explain that tree splits are mostly scale-invariant (and justify your decision).
- Add one short subsection on **QWK formula intuition** (observed agreement vs expected agreement with quadratic penalty).

### 3) Evaluation depth can be stronger
You already report QWK, but you can score higher on insight by adding:
- Classification report per class (precision/recall/F1).
- Macro/weighted F1 to highlight class imbalance effects.
- Brief “error pattern” interpretation from confusion matrix (which neighbouring scores are often confused and why).

### 4) Feature engineering / selection discussion can be tightened
You discuss correlations and feature importance. Improve rigour by adding:
- A short leakage/identifier statement: why `essayid` is excluded.
- One small ablation check: compare QWK with all features vs reduced feature set.
- A note about collinearity among length-based features (`chars`, `words`, `stemmed`, `unstemmed`) and why DT may still use one dominant split.

### 5) Kaggle submission evidence
You mention Kaggle score in writing; include concrete evidence for marking convenience:
- Add a small markdown table: model name, local validation QWK, Kaggle public QWK, submission date/time.
- Include the final CSV preview (`head`) and explicit statement: “200 lines total including header (199 predictions)”.

## Suggested “high-mark” narrative improvements (what teachers like)
- Move from “what I did” to **“why this method is appropriate for this dataset and metric”**.
- Add 2–3 concise “insight statements” after each figure/table.
- Connect imbalance → confusion matrix behaviour → metric choice (QWK) in one coherent story.
- In conclusion, include one sentence on practical impact: “If deployed, model should be monitored for minority-score fairness.”

## Fast upgrade checklist (30–45 mins)
1. Add three micro-sections (Binary vs Multi-class; Normalisation decision; QWK intuition).
2. Add classification report and macro/weighted F1.
3. Add Kaggle evidence table + CSV shape confirmation.
4. Add one ablation experiment (with/without selected features).
5. Ensure paths are robust and notebook runs top-to-bottom without manual fixes.

## Final verdict
If submitted as-is, this looks like a **solid pass / potentially good merit-level quality** depending on your rubric weighting. If you implement the fast-upgrade checklist, your report will look much more “distinction-style”: clearer argumentation, stronger methodological justification, and more convincing independent insight.
