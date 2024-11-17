# BLENDED_LEARNING
# Implementation of Decision Tree Model for Tumor Classification

## AIM:
To implement and evaluate a Decision Tree model to classify tumors as benign or malignant using a dataset of lab test results.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Load Data: Import the dataset using pandas and load the tumor data from the given file path.
2.Check for Missing Values: Check if there are any missing values in the dataset using isnull().sum().
3.Handle Missing Values: If there are any missing values, remove them using dropna().
4.Separate Features and Target Variable: 
       Separate the feature variables X (all columns except 'Class').
       Set the target variable y as the 'Class' column.
5.Split Data: Divide the dataset into training (80%) and testing (20%) sets using train_test_split().
6.Initialize Decision Tree Classifier: Initialize the DecisionTreeClassifier model with a fixed random state.
7.Train the Model: Fit the DecisionTreeClassifier model on the training data.
8.Make Predictions: Use the trained model to predict on the test data.
9.Evaluate the Model:
      Confusion Matrix: Calculate and print the confusion matrix.
      Classification Report: Print the classification report with precision, recall, and f1-score.
      Accuracy Score: Print the accuracy of the model on the test data.
10.Visualize the Confusion Matrix: Create a heatmap using seaborn to visualize the confusion matrix with appropriate labels for "Benign" and "Malignant" classes.
11.Display Decision Tree Rules: Print out the decision tree rules using export_text() to show the classification logic.
12.Visualize the Decision Tree: Plot the decision tree using plot_tree() to visually represent how the decision-making process works.
## Program:
```
/*
Program to  implement a Decision Tree model for tumor classification.
Developed by: DURGADEVI P
RegisterNumber:  212223100006
*/

import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier, plot_tree, export_text
from sklearn.metrics import classification_report, confusion_matrix, accuracy_score
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
file_path = r"C:\Users\admin\Downloads\tumor.csv"  # Replace with your file path if necessary
data = pd.read_csv(file_path)

# Check for missing values
print("Checking for missing values...")
print(data.isnull().sum())

# Handle missing values (if any exist)
if data.isnull().values.any():
    data = data.dropna()

# Separate features and target variable
X = data.drop('Class', axis=1)
y = data['Class']

# Split dataset into training and testing sets (80% train, 20% test)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Initialize Decision Tree Classifier
clf = DecisionTreeClassifier(random_state=42)

# Train the model
clf.fit(X_train, y_train)

# Predict on the test set
y_pred = clf.predict(X_test)

# Evaluate the model
print("\nConfusion Matrix:")
cm = confusion_matrix(y_test, y_pred)
print(cm)

print("\nClassification Report:")
print(classification_report(y_test, y_pred))

print("\nAccuracy Score:")
print(accuracy_score(y_test, y_pred))

# Visualize the Confusion Matrix
plt.figure(figsize=(8, 6))
sns.heatmap(cm, annot=True, fmt="d", cmap="Blues", xticklabels=["Benign", "Malignant"], yticklabels=["Benign", "Malignant"])
plt.title("Confusion Matrix")
plt.xlabel("Predicted Labels")
plt.ylabel("True Labels")
plt.show()

# Display the decision tree rules
tree_rules = export_text(clf, feature_names=list(X.columns))
print("\nDecision Tree Rules:")
print(tree_rules)

# Visualize the Decision Tree
plt.figure(figsize=(20, 10))  # Adjust figure size as needed
plot_tree(clf, feature_names=X.columns, class_names=["Benign", "Malignant"], filled=True)
plt.title("Decision Tree Visualization")
plt.show()
```

## Output:
![simple linear regression model for predicting the marks scored](sam.png)
![386868961-fe1ae58b-adda-4852-8687-a719c02b269c](https://github.com/user-attachments/assets/d001e75a-4164-473b-b099-6f7db0bcaaa4)
![386868969-b5f70b4b-4551-462d-a486-d9434d25257e](https://github.com/user-attachments/assets/95b9bc6d-0ce6-4653-aa45-e50105198a43)
![386868980-05d084b9-0835-4766-816d-432a9217fdb5](https://github.com/user-attachments/assets/42678b99-2f81-4472-bc00-7fb1029254e5)
![386868998-d1dca6b3-62bc-4a0e-bbb4-3aa8a9f5ae2c](https://github.com/user-attachments/assets/6a6da79f-3615-444c-8349-32c6b5f25b4d)


## Result:
Thus, the Decision Tree model was successfully implemented to classify tumors as benign or malignant, and the model’s performance was evaluated.
