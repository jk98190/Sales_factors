Online Shopping Behaviour and Sales Analysis
Project Overview
This project uses Python to analyze two e-commerce datasets and identify patterns in online purchase behaviour, retail sales, and customer purchasing activity.

It combines descriptive statistics, data visualization, correlation analysis, machine learning, feature selection, regression, and customer clustering to produce insights that can support data-driven marketing and business decisions.
Objectives
- Summarize numerical data using mean, median, mode, and descriptive statistics.
- Inspect missing values and duplicate records.
- Visualize purchase outcomes, numerical distributions, sales trends, and top-selling products.
- Identify variables associated with online purchase conversion.
- Train a machine-learning model to classify sessions as purchase or no purchase.
- Rank and select important features using model-based feature selection and mutual information.
- Analyze monthly retail sales and product performance.
- Use regression to estimate transaction-line sales.
- Segment customers using K-Means clustering and customer-level purchasing features.
Datasets
1. online_shoppers_intention.csv
Contains website-session information, including page visits, time spent on pages, bounce and exit rates, visitor type, month, and the Revenue outcome.

Target variable: Revenue

Revenue is a Boolean outcome indicating whether a session resulted in a purchase. It is not the monetary amount of revenue.
2. online_shoppers_cleaned.csv
Contains retail transaction-line data, including invoice number, product code, product description, quantity, invoice date, unit price, customer ID, and country.

The script calculates transaction-line sales as:

Sales = Quantity × UnitPrice

Cancellations and lines with non-positive quantity or unit price are excluded from the positive-sales analysis. This is an analytical filter, not a full accounting reconciliation.
Tools and Libraries
- Pandas: data loading, cleaning checks, grouping, and summaries
- NumPy: numerical operations
- Matplotlib: charts and plots
- Seaborn: statistical visualizations
- Scikit-learn: classification, regression, feature selection, preprocessing, scaling, and clustering
Analysis Workflow
1. Load both CSV files.
2. Review dataset dimensions, missing values, duplicate records, and descriptive statistics.
3. Calculate retail transaction sales.
4. Visualize purchase outcomes, distributions, and correlations.
5. Train a Random Forest classifier to predict purchase conversion.
6. Evaluate the classifier using precision, recall, F1-score, and ROC-AUC.
7. Rank features by Random Forest importance and mutual information.
8. Plot monthly sales and identify top-selling products.
9. Fit a Random Forest regression model to transaction-line sales.
10. Create customer-level features and segment customers using K-Means.
11. Export selected results to CSV files.
Setup and Execution
1. Install the required packages
pip install pandas numpy matplotlib seaborn scikit-learn
2. Check the input file paths
The script currently uses these paths:
online_shoppers_cleaned = pd.read_csv(
    "/Users/jahaankachwala/Downloads/Projects /Online Retail/online_shoppers_cleaned.csv"
)

online_shoppers_intention = pd.read_csv(
    "/Users/jahaankachwala/Downloads/Projects /Online Retail/online_shoppers_intention.csv"
)
Confirm that the folder name and file paths match your Mac exactly. If you move the files, update these paths.
3. Run the script
Run online_shopping_analysis_simple.py in a Python environment such as Jupyter Notebook, VS Code, or a terminal.
Output Files
The script saves these CSV files in the current working directory:
- purchase_feature_importance.csv — model-ranked purchase-intent features
- purchase_mutual_information.csv — features ranked by mutual information
- monthly_sales.csv — total positive sales by month
- customer_clusters.csv — customer-level features and assigned cluster
Charts are displayed during execution.
Important Interpretation Notes
- Association is not causation. Correlation and feature importance identify patterns in the available data; they do not prove that changing a variable will increase sales.
- Purchase conversion is imbalanced. Only a minority of sessions result in purchases. Review precision, recall, and F1-score rather than relying only on accuracy.
- PageValues may be a late-funnel signal. Its predictive power should be tested in a separate model that excludes it if the goal is to identify purchase intent early in a session.
- Sales regression is partly arithmetic. Since transaction sales are calculated from quantity multiplied by unit price, those variables are expected to dominate predictions. This model is not a causal analysis of sales drivers.
- Retail sales are not necessarily net revenue. Returns, cancellation handling, taxes, shipping, and accounting rules should be reviewed before using these totals for financial reporting.
- Clustering is exploratory. Customer segments should be checked for stability and business usefulness before using them to target campaigns.
- Outliers matter. Large quantities or transaction values may represent valid bulk purchases or data issues and should be investigated rather than automatically deleted.
Business Applications
Potential applications include:
- Identifying sessions with characteristics associated with purchase conversion
- Prioritizing website journey improvements for testing
- Comparing product and monthly sales performance
- Finding high-value, frequent customers and customers who may need reactivation
- Supporting marketing segmentation and campaign planning
Suggested Future Improvements
- Compare purchase models with and without PageValues.
- Tune the classification threshold based on the business cost of missed purchases and false alarms.
- Use time-based validation for sales forecasting.
- Test log-transformed or robust regression approaches to reduce the influence of extreme sales values.
- Evaluate customer clusters over time and validate them against campaign outcomes.
- Use A/B tests to measure whether website or marketing changes cause incremental conversions.
Author
Add your name, course, institution, and project date here if this README is being used for a portfolio or academic submission.
