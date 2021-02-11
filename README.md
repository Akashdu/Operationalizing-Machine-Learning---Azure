# Operationalizing Machine Learning

In this project we are training an AutoML Model and then it is deployed and then consumed. We are using the Bank Marketing Dataset. We are also creating a pipeline the project.

## Architectural Diagram
![Architectural Diagram](images/architecture.PNG)

## Key Steps

### 1. AutoML Experiment
Uploading the Bank Marketing Dataset in Azure
![Bank Marketing Dataset](images/dataset.PNG)

Next, we ran AutoML on the Bank Dataset. It took around 22min to train various models.
![AutoML Run Completion](images/completed_run.PNG)

Finally, we found the best model. The list is sorted in descending order in terms of accuracy.
![All Models](images/all_models.PNG)

VotingEnsemble was the best performing model with an accuracy of 91.92%.
![Model with best accuracy](images/best_model.PNG)

### 2. Model Deployment
The next step was to deploy the best model which was VotingEnsemble.
![Deploy Voting Ensemble](images/deployment_successful.PNG)
![Deploy Voting Ensemble](images/deployment_successful_2.PNG)

### 3. Enable Logging
The best performing model was deployed using Azure Container Instance (ACI) and authentication was enabled while deploying. We also enabled Application Insights using logs.py file. Application Insights are disabled before executing logs.py.
![Application Insights](images/insights.PNG)

We can also check the logs after running the logs.py file
![Logs](images/insights_2.PNG)
![Logs](images/insights_3.PNG)

### 4. Swagger
We'll use the serve.py file to serve json file which contains the schema of the REST API through which the model can be called. We have downloaded the swagger.json file from the deployed model.
![Swagger UI](images/swagger_ui.png)


Calling the REST API from Swagger
![Swagger POST request](images/swagger_response.png)

### 5. Model Endpoint
After the model has been deployed, we'll use the endpoints.py file to send request to the REST API.
![Model Endpoint](images/end_point.PNG)

### 6. Create, Publish and Consume AzureML Pipeline
Below is the screenshot that confirms that the AzureML Pipeline was completed the execution successfully.
![Pipeline executed successfully](images/pipeline_completed_2.PNG)

We can see the details of the pipeline in the endpoints section.![Pipeline Endpoint](images/pipeline_endpoint.PNG)

In the below screenshot we can see the pipeline is running
![Pipeline Running](images/pipeline_running.PNG)

Run widget gives us information related to the pipeline run status. Through this, you can track the process of the pipelines from the notebook without having to naviagate to the azure studio.
![Pipeline run widget complete](images/pipeline_endpoint_run_widget.png)

Finally, we can see the details about the completed pipeline along with other details such as rest endpoints
![Pipeline Endpoint](images/pipeline_endpoint_2.PNG)

## Future work
1. We are using Azure Container Instance (ACI) to deploy the model. We could deploy the model using Azure Kubernetes Instance (AKS) and also compare the deployment time and cost.
2. We are choosing the best model based on the accuracy but the data that we are using is imbalanced. The Accuracy metric is not ideal for imbalanced dataset. What We could do is understand the business requirement in more detail and choose the right metric.

## Screen Recording
https://www.youtube.com/watch?v=-EyucVP8Q6w
