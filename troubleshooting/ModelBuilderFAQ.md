# Model Builder FAQ

## Why isn't GPU supported for my scenario? 
Model Builder supports GPU Training for tasks where the advantages outweigh the costs. For many scenarios, the cost of moving the data to the GPU outweighs the benefits the GPU provides. Currently only Image Classification is supported in Model Builder, while Data Classification, Value Prediction, Recommendation, Forecasting are not. 

Want more info? Check out this [blog](https://dasha.ai/en-us/blog/pytorch-ml.net-inference-performance-comparison) written by the folks at Dasha, or see info provided by community members [torronen](https://github.com/dotnet/machinelearning/issues/5873#issuecomment-1034074969) and [jucchytil](https://github.com/dotnet/machinelearning-modelbuilder/issues/1158#issuecomment-759190047). 
