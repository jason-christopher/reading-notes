# Module 2 - Microsoft Azure AI Fundamentals: Explore visual tools for machine learning

## Use Automated Machine Learning in Azure Machine Learning

### Types of machine learning

There are two general approaches to machine learning, **supervised** and **unsupervised** machine learning. In both approaches, you train a model to make predictions.

The **supervised machine** learning approach requires you to start with a dataset with known label values:

* **Regression**: used to predict a continuous value; like a price, a sales total, or some other measure.
* **Classification**: used to determine a class label; an example of a binary class label is whether a patient has diabetes or not; an example of multi-class labels is classifying text as positive, negative, or neutral.

The **unsupervised** machine learning approach starts with a dataset without known label values.

* **Clustering**: used to determine labels by grouping similar information into label groups; like grouping measurements from birds into species.

### What is Azure Machine Learning studio?

**Azure Machine Learning** is a cloud-based service that helps simplify some of the tasks it takes to prepare data, train a model, and deploy a predictive service.

To use Azure Machine Learning, you first create a **workspace** resource in your Azure subscription. You can then use this workspace to manage data, compute resources, code, models, and other artifacts related to your machine learning workloads.

**Azure Machine Learning studio** is a web portal for machine learning solutions in Azure. It includes a wide range of features and capabilities that help data scientists prepare data, train models, publish predictive services, and monitor their usage. There are four kinds of compute resource you can create:

* **Compute Instances**: Development workstations that data scientists can use to work with data and models.
* **Compute Clusters**: Scalable clusters of virtual machines for on-demand processing of experiment code.
* **Inference Clusters**: Deployment targets for predictive services that use your trained models.
* **Attached Compute**: Links to existing Azure compute resources, such as Virtual Machines or Azure Databricks clusters.
![Azure Machine Learning Studio](https://learn.microsoft.com/en-us/training/wwl-data-ai/use-automated-machine-learning/media/studio-home.png)

### What is Azure Automated Machine Learning?

Azure Machine Learning includes an **automated machine learning** capability that automatically tries multiple pre-processing techniques and model-training algorithms in parallel.

You can create an automated machine learning **job** in Azure Machine Learning studio.

![Create job](https://learn.microsoft.com/en-us/training/wwl-data-ai/use-automated-machine-learning/media/automated-machine-learning-portal.png)

You can configure multiple settings for your job before starting an automated machine learning run. The run configuration provides the information needed to specify your training script, compute target, and Azure ML environment in your run configuration and run a training job.

![Configure jobs](https://learn.microsoft.com/en-us/training/wwl-data-ai/use-automated-machine-learning/media/start-job-machine-learning-studio.png)

### Understand the AutoML process

You can think of the steps in a machine learning process as:

* **Prepare data**: Identify the features and label in a dataset. Pre-process, or clean and transform, the data as needed. In Azure Machine Learning, data for model training and other operations is usually encapsulated in an object called a dataset. You can create your own dataset in Azure Machine Learning studio.
  ![Prepare Data](https://learn.microsoft.com/en-us/training/wwl-data-ai/use-automated-machine-learning/media/auto-machine-learning-select-data.png)
* **Train model**: Split the data into two groups, a training and a validation set. Train a machine learning model using the training data set. Test the machine learning model for performance using the validation data set. The automated machine learning capability in Azure Machine Learning supports **supervised** machine learning models:
  * **Classification** (predicting categories or classes)
  * **Regression** (predicting numeric values)
  * **Time series forecasting** (predicting numeric values at a future point in time)
  ![Train Model](https://learn.microsoft.com/en-us/training/wwl-data-ai/use-automated-machine-learning/media/choose-task-settings.png)
  In Automated Machine Learning, you can select configurations for the **primary metric**, type of model used for training, exit criteria, and concurrency limits.
  ![Select Configurations](https://learn.microsoft.com/en-us/training/wwl-data-ai/use-automated-machine-learning/media/machine-learning-run-configurations.png)
  ![Configure Details](https://learn.microsoft.com/en-us/training/wwl-data-ai/use-automated-machine-learning/media/training-validation.png)
* **Evaluate performance**: Compare how close the model's predictions are to the known labels. The **Predicted vs. True** chart should show a diagonal trend in which the predicted value correlates closely to the true value. The dotted line shows how a perfect model should perform. The closer the line of your model's average predicted value is to the dotted line, the better its performance. A histogram below the line chart shows the distribution of true values.
  ![Evaluate Performance](https://learn.microsoft.com/en-us/training/wwl-data-ai/use-automated-machine-learning/media/predicted-vs-true.png)
* **Deploy a predictive service**: After you train a machine learning model, you can deploy the model as an application on a server or device so that others can use it. In Azure Machine Learning, you can deploy a service as an **Azure Container Instances (ACI)** or to an **Azure Kubernetes Service (AKS)** cluster. For production scenarios, an AKS deployment is recommended, for which you must create an inference cluster compute target.

***

### Summary

In this module, you learned how to:

* Identify the machine learning process.
* Understand Azure Machine Learning capabilities.
* Use automated machine learning in Azure Machine Learning studio to train and deploy a predictive model.

Source: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/use-automated-machine-learning/)
