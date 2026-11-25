# Used-car-price-prediction
Machine learning regression project predicting used-car asking prices using data cleaning, exploratory analysis, and Random Forest.
- [Jupyter notebook](used_car_price_prediction.ipynb)
- [Five-slide PowerPoint deck](presentation/used_car_price_prediction.pptx)
- [Dataset instructions and checksum](data/README.md)

## Reproduce the analysis

1. Extract the project archive and open a terminal in the project folder.
2. Keep the included CSV at `data/used_cars_dataset.csv`.
3. Create and activate a Python 3.12 virtual environment.

   Windows PowerShell

   ```powershell
   py -3.12 -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

   macOS or Linux

   ```bash
   python3.12 -m venv .venv
   source .venv/bin/activate
   ```

4. Install dependencies and open the notebook.

   ```bash
   python -m pip install -r requirements.txt
   python -m notebook used_car_price_prediction.ipynb
   ```

5. Select **Run All**. To execute the notebook from the terminal instead, run:

   ```bash
   python -m nbconvert --to notebook --execute --inplace --ExecutePreprocessor.timeout=300 used_car_price_prediction.ipynb
   ```

## Method

Remove exact duplicates, clean structured fields, and recover selected missing details from seller descriptions. Use an 80/20 split with seed 42. Fit the preprocessing and model together on training rows, then report MAE, RMSE and R² on the same test rows for all models.

The target is the advertised price in INR. Estimates for rare and expensive vehicles are less certain, and the existing test design should be followed by validation on newly collected listings.

## Test results

| Model | MAE (INR) | RMSE (INR) | R² |
| --- | ---: | ---: | ---: |
| Random Forest | 259,623 | 910,384 | 0.714 |
| Gradient Boosting | 368,866 | 1,113,206 | 0.573 |
| Median baseline | 678,667 | 1,763,281 | −0.072 |

Random Forest reduced MAE by 62% compared with the baseline. The deck and table use the rebuilt notebook's results.

## Put the project on GitHub

Create an empty repository on GitHub. In this project folder, run the commands below and replace the example remote with your repository URL.

```bash
git init -b main
git add .
git commit -m "Add used-car price prediction capstone"
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

The archive includes the supplied dataset. See the [dataset notes](data/README.md) for its checksum and provenance.
