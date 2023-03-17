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

**Datasets** are versioned packaged data objects that can be easily consumed in experiments and pipelines. Datasets are the recommended way to work with data, and are the primary mechanism for advanced Azure Machine Learning capabilities like data labeling and data drift monitoring. Datasets are typically based on files in a **datastore**, though they can also be based on URLs and other sources. You can create the following types of dataset:

* **Tabular**: The data is read from the dataset as a table. You should use this type of dataset when your data is consistently structured and you want to work with it in common tabular data structures, such as Pandas dataframes.
* **File**: The dataset presents a list of file paths that can be read as though from the file system. Use this type of dataset when your data is unstructured, or when you need to process the data at the file level (for example, to train a convolutional neural network from a set of image files).

To create a **tabular** dataset using the SDK, use the `from_delimited_files` method of the `Dataset.Tabular` class. The paths can include **wildcards** (for example, `/files/*.csv`) making it possible to encapsulate data from a large number of files in a single dataset. The dataset in this example includes data from two file paths within the default datastore (the `current_data.csv` file in the `data/files` folder and all `.csv` files in the `data/files/archive/` folder). After creating the dataset, the code registers it in the workspace with the name `csv_table`:

  ```python
  from azureml.core import Dataset

  blob_ds = ws.get_default_datastore()
  csv_paths = [(blob_ds, 'data/files/current_data.csv'),
              (blob_ds, 'data/files/archive/*.csv')]
  tab_ds = Dataset.Tabular.from_delimited_files(path=csv_paths)
  tab_ds = tab_ds.register(workspace=ws, name='csv_table')
  ```

To create a **file** dataset using the SDK, use the `from_files` method of the `Dataset.File` class. The dataset in this example includes all `.jpg` files in the `data/files/images` path within the default datastore. After creating the dataset, the code registers it in the workspace with the name `img_files`.

  ```python
  from azureml.core import Dataset

  blob_ds = ws.get_default_datastore()
  file_ds = Dataset.File.from_files(path=(blob_ds, 'data/files/images/*.jpg'))
  file_ds = file_ds.register(workspace=ws, name='img_files')
  ```

After **registering** a dataset, you can retrieve it by using any of the following techniques:

* The **datasets dictionary** attribute of a **Workspace** object.
* The `get_by_name` or `get_by_id` method of the **Dataset** class.

  ```python
  import azureml.core
  from azureml.core import Workspace, Dataset

  # Load the workspace from the saved config file
  ws = Workspace.from_config()

  # Get a dataset from the workspace datasets collection
  ds1 = ws.datasets['csv_table']

  # Get a dataset by name from the datasets class
  ds2 = Dataset.get_by_name(ws, 'img_files')
  ```

Datasets can be **versioned**, enabling you to track historical versions of datasets that were used in experiments, and reproduce those experiments with data in the same state. You can create a new version of a dataset by registering it with the same name as a previously registered dataset and specifying the `create_new_version` property. In this example, the `.png` files in the `images` folder have been added to the definition of the `img_paths` dataset example used in the previous topic.

  ```python
  img_paths = [(blob_ds, 'data/files/images/*.jpg'),
              (blob_ds, 'data/files/images/*.png')]
  file_ds = Dataset.File.from_files(path=img_paths)
  file_ds = file_ds.register(workspace=ws, name='img_files', create_new_version=True)
  ```

You can **retrieve** a specific version of a dataset by specifying the version parameter in the `get_by_name` method of the **Dataset** class: `img_ds = Dataset.get_by_name(workspace=ws, name='img_files', version=2)`.

***

### Working with Tabular datasets

You can read data directly from a **tabular** dataset by converting it into a Pandas or Spark dataframe:

  ```python
  df = tab_ds.to_pandas_dataframe()
  # code to work with dataframe goes here, for example:
  print(df.head())
  ```

When you need to access a dataset in an experiment script, you must pass the dataset to the script by:

