# Image Classification using AWS SageMaker

Use AWS Sagemaker to train a pretrained model that can perform image classification by using the Sagemaker profiling, debugger, hyperparameter tuning and other good ML engineering practices. This can be done on either the provided dog breed classication data set or one of your choice.

## Project Set Up and Installation
Enter AWS through the gateway in the course and open SageMaker Studio. 
Download the starter files.
Download/Make the dataset available. 

## Dataset
The provided dataset is the dogbreed classification dataset which can be found in the classroom.
The project is designed to be dataset independent so if there is a dataset that is more interesting or relevant to your work, you are welcome to use it to complete the project.

### Access
Upload the data to an S3 bucket through the AWS Gateway so that SageMaker has access to the data. 

## Hyperparameter Tuning
What kind of model did you choose for this experiment and why? Give an overview of the types of parameters and their ranges used for the hyperparameter search



The model used in this project is ```resetnet50``` which is a pretrained model. The parameters used  instance_count, instance_type which refers to the number of machines and type of machine used respectively.
The models architecure has two layers

Remember that your README should:
- Include a screenshot of completed training jobs
- Logs metrics during the training process
- Tune at least two hyperparameters
- Retrieve the best best hyperparameters from all your training jobs

## Debugging and Profiling
 Give an overview of how you performed model debugging and profiling in Sagemaker
 
 ![](https://raw.githubusercontent.com/moseti1/udc-img-dog-classification/main/best-training-job.png)
 
 
 ![](https://raw.githubusercontent.com/moseti1/udc-img-dog-classification/main/loss-graph.png)
 
Traing of the model was successiful. Althoug loss would be plotted sucessifully. 

Solving this error require investigating the profiler report carefully.

### Results
 What are the results/insights did you get by profiling/debugging your model?
 
 Best traing job
 ![](https://raw.githubusercontent.com/moseti1/udc-img-dog-classification/main/best-hpo-job.png)
 
Job trainging debugging summary.Provides summary of training job, system resource usage statistics, framework metrics, rules summary, and detailed analysis from each rule. The graphs and tables are interactive.

 
 ![](https://raw.githubusercontent.com/moseti1/udc-img-dog-classification/main/debug-summary.png)

 Remember to provide the profiler html/pdf file in your submission.


## Model Deployment
 Give an overview of the deployed model and instructions on how to query the endpoint with a sample input.
 
 Deployment was sucessiful. You can query the endpont by passing an image item to the predict method of the model.

 Remember to provide a screenshot of the deployed active endpoint in Sagemaker.
 
 ![](https://raw.githubusercontent.com/moseti1/udc-img-dog-classification/main/endpoint-screen.png)
 
 
 ![](https://raw.githubusercontent.com/moseti1/udc-img-dog-classification/main/endpoint-screen1.png)
 
 To query the endpoint, create a  ```payload``` object from one of the test images and pass it to ```predictor.predict()```

## Standout Suggestions
**TODO (Optional):** This is where you can provide information about any standout suggestions that you have attempted.

