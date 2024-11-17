Performance Analysis of Deep Learning Models for Alphabet Soup
Overview of the Analysis
The nonprofit foundation Alphabet Soup seeks to develop a predictive tool to identify applicants most likely to succeed with funding. Using machine learning and neural networks, we aim to create a binary classification model that leverages historical funding data to predict successful applicants. The dataset contains over 34,000 rows of metadata, with features like application type, organization classification, funding amount, and success indicators.

Results
Data Preprocessing
     (*)  Target Variable:
         IS_SUCCESSFUL – A binary variable indicating if funding was effectively utilized.

     * Features:
       Depending on the model, features included:

        * Application metadata (e.g., APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, INCOME_AMT).
        * Specific columns like EIN and NAME (Model 3 included these).
        * One-hot encoded categorical variables.
     * Variables Removed:

        * In Model 1, EIN and NAME were removed as they are identifiers without predictive value.
        * In Model 2, STATUS and SPECIAL_CONSIDERATIONS were also dropped in addition to EIN and NAME, making four columns removed in total.
        * In Model 3, EIN and NAME were added back, but STATUS and SPECIAL_CONSIDERATIONS were dropped instead.
Compiling, Training, and Evaluating the Model
Model 1
     * Configuration:

        * Features: Dropped EIN and NAME.
        * Cutoff Values: APPLICATION_TYPE (600), CLASSIFICATION (300).
        * Random State: 78.
        * Architecture: Two hidden layers with 8 and 12 neurons (activation: ReLU), output layer using sigmoid.
        * Training Details: Default data split, 100 epochs.
     * Performance:

        * Accuracy: 72%
        * Loss: 0.552
Model 2
     * Configuration:

        * Features: Dropped EIN, NAME, STATUS, and SPECIAL_CONSIDERATIONS.
        * Cutoff Values: APPLICATION_TYPE (600), CLASSIFICATION (800).
        * Architecture: Three hidden layers with 8, 12, and 10 neurons (activation: ReLU), output layer using sigmoid.
        * Training Details: Default data split, 100 epochs.
     * Performance:

        * Accuracy: 72.6%
        * Loss: 0.552
Model 3
     * Configuration:

        * Features: Retained EIN and NAME, dropped STATUS and SPECIAL_CONSIDERATIONS.
        * Cutoff Values: APPLICATION_TYPE (800), CLASSIFICATION (1000).
        * Random State: 15.
        * Architecture: Three hidden layers with 8, 5, and 9 neurons (activation: Sigmoid), output layer using sigmoid.
        * Training Details: Adjusted data split to 40%/60%, batch size of 64, 100 epochs.
     * Performance:

        * Accuracy: 80%
        * Loss: 0.443
Steps Taken to Increase Model Performance
   1. Adjusted the feature set by dropping or including key columns (EIN, NAME, STATUS, and SPECIAL_CONSIDERATIONS) to optimize information relevance.
   2. Increased cutoff thresholds for categorical variables like APPLICATION_TYPE and CLASSIFICATION to reduce noise.
   3. Changed activation functions to sigmoid for improved output layer behavior.
   4. Altered random states and batch sizes to enhance model generalization and training efficiency.
   5. Incorporated additional hidden layers and tweaked neuron counts to capture complex patterns.
Summary
     * Overall Results:
          The third model demonstrated the highest accuracy (80%) and lowest loss (0.443), outperforming the first two models. By refining the feature set and model architecture, significant improvements were achieved.

     * Recommendation:
          A Random Forest Classifier or Gradient Boosted Decision Trees could be explored as alternative models. These methods excel in binary classification and can handle categorical and numerical data effectively without extensive
          preprocessing. Their ability to capture nonlinear relationships might improve performance further, especially with feature importance metrics guiding feature selection.