* Using a **script argument** for a tabular dataset. When you take this approach, the argument received by the script is the **unique ID** for the dataset in your workspace. In the script, you can then get the workspace from the run context and use it to retrieve the dataset by it's **ID**. Here are examples of the **ScriptRunConfig** and **Script**, respectively:

  ```python
  env = Environment('my_env')
  packages = CondaDependencies.create(conda_packages=['pip'],
                                      pip_packages=['azureml-defaults',
                                                    'azureml-dataprep[pandas]'])
  env.python.conda_dependencies = packages

  script_config = ScriptRunConfig(source_directory='my_dir',
                                  script='script.py',
                                  arguments=['--ds', tab_ds],
                                  environment=env)
  ```

  ```python
  from azureml.core import Run, Dataset

  parser.add_argument('--ds', type=str, dest='dataset_id')
  args = parser.parse_args()

  run = Run.get_context()
  ws = run.experiment.workspace
  dataset = Dataset.get_by_id(ws, id=args.dataset_id)
  data = dataset.to_pandas_dataframe()
  ```

* Using a **named input** for a tabular dataset. In this approach, you use the `as_named_input` method of the dataset to specify a name for the dataset. Then in the script, you can retrieve the dataset by name from the run context's `input_datasets` collection without needing to retrieve it from the workspace. Note that if you use this approach, you still need to include a **script argument** for the dataset, even though you don’t actually use it to retrieve the dataset. Here are examples of the **ScriptRunConfig** and **Script**, respectively:

  ```python
  env = Environment('my_env')
  packages = CondaDependencies.create(conda_packages=['pip'],
                                      pip_packages=['azureml-defaults',
                                                    'azureml-dataprep[pandas]'])
  env.python.conda_dependencies = packages

  script_config = ScriptRunConfig(source_directory='my_dir',
                                  script='script.py',
                                  arguments=['--ds', tab_ds.as_named_input('my_dataset')],
                                  environment=env)
  ```

  ```python
  from azureml.core import Run

  parser.add_argument('--ds', type=str, dest='ds_id')
  args = parser.parse_args()

  run = Run.get_context()
  dataset = run.input_datasets['my_dataset']
  data = dataset.to_pandas_dataframe()
  ```

***

### Working with File datasets

You can use the `to_path()` method to return a list of the file paths encapsulated by the dataset:

  ```python
  for file_path in file_ds.to_path():
      print(file_path)
  ```

Just as with a **Tabular** dataset, there are two ways you can pass a **file** dataset to a script:

* Using a **script argument** for a file dataset. Unlike with a **tabular** dataset, you must specify a **mode** for the **file** dataset argument, which can be `as_download` or `as_mount`. This provides an access point that the script can use to read the files in the dataset. In most cases, you should use `as_download`, which copies the files to a temporary location on the compute where the script is being run. However, if you are working with a large amount of data for which there may not be enough storage space on the experiment compute, use `as_mount` to stream the files directly from their source. Here are examples of the **ScriptRunConfig** and **Script**, respectively:

  ```python
  env = Environment('my_env')
  packages = CondaDependencies.create(conda_packages=['pip'],
                                      pip_packages=['azureml-defaults',
                                                    'azureml-dataprep[pandas]'])
  env.python.conda_dependencies = packages

  script_config = ScriptRunConfig(source_directory='my_dir',
                                  script='script.py',
                                  arguments=['--ds', file_ds.as_download()],
                                  environment=env)
  ```

  ```python
  from azureml.core import Run
  import glob

  parser.add_argument('--ds', type=str, dest='ds_ref')
  args = parser.parse_args()
  run = Run.get_context()

  imgs = glob.glob(args.ds_ref + "/*.jpg")
  ```

* Using a **named input** for a file dataset. In this approach, you use the `as_named_input` method of the dataset to specify a name before specifying the **access mode**. Then in the script, you can retrieve the dataset by name from the run context's `input_datasets` collection and read the files from there. As with tabular datasets, if you use a named input, you still need to include a **script argument** for the dataset, even though you don’t actually use it to retrieve the dataset. Here are examples of the **ScriptRunConfig** and **Script**, respectively:

  ```python
  env = Environment('my_env')
  packages = CondaDependencies.create(conda_packages=['pip'],
                                      pip_packages=['azureml-defaults',
                                                    'azureml-dataprep[pandas]'])
  env.python.conda_dependencies = packages

  script_config = ScriptRunConfig(source_directory='my_dir',
                                  script='script.py',
                                  arguments=['--ds', file_ds.as_named_input('my_ds').as_download()],
                                  environment=env)
  ```

  ```python
  from azureml.core import Run
  import glob

  parser.add_argument('--ds', type=str, dest='ds_ref')
  args = parser.parse_args()
  run = Run.get_context()

  dataset = run.input_datasets['my_ds']
  imgs= glob.glob(dataset + "/*.jpg")
  ```

***

### Summary

Source: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/work-with-data-in-aml/)
