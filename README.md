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

The model used in this project is  `resetnet50` that is pretrained, with architecture `
    model.fc = nn.Sequential(
                   nn.Linear(2048, 128),
                   nn.ReLU(inplace=True),
                   nn.Linear(128, 133))`
                   
  

Remember that your README should:
- Include a screenshot of completed training jobs
- Logs metrics during the training process
- Tune at least two hyperparameters
- Retrieve the best best hyperparameters from all your training jobs

## Debugging and Profiling
 Give an overview of how you performed model debugging and profiling in Sagemaker

The model training process was a success. The best traing job had a `learning_rate` of `0.0033394403406322728`.

To debug the model i set a debug hook in the  `train_model.py` and `hpo.py` scripts. The hook records training summary of the model and gives overview of the training process including data and insights on the infrustructure used.To illustrate the model performance we draw a tensor graph as below.

![](https://raw.githubusercontent.com/moseti1/udc-img-dog-classification/main/loss-graph.png)



Training Job Summary

![](https://raw.githubusercontent.com/moseti1/udc-img-dog-classification/main/train-job-screen.png)

Best Train Job Hyperparameters

![](https://raw.githubusercontent.com/moseti1/udc-img-dog-classification/main/best-hpo-job.png)

### Results
 What are the results/insights did you get by profiling/debugging your model?
 
 Training of the model was a success with `Testing Loss: 55.0` and `Testing Accuracy: 15.0`

 Remember to provide the profiler html/pdf file in your submission.
 
 [profiler results](https://github.com/moseti1/udc-img-dog-classification/blob/88a92008cb8a1825b624f6ce2c3275f3a3a1cbf4/profiler-report.html)


## Model Deployment
Give an overview of the deployed model and instructions on how to query the endpoint with a sample input.

To query the model you create an image object and pass it to the model end point as in below.

```
with open("dogImages/test/010.Anatolian_shepherd_dog/Anatolian_shepherd_dog_00695.jpg", "rb") as f:
    payload = f.read()
    
from PIL import Image
import io
Image.open(io.BytesIO(payload))

response=predictor.predict(payload, initial_args={"ContentType": "image/jpeg"})
```


A screenshot of the deployed active endpoint in Sagemaker.

![](https://raw.githubusercontent.com/moseti1/udc-img-dog-classification/main/endpoint-screen.png)

## Standout Suggestions
**TODO (Optional):** This is where you can provide information about any standout suggestions that you have attempted.

