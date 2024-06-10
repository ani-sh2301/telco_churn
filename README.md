# Telco Churn Prediction

## Introduction
In the telecom industry, customer churn refers to the phenomenon where customers leave a service provider for a competitor. Predicting which customers are likely to churn is crucial for telecom companies because retaining existing customers is often more cost-effective than acquiring new ones. <br>
For the telco company to expand its clientele, its number of new customers must exceed its churn rate.<br>
Several factors can influence a customer's decision to leave, such as:
<li><b>Service quality, Pricing, Customer service, Usage patterns.</b></li>
To predict churn, we need to analyze various types of data, like:
<li><b>Customer demographics, Usage patterns, Service interactions, Billing information.</b></li>

The dataset used in this project: Telco Customer Churn<br>
<b>Link:</b> https://www.kaggle.com/datasets/blastchar/telco-customer-churn<br>

The dataset contains 7043 rows and 21 columns<br>
<b>Columns:</b> ['customerID', 'gender', 'SeniorCitizen', 'Partner', 'Dependents',
       'tenure', 'PhoneService', 'MultipleLines', 'InternetService',
       'OnlineSecurity', 'OnlineBackup', 'DeviceProtection', 'TechSupport',
       'StreamingTV', 'StreamingMovies', 'Contract', 'PaperlessBilling',
       'PaymentMethod', 'MonthlyCharges', 'TotalCharges', 'Churn']<br>

## Data Preprocessiong
<ul>
<li>Converted Data Types: The TotalCharges column was initially of type object. I converted it to float type.</li>
<li>Handled Empty Strings: During the conversion, I found empty strings in the TotalCharges column. These were rows where tenure was 0, making TotalCharges equal to 0. I filled these empty spaces with 0.</li>
<li>Checked for Null Values: There were no null values in the dataset.</li>
<li>Removed Duplicates: No duplicate records were found.</li>
<li>Dropped Irrelevant Columns: The CustomerID column was dropped as it was not relevant to predicting churn.</li>
<li>Checked for Outliers: I checked for outliers in the numerical columns tenure, MonthlyCharges, and TotalCharges and found none.</li>
</ul>

## Exploratory Data Analysis
<h4>Techniques Used:</h4>
<ul>
  <li>Univariate analysis</li>
  <li>Bivariate analysis</li>
  <li>Multivariate analysis</li>
  <li>Descriptive statistics and visualizations (pie chart, bar chart, box plot, histograms, pair plot)</li>
</ul>

<h4>Findings:</h4>

<ol>
  <li>
    <b>Univariate Analysis:</b>
    <ul>
      <li>I found that the average tenure was around 32 months.</li>
      <li>The average monthly charges were $64.7.</li>
      <li>The average total charges were $2279.7, with a high standard deviation.</li>
      <li>The churn rate was 26.5%.</li>
      <li>The gender distribution was almost equal between male and female customers.</li>
    </ul>
  </li>

  <li>
    <b>Bivariate Analysis:</b>
    <ul>
      <li>I discovered that the average tenure for customers who churned (churn=yes) was 10 months, compared to 38 months for those who did not churn (churn=no).</li>
      <li>The average monthly charges were higher for customers who churned.</li>
      <li>I identified that customers more likely to leave included those with:
        <ul>
          <li>No partner</li>
          <li>No dependents</li>
          <li>Phone service</li>
          <li>Fiber optic internet</li>
          <li>No online security</li>
          <li>No online backup</li>
          <li>No tech support</li>
          <li>Month-to-month contracts</li>
          <li>Paperless billing</li>
        </ul>
      </li>
    </ul>
  </li>

  <li>
    <b>Multivariate Analysis:</b>
    <ul>
      <li>I found that the number of month-to-month contracts decreased with increasing tenure, while two-year contracts increased.</li>
      <li>With increasing tenure, the likelihood of a customer leaving decreased.</li>
      <li>Total charges were inversely proportional to churn.</li>
      <li>Customers with a tenure of 0-24 months were more likely to leave.</li>
      <li>Customers who paid monthly charges between $51 and $118 were more likely to leave.</li>
      <li>Pair plot analysis revealed correlations between:
        <ul>
          <li>Tenure and total charges</li>
          <li>Monthly charges and total charges</li>
        </ul>
      </li>
    </ul>
  </li>
</ol>

## Feature Engineering
<b>Encoding the Data:</b>
<ul>
  <li>I used label encoding for all categorical columns.</li>
  <li>I applied one-hot encoding to columns with multiple classes (i.e., more than 2).</li>
</ul>

<b>Dropping Unnecessary Columns:</b>
<ul>
  <li>I dropped columns created during EDA that were not required, such as tenure_bin, MonthlyCharges_bin, and TotalCharges_bin.</li>
</ul>

<b>Handling Multicollinearity:</b>
<ul>
  <li>I created a correlation matrix to identify multicollinearity.</li>
  <li>Based on the correlation analysis, I removed highly correlated columns to reduce multicollinearity. The removed columns were:
    <ul>
      <li>tenure</li>
      <li>MonthlyCharges</li>
      <li>InternetService_2</li>
      <li>OnlineSecurity_1</li>
      <li>DeviceProtection_1</li>
      <li>TechSupport_1</li>
      <li>StreamingTV_1</li>
      <li>StreamingMovies_1</li>
    </ul>
  </li>
</ul>

## Model Selection and Training
<b>Data Splitting:</b>
<ul>
  <li>I first split the data into training and testing sets.</li>
</ul>

<b>Model Training:</b>
<ul>
  <li>I trained multiple models, including:
    <ul>
      <li>Logistic Regression</li>
      <li>Gradient Boosting</li>
      <li>Random Forest</li>
    </ul>
  </li>
</ul>

<b>Hyperparameter Tuning:</b>
<ul>
  <li>I performed hyperparameter tuning for each model to optimize their performance.</li>
</ul>
<p>
Comparing these models I found that gradient boosting has the highest accuracy among all.<br>
Logistic regression: 0.8031<br>
Gradient boosting: 0.812<br>
Random Forest: 0.77<br>
These steps provided a comprehensive understanding of each model's performance, helping to identify the best model for predicting customer churn.

</p>

## Model Evaluation
<b>Evaluation Metrics</b>

<ul>
    <li>I evaluated the different models using the following metrics:
        <ul>
            <li>Accuracy</li>
            <li>Precision</li>
            <li>Recall</li>
            <li>F1 Score</li>
        </ul>
    </li>
    <li>I also generated classification reports for each model.</li>
</ul>

<b>Model Comparison</b>

<ul>
    <li>I compared all the models using the evaluation metrics listed above.</li>
    <li>I constructed a performance comparison graph to visually compare the models based on these metrics.</li>
</ul>

## Conclusion
<p>
In conclusion, I found out that a lot of customers, about 26.5%, are thinking of leaving the telecom company. After trying out different methods, I discovered that Gradient Boosting and Logistic Regression are the best at predicting who might leave, with around 81% accuracy. I also learned that factors like how long a customer has been with the company, how much they pay each month, and the type of contract they have can help us predict if they'll leave or not. </p>


