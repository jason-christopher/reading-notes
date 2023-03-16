# Module 2 - Microsoft Azure AI Fundamentals: Explore visual tools for machine learning

## Create a classification model with Azure Machine Learning designer

Classification is a form of **supervised** machine learning that is used to predict which category, or class, an item belongs to. This machine learning technique can be applied to **binary** and **multi-class** scenarios.

Some examples for classification machine learning models are:

* Using clinical data to predict whether a patient will become sick or not.
* Using historical data to predict whether text sentiment is positive, negative, or neutral.
* Using characteristics of small businesses to predict if a new venture will succeed.

### Understand steps for classification

You can think of the steps to train and evaluate a classification machine learning model as:

1. Prepare data: Identify the features and label in a dataset. Pre-process, or clean and transform, the data as needed.
2. Train model: Split the data into two groups, a training and a validation set. Train a machine learning model using the training data set. Test the machine learning model for performance using the validation data set. You will use designer's **Score Model** component to generate the predicted class label value. Once you connect all the components, you will want to run an experiment, which will use the data asset on the canvas to train and score a model.
3. Evaluate performance: Compare how close the model's predictions are to the known labels. You can review evaluation metrics on the completed job page by right-clicking on the **Evaluate model** component.
    * The **confusion matrix** is a tool used to assess the quality of a classification model's predictions. In a binary classification model where you're predicting one of two possible values, the confusion matrix is a 2x2 grid showing the predicted and actual value counts for classes 1 and 0.
      ![Confusion Matrix](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/confusion-matrix-terms.png)
    * For a **multi-class classification model**, the same approach is used to tabulate each possible combination of actual and predicted value counts - so a model with three possible classes would result in a 3x3 matrix with a diagonal line of cells where the predicted and actual labels match. Metrics that can be derived from the confusion matrix include:
      * **Accuracy**: The number of correct predictions (true positives + true negatives) divided by the total number of predictions.
      * **Precision**: The number of the cases classified as positive that are actually positive: the number of true positives divided by (the number of true positives plus false positives).
      * **Recall**: The fraction of positive cases correctly identified: the number of true positives divided by (the number of true positives plus false negatives).
      * **F1 Score**: An overall metric that essentially combines precision and recall.
    * **Choosing a threshold** - A classification model predicts the probability for each possible class. In the case of a binary classification model, the predicted probability is a value between 0 and 1. Designer has a useful **threshold slider** for reviewing how the model performance would change depending on the set threshold.
      ![Threshold](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/threshold-example.png)
    * **ROC curve** and **AUC metric** - Another term for **recall** is **True positive rate**, and it has a corresponding metric named **False positive rate**, which measures the number of negative cases incorrectly identified as positive compared the number of actual negative cases. Plotting these metrics against each other for every possible threshold value between 0 and 1 results in a curve, known as the **receiver operating characteristic (ROC) curve**. In an ideal model, the curve would go all the way up the left side and across the top, so that it covers the full area of the chart. The larger the **area under the curve (AUC)** (which can be any value from 0 to 1), the better the model is performing. You can review the ROC curve in **Evaluation Results**.
      ![ROC Curve](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-classification-model-azure-machine-learning-designer/media/roc-curve-example.png)
4. Deploy a predictive service: After you train a machine learning model, you need to convert the training pipeline into a real-time **inference pipeline**. The inference pipeline performs the same data transformations as the first pipeline for new data. Then it uses the trained model to **infer**, or predict, label values based on its features. This model will form the basis for a predictive service that you can publish for applications to use. After creating the inference pipeline, you can deploy it as an endpoint. In the endpoints page, you can view deployment details, test your pipeline service with sample data, and find credentials to connect your pipeline service to a client application. The Deployment state on the **Details** tab will indicate **Healthy** when deployment is successful. On the **Test** tab, you can test your deployed service with sample data in a JSON format to test the service before connecting it to an application. You can find credentials for your service on the **Consume** tab. These credentials are used to connect your trained machine learning model as a service to a client application.

***

### Summary

In this module, you learned how to:

* Identify classification machine learning scenarios.
* Use Azure Machine Learning designer to train a classification model.
* Use a classification model for inferencing.
* Deploy and test a classification model.

Source: Source: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/create-classification-model-azure-machine-learning-designer/)
