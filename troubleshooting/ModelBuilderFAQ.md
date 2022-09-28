# Model Builder FAQ

## Why isn't GPU supported for my scenario? 
Model Builder only supports GPU training for Image Classification tasks. It does not support GPU training for any text based scenarios. The advantages for using GPU is only prevalent for deep learning tasks. Classical ML algorithms in ML.NET (classification, regression) aren't helped very much by training on GPU.

Several users have tested and written up information on this. See [comment](https://github.com/dotnet/machinelearning/issues/5873#issuecomment-1034074969) for more information. 
