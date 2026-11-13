# Assignment-3-SLCM-Classification-Analysis
Course: CS-430-01 Machine Learning Student: Hana Abdelaal

Goal

Can household and housing information help identify households with $3,000 or more in past-due rent? This project builds the target high_arrears (1 if past_due_rent is at least $3,000, otherwise 0) and compares five classification models on the same prepared data.

Files:
Assignment3_SLCM_Classification.ipynb: the completed notebook, with the numbered questions, code, interpretations, and visible outputs.
SLCM_rent_arrears_student_clean.csv: the provided de-identified dataset (same dataset as Assignment 2).
README.md: this file.
Data:
The dataset has 1,754 households and 14 columns. About 69% of households are in class 0 (under $3,000 past due) and about 31% are in class 1 ($3,000 or more). record_id and past_due_rent were not used as model inputs (past_due_rent is used only to create the target, and using it as an input would leak the answer).
Method:
One 80/20 train/test split (test_size=0.20, random_state=42, stratify=y), giving 1,403 training and 351 test households.
One shared preprocessing pipeline: median imputation and StandardScaler for numeric columns; most-frequent imputation and OneHotEncoder(handle_unknown="ignore") for categorical columns.
Five models: Logistic Regression, KNN, Decision Tree, Random Forest, and SVC, each in a pipeline with the same preprocessor.
Evaluation: test accuracy, recall, and F1 for class 1, plus a confusion matrix for the model with the highest F1.
Tuning: GridSearchCV (cv=3, scoring="f1") on the training set only, for KNN (n_neighbors = 3, 5, 7) and Random Forest (max_depth = 3, 5, None).
Main results
KNN had the best test F1 (0.423) and the best recall (0.376). It found 41 of the 109 high-arrears households in the test set and missed 68.
All five models had accuracy of roughly 0.68 to 0.71, close to the 0.69 you would get by always predicting class 0, so accuracy alone was not a useful way to compare them.
GridSearchCV: KNN's best cross-validation F1 was 0.4855 (n_neighbors=7) and Random Forest's was 0.4575 (max_depth=None).
How to run
Open the notebook in Google Colab.
Upload SLCM_rent_arrears_student_clean.csv to the Colab session (folder icon, left side).
Make sure the file name in the first code cell (pd.read_csv(...)) matches the uploaded file.
Choose Runtime > Run all.
Responsible use and AI disclosure
I used Claude (an AI assistant) to explain concepts, help debug and check code, and help polish the wording of some written answers. I reviewed the work and I understand the results, and the interpretations reflect my own understanding.



