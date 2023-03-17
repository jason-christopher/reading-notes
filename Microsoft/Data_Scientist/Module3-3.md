# Module 3 - Build and operate machine learning solutions with Azure Machine Learning

## Work with Data in Azure Machine Learning

### Introduction to datastores

In Azure Machine Learning, **datastores** are abstractions for cloud data sources. They encapsulate the information required to connect to data sources. You can access datastores directly in code by using the Azure Machine Learning SDK, and use it to upload or download data. Azure Machine Learning supports the creation of datastores for multiple kinds of Azure data source, including:

* Azure Storage (blob and file containers)
* Azure Data Lake stores
* Azure SQL Database
* Azure Databricks file system (DBFS)

Every workspace has two built-in datastores (an **Azure Storage blob container**, and an **Azure Storage file container**) that are used as system storage by Azure Machine Learning. There's also a third datastore that gets added to your workspace if you make use of the open datasets provided as samples.

In most machine learning projects, you will likely need to work with data sources of your own - either because you need to store larger volumes of data than the built-in datastores support, or because you need to integrate your machine learning solution with data from existing applications.

***

### Using and managing datastores

To add a datastore to your workspace, you can register it using the graphical interface in Azure Machine Learning studio, or you can use the Azure Machine Learning SDK. For example, the following code registers an Azure Storage blob container as a datastore named `blob_data`:

  ```python
  from azureml.core import Workspace, Datastore

  ws = Workspace.from_config()

  # Register a new datastore
  blob_ds = Datastore.register_azure_blob_container(workspace=ws, 
                                                    datastore_name='blob_data', 
                                                    container_name='data_container',
                                                    account_name='az_store_acct',
                                                    account_key='123456abcde789…')
  ```

You can view and manage datastores in Azure Machine Learning Studio, or you can use the Azure Machine Learning SDK. For example, the following code lists the names of each datastore in the workspace:

  ```python
  for ds_name in ws.datastores:
      print(ds_name)
  ```

You can get a reference to any datastore by using the `Datastore.get()` method: `blob_store = Datastore.get(ws, datastore_name='blob_data')`.

The workspace always includes a default datastore (initially, this is the built-in `workspaceblobstore` datastore), which you can retrieve by using the `get_default_datastore()` method of a **Workspace** object: `default_store = ws.get_default_datastore()`.

When planning for datastores, consider the following guidelines:

* When using Azure blob storage, **premium** level storage may provide improved I/O performance for large datasets. However, this option will increase cost and may limit replication options for data redundancy.
* When working with data files, although CSV format is very common, Parquet format generally results in better performance.
* You can access any datastore by name, but you may want to consider changing the default datastore (which is initially the built-in `workspaceblobstore` datastore).

To change the default datastore, use the `set_default_datastore()` method: `ws.set_default_datastore('blob_data')`.

***

### Introduction to datasets

***

### Summary

Source: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/work-with-data-in-aml/)
