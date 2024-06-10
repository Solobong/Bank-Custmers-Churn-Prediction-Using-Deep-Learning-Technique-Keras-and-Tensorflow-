# Bank-Custmers-Churn-Prediction-Using-Deep-Learning-Technique-Keras-and-Tensorflow-
Thanks for the additional details. Here's the updated README file incorporating the ensemble methods and other aspects you've described:

---

# Bank Customer Churn Prediction

This project involves predicting customer churn for a bank using a dataset of customer information and transaction details. The goal is to identify customers who are likely to leave the bank and understand the factors influencing their decision.

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Data Preprocessing](#data-preprocessing)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Modeling](#modeling)
- [Results](#results)
- [Handling Imbalanced Data](#handling-imbalanced-data)
- [Ensembling with Undersampling Technique](#ensembling-with-undersampling-technique)
- [Usage](#usage)
- [Installation](#installation)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Introduction
Customer churn prediction is crucial for businesses to retain customers and enhance customer satisfaction. This project uses machine learning techniques to predict customer churn based on a variety of features such as tenure, monthly charges, and service usage.

## Dataset
The dataset contains customer information and details about their tenure, monthly charges, total charges, and whether they have churned or not.

**Columns:**
- `customerID`: Unique identifier for the customer
- `tenure`: Number of months the customer has stayed with the bank
- `MonthlyCharges`: The amount charged to the customer monthly
- `TotalCharges`: The total amount charged to the customer
- `Churn`: Whether the customer has churned (Yes/No)
- Other columns related to services used by the customers (e.g., InternetService, Contract, PaymentMethod)

## Data Preprocessing
- Dropped the `customerID` column
- Converted `TotalCharges` to numeric and handled missing values
- Encoded categorical variables (e.g., replacing 'Yes' and 'No' with 1 and 0)
- Applied one-hot encoding to columns like `InternetService`, `Contract`, and `PaymentMethod`
- Scaled numerical columns (`tenure`, `MonthlyCharges`, `TotalCharges`) using `MinMaxScaler`

## Exploratory Data Analysis
Visualizations were created to understand the distribution of churn with respect to tenure and monthly charges:
- Customers with longer tenure are less likely to churn.
- Monthly charges are higher for customers who churn.

## Modeling
Two models were trained using TensorFlow and Keras:
1. Model with 50 epochs
2. Model with 100 epochs

Both models used a simple neural network architecture:
- Input layer with 20 neurons
- Output layer with 1 neuron (sigmoid activation)

The models were evaluated using accuracy and confusion matrices.

## Results
The models showed similar accuracy for both 50 and 100 epochs, indicating that increasing epochs did not significantly improve performance. The confusion matrix and classification report were used to assess model performance.

## Handling Imbalanced Data
The dataset exhibited an imbalance between the churn and non-churn classes. Various techniques were applied to address this:
1. **Undersampling**: Reduced the number of non-churn samples to match churn samples.
2. **Oversampling**: Increased the number of churn samples to match non-churn samples.
3. **SMOTE (Synthetic Minority Over-sampling Technique)**: Generated synthetic samples to balance the dataset.

The SMOTE technique yielded the best results, with balanced F1-scores for both classes.

## Ensembling with Undersampling Technique
An ensemble method was applied using undersampling:
- Divided the majority class into three batches and trained models on each batch.
- Combined predictions from the three models using a majority vote.

**Steps:**
1. Split the data into training and test sets.
2. Divided the majority class (non-churn) into three batches.
3. Trained separate models on each batch.
4. Combined predictions from all three models using a majority vote.

**Results:**
The F1-scores for individual batches were not impressive, but combining the predictions using majority voting slightly improved the results. However, the SMOTE technique still provided the best overall performance.

## Usage
To use this dataset and model:
1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/bank-customer-churn-prediction.git
    ```
2. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```
3. Run the Jupyter notebook or Python script to see the analysis and model training.

## Installation
Ensure you have Python installed. Then, install the necessary packages using the provided `requirements.txt` file.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
Special thanks to the creators of the dataset and the open-source community for providing the tools and resources used in this project.

---

Feel free to modify this template according to your specific details and preferences.
