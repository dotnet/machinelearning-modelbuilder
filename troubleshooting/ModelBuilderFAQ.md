# Model Builder FAQ

## Why isn't GPU supported for my scenario? 
Model Builder only supports GPU training for Image Classification tasks. It does not support GPU training for any text based scenarios. The advantages for using GPU is only prevalent for deep learning tasks. Classical ML algorithms in ML.NET (classification, regression) aren't helped very much by training on GPU.

Want more info? Check out this [blog](https://dasha.ai/en-us/blog/pytorch-ml.net-inference-performance-comparison) written by the folks at Dasha, or see info provided by community members [torronen](https://github.com/dotnet/machinelearning/issues/5873#issuecomment-1034074969) and [jucchytil](https://github.com/dotnet/machinelearning-modelbuilder/issues/1158#issuecomment-759190047). 
