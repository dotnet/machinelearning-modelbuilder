## Introduction
Model Builder is a simple UI tool that runs locally for developers to build, train and ship custom machine learning models in your applications. [Try Model Builder preview now!](https://aka.ms/mlnettemplates). 

Developers with no ML expertise can use this simple visual interface to connect to their data stored in files, SQL Server and more for training the model.

Model Builder leverages best in class automated machine learning (AutoML) to evaluate different models. It produces the best model for your scenario without any tuning required from the developer.

At the end, developers can generate code for training and consuming this model in their applications.

<img src=".github/ml-dotnet-model-builder.gif">


This readme provides the following details for Model Builder:
* <a href="https://github.com/dotnet/machinelearning-samples/blob/master/modelbuilder/readme.md#Installation">Installation</a>
* <a href="https://dotnet.microsoft.com/learn/machinelearning-ai/ml-dotnet-get-started-tutorial/intro">Getting started tutorial</a>
* [Documentation](https://aka.ms/modelbuilderdocs)
* [Limitations](https://github.com/dotnet/machinelearning-samples/blob/master/modelbuilder/readme.md#Limitations)

## Installation

Model Builder can be installed on Visual Studio 2017/ 2019. You can install it by clicking "Download" from the [Visual Studio Marketplace](https://aka.ms/mlnettemplates)


**Pre-requisites**
* Visual Studio 2017 15.6 or later or Visual Studio 2019
* All SKU's of Visual Studio
* .NET Core 2.1 SDK

## Limitations
This is the first preview of Model Builder and has the following limitations. We are actively working on improving the experience in the future releases.

* There is a limit of 1GB on the training dataset.
* SQL Server has a limit of 100K rows for training
* Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported.


# Contributing

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

# Legal Notices

.NET Foundation and any contributors grant you a license to the .NET Foundation documentation and other content
in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode),
see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the
[LICENSE-CODE](LICENSE-CODE) file.

Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation
may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.
The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.
Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.

Privacy information can be found at https://privacy.microsoft.com/en-us/

.NET Foundation and any contributors reserve all other rights, whether under their respective copyrights, patents,
or trademarks, whether by implication, estoppel or otherwise.
