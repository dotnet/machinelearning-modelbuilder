THIS IS WORK IN PROGRESS 

Setting up a pipeline to enable continuous integration of an ML model. 
1. Checkin the mbconfig file to your repo
2. Add new pipeline in Azure Pipelines
3. Setup AML permissions to Azure Devops
    - Goto Project settings, select Service connections, create a new connection of type Azure Resource Manager, select Service principal (automatic) and configure it to the Resource Group of your Machine Learning workspace. Name it azmldemows. For more details see [here](https://docs.microsoft.com/en-us/azure/devops/pipelines/library/service-endpoints?view=azure-devops). 
4. Add [retrain.yml](./retrain.yml). Replace the ml-ws-connection, ml-ws, ml-rg, ml-ct, and mbConfig-file-path.
5. Add [aml.yml](./aml.yml). Replace experiment_name and compute_name
6. Add [DOCKERFILE](./DOCKERFILE)

