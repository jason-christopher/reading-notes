# Module 2 - Microsoft Azure AI Fundamentals: Explore visual tools for machine learning

## Create a regression model with Azure Machine Learning designer

Regression is an example of a **supervised** machine learning technique in which you train a model using data that includes both the **features** and known values for the **label**, so that the model learns to fit the feature combinations to the label. Then, after training has been completed, you can use the trained model to predict labels for new items for which the label is unknown.

A few regression machine learning scenarios are:

* Using characteristics of houses, such as square footage and number of rooms, to predict home prices.
* Using characteristics of farm conditions, such as weather and soil quality, to predict crop yield.
* Using characteristics of a past campaign, such as advertising logs, to predict future advertisement clicks.

***

### What is Azure Machine Learning designer?

To author regression machine learning models in Azure Machine Learning studio, you can use a visual interface called **designer** that you can use to train, test, and deploy machine learning models. The drag-and-drop interface makes use of clearly defined inputs and outputs that can be shared, reused, and version controlled.

![Designer](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-regression-model-azure-machine-learning-designer/media/designer-canvas-screenshot.png)

**Pipelines** let you organize, manage, and reuse complex machine learning workflows across projects and users. A pipeline starts with the dataset from which you want to train the model. Each time you run a pipeline, the configuration of the pipeline and its results are stored in your workspace as a pipeline job.

![Pipelines](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-regression-model-azure-machine-learning-designer/media/pipeline-page-example.png)

An **component** encapsulates one step in a machine learning pipeline. You can think of a component as a programming function and as a building block for Azure Machine Learning pipelines. In a pipeline project, you can access data assets and components from the left panel's Asset Library tab.

![Components](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-regression-model-azure-machine-learning-designer/media/components-example.png)

You can create **data assets** on the Data page from local files, a datastore, web files, and Open Datasets. These data assets will appear along with standard sample datasets in designer's Asset Library.

![Data Assets](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-regression-model-azure-machine-learning-designer/media/data-creation-location.png)

A **job** executes a task against a specified compute target. Jobs enable systematic tracking for your machine learning experimentation and workflows. Once a job is created, Azure ML maintains a run record for the job. All of your jobs' run records can be viewed in Azure ML studio. In your designer project, you can access the status of a pipeline job using the Submitted jobs tab on the left pane.

![Jobs](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-regression-model-azure-machine-learning-designer/media/submitted-jobs-location.png)

You can find all the jobs you have run in a workspace on the Jobs page.

![All Jobs](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-regression-model-azure-machine-learning-designer/media/jobs-page-location.png)

***

### Regression steps

You can think of the steps to train and evaluate a regression machine learning model as:

1. **Prepare data**: Identify the features and label in a dataset. Pre-process, or clean and transform, the data as needed.
2. **Train model**: Split the data into two groups, a training and a validation set. Train a machine learning model using the training data set. Test the machine learning model for performance using the validation data set. You will use designer's **Score Model** component to generate the predicted class label value. Once you connect all the components, you will want to run an experiment, which will use the data asset on the canvas to train and score a model.
3. **Evaluate performance**: Compare how close the model's predictions are to the known labels. You can review evaluation metrics on the completed job page by right-clicking on the **Evaluate model** component.
  ![Evaluate results](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-regression-model-azure-machine-learning-designer/media/evaluate-model-example.png)
4. **Deploy a predictive service**: After you train a machine learning model, you need to convert the training pipeline into a real-time **inference pipeline**. The inference pipeline performs the same data transformations as the first pipeline for new data. Then it uses the trained model to **infer**, or predict, label values based on its features. This model will form the basis for a predictive service that you can publish for applications to use. After creating the inference pipeline, you can deploy it as an endpoint. In the endpoints page, you can view deployment details, test your pipeline service with sample data, and find credentials to connect your pipeline service to a client application. The Deployment state on the **Details** tab will indicate **Healthy** when deployment is successful. On the **Test** tab, you can test your deployed service with sample data in a JSON format to test the service before connecting it to an application. You can find credentials for your service on the **Consume** tab. These credentials are used to connect your trained machine learning model as a service to a client application.
  ![Deployment](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-regression-model-azure-machine-learning-designer/media/endpoints-example-1.png)
  ![Test Tab](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-regression-model-azure-machine-learning-designer/media/endpoints-example-3.png)
  ![Consume Tab](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-regression-model-azure-machine-learning-designer/media/endpoints-example-2.png)

***

### Summary

In this module, you learned how to:

* Identify regression machine learning scenarios.
* Use Azure Machine Learning designer to train a regression model.
* Use a regression model for inferencing.
* Deploy a regression model as a service.

Source: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/create-regression-model-azure-machine-learning-designer/)
