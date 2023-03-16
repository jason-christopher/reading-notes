# Module 3 - Build and operate machine learning solutions with Azure Machine Learning

## Introduction to the Azure Machine Learning SDK

Azure Machine Learning enables you to manage machine learning model data preparation, training, validation, and deployment. It supports existing frameworks such as Scikit-Learn, PyTorch, and Tensorflow; and provides a cross-platform platform for operationalizing machine learning in the cloud.

### Azure Machine Learning workspaces

A **workspace** is a context for the experiments, data, compute targets, and other assets associated with a machine learning workload. A workspace defines the boundary for a set of related machine learning assets. You can use workspaces to group machine learning assets based on projects, deployment environments (for example, test and production), teams, or some other organizing principle. The assets in a workspace include:

* Compute targets for development, training, and deployment.
* Data for experimentation and model training.
* Notebooks containing shared code and documentation.
* Experiments, including run history with logged metrics and outputs.
* Pipelines that define orchestrated multi-step processes.
* Models that you have trained.

Workspaces are Azure resources, and as such they are defined within a **resource group** in an **Azure subscription**, along with other related Azure resources that are required to support the workspace. The Azure resources created alongside a workspace include:

* A storage account - used to store files used by the workspace as well as data for experiments and model training.
* An Application Insights instance, used to monitor predictive services in the workspace.
* An Azure Key Vault instance, used to manage secrets such as authentication keys and credentials used by the workspace.
* A container registry, created as-needed to manage containers for deployed models.

You can assign **role-based access control (RBAC)** authorization policies to a workspace, enabling you to manage permissions that restrict what actions specific Azure Active Directory (AAD) principals can perform.

You can create a workspace in any of the following ways:

* In the Microsoft Azure portal, create a new **Machine Learning** resource, specifying the subscription, resource group and workspace name.
* **Azure Machine Learning Python SDK** to run code that creates a workspace. For example, the following code creates a workspace named aml-workspace (assuming the Azure ML SDK for Python is installed and a valid subscription ID is specified):

  ```python
  from azureml.core import Workspace
    
    ws = Workspace.create(name='aml-workspace', 
                      subscription_id='123456-abc-123...',
                      resource_group='aml-resources',
                      create_resource_group=True,
                      location='eastus'
                     )
  ```

* **Azure Command Line Interface (CLI)** with the Azure Machine Learning CLI extension. For example, you could use the following command (which assumes a resource group named aml-resources has already been created): `az ml workspace create -w 'aml-workspace' -g 'aml-resources'`
* Create an **Azure Resource Manager template**.

***

### Azure Machine Learning tools and interfaces

Azure Machine Learning provides a cloud-based service that offers flexibility in how you use it. There are user interfaces specifically designed for Azure Machine Learning:

* **Azure Machine Learning studio** - web-based tool for managing an Azure Machine Learning workspace. It enables you to create, manage, and view all of the assets in your workspace and provides the following graphical tools:
  * **Designer**: A drag and drop interface for "no code" machine learning model development.
  * **Automated Machine Learning**: A wizard interface that enables you to train a model using a combination of algorithms and data preprocessing techniques to find the best model for your data.
* **Azure Machine Learning SDK** - used to create, manage, and use assets in an Azure Machine Learning workspace. By writing scripts to create and manage resources, you can:
  * Run machine learning operations from your preferred development environment.
  * Automate asset creation and configuration to make it repeatable.
  * Ensure consistency for resources that must be replicated in multiple environments (for example, development, test, and production)
  * Incorporate machine learning asset configuration into developer operations (DevOps) workflows, such as continuous integration / continuous deployment (CI/CD) pipelines.

  Installing the Azure Machine Learning SDK for Python:
  1. Install the Azure Machine Learning SDK for Python by using the `pip` package management utility: `pip install azureml-sdk`
  2. Install the `azureml-widgets` package which provides support for interactive widgets in a Jupyter notebook environment: `pip install azureml-sdk azureml-widgets`
  3. After installing the SDK package in your Python environment, you can write code to connect to your workspace and perform machine learning operations:

      ```python
      {
        "subscription_id": "1234567-abcde-890-fgh...",
        "resource_group": "aml-resources",
        "workspace_name": "aml-workspace"
      }
      ```

  4. To connect to the workspace using the configuration file, you can use the `from_config` method of the Workspace class in the SDK. By default, the `from_config` method looks for a file named `config.json` in the folder containing the Python code file, but you can specify another path if necessary.

      ```python
      from azureml.core import Workspace

      ws = Workspace.from_config()
      ```

  5. As an alternative to using a configuration file, you can use the get method of the Workspace class with explicitly specified subscription, resource group, and workspace details as shown here - though the configuration file technique is generally preferred due to its greater flexibility when using multiple scripts:

      ```python
      from azureml.core import Workspace

      ws = Workspace.get(name='aml-workspace',
                        subscription_id='1234567-abcde-890-fgh...',
                        resource_group='aml-resources')
      ```

  6. 

***

### Summary

In this module, you learned how to:

* Provision an Azure Machine Learning workspace.
* Use tools and interfaces to work with Azure Machine Learning.
* Run code-based experiments in an Azure Machine Learning workspace.

Source: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-machine-learning-service/)
