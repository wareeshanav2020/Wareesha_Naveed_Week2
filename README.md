\# Hotel Booking Cancellation Prediction



\## Project Overview



This project uses machine learning to predict whether a hotel booking will be cancelled.



The target variable is `is\_canceled`.



Three classification models were evaluated:



\- Logistic Regression

\- Decision Tree

\- Random Forest



The Decision Tree was selected as the final model based on its overall balance of Accuracy, Recall, and F1 Score.



\### Final Model Performance



\- Accuracy: 81.49%

\- Precision: 70.90%

\- Recall: 55.38%

\- F1 Score: 62.19%

\- ROC AUC: 86.86%



\## Project Files



\- `Hotel\_Booking\_Cancellation\_Prediction\_Analysis.ipynb` — Main analysis notebook

\- `hotel\_booking\_modeling\_dataset.csv` — Final dataset used for modeling

\- `hotel\_model\_comparison.csv` — Model performance comparison

\- `hotel\_model\_comparison\_report.pdf` — Model performance comparison - technical report

\- `hotel\_cancellation\_decision\_tree.pkl` — Saved final Decision Tree pipeline

\- `README.md` — Project documentation



\## Requirements



Python 3.x with the following libraries:



\- pandas

\- numpy

\- scikit-learn

\- matplotlib

\- seaborn

\- joblib



\## Run Instructions



\### 1. Open the Notebook



Open:



`Hotel\_Booking\_Cancellation\_Prediction\_Analysis.ipynb`



The notebook can be run in Google Colab or Jupyter Notebook.



\### 2. Upload the Dataset



Upload:



`hotel\_booking\_modeling\_dataset.csv`



to the notebook environment if required.



\### 3. Run the Notebook



Run the notebook cells from top to bottom to reproduce the analysis, model training, evaluation, and comparison.



\### 4. Load the Saved Model



The trained Decision Tree pipeline is available as:



`hotel\_cancellation\_decision\_tree.pkl`



It can be loaded using `joblib` for future predictions.



\## Final Model



The selected model is a Decision Tree classifier.



It is intended as a decision-support prototype and should be further validated using real-world and future booking data before production deployment.

