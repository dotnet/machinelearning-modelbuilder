# Dockerfiles

This directory contains a set of Dockerfiles for use as custom training environments in Azure Machine Learning. For more information on using Docker images to create environments in Azure Machine Learning, see the article [how to manage environments](https://docs.microsoft.com/azure/machine-learning/how-to-manage-environments-v2#create-an-environment-from-a-docker-image)

## Files

| Name | Location | Description |
| --- | --- | --- |
| Slim | [Dockerfiles/slim/Dockerfile](./slim/Dockerfile) | Contains .components included in NET 6 SDK Dockerfile | 
| ML.NET CLI | [Dockerfiles/mlnetcli/Dockerfile](./mlnetcli/Dockerfile) |

## Usage

For more information on using these images, see the related blog post,
[Train an ML.NET model with Azure ML](https://devblogs.microsoft.com/dotnet/training-a-ml-dotnet-model-with-azure-ml/#training-a-ml-net-model-via-azure-machine-learning).