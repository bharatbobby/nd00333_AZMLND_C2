Machine learning with Azure - BankMarketing.

In this project of of the course "Machine Learning Engineer with Microsoft Azure", I used Microsoft Azure Machine Learning Studio Automated ML to create a model based on a dataset, deployoed that to a web service, consumed the endpoints to get the results back and also automated the flow using pipelines (created using a notebook)

An overview of the project
First we uploaded the BankMarketing dataset (csv file). The dataset was then combined with an AutomatedML step. The best model from the automl run was registered which came to be Voting Ensemble with accuracy of 94.617%. We deployed this model to a webservice using Azure Container Instance. We enabled the logging and enabled the application insights. We also consumed the deployed model using Swagger and used the endpoint.py script to interact with the trained model. We will fully automate the process by creating a Azure ML Pipeline via Python SDK to have Automation and Efficiency.
The main point of the model is determine if the user will subscribe - yes or no.

Architectural Diagram
![image](https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/efbc43cb-4e3f-4bc6-8bac-1a31d531bef1)

Key Steps
1. Create a dataset in Azure ML: Here is the data loaded into the ML workspace
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/4df14b6a-b08e-4ec2-b955-e45269cecf0d">

2.	Run an Auto ML experiment in azure portal: Using the Bank-marketing dataset, Automated ML was used on a binary classification
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/07303327-58bf-4f0f-a63f-ff3f1ae6af0d">

3.	Completed Auto ML experiment:
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/e98ca6ee-a1bf-466c-aaca-f54ff72c3a30">

4. See the best Model and its parameters- Voting Ensemble
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/de816cdd-66dc-44ab-abea-89b0e8f01f69">

5. Deploy this model to give an endpoint so that we can consume
(Currently - application insights enabled is false): Deploying a machine learning model using Azure Container Instance (ACI) allows me to create a scalable, serverless environment where we can interact with the model via HTTP POST requests.
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/504e647f-e21a-48da-be0c-e79ecc4b7cba">

6. To enable application insights - I used python script logs.py
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/0ff9b109-c80c-4e7f-8752-45823957bc6f">

7. Now after running the logs.py script - application insights enabled becomes true:
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/2bdd44a9-af75-4fb1-af53-293b24742975">

8. See logs: By enabling Application Insights logging, we can monitor the performance and diagnose issues with your deployed model in ACI. The combination of proper logging and configuring ACI to use Application Insights ensures comprehensive monitoring and logging capabilities.
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/082d3cca-ad85-4e76-89be-f9f2e35c08bc">

9. Deploy swagger to local machine using docker image and use swagger.json file from our model deployment to see documentation about endpoints:
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/721e136f-51d4-4533-820f-c8c15e88bb90">

10. Consume the endpoint giving 2 inputs and see the result using python script:
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/d57f4749-44c2-4d73-86ba-b97a0a675484">

11. Pipeline creation and running: Fully automate the process by creating a Azure ML Pipeline via Python SDK.
    Automation and Efficiency - Pipelines help manage the various stages of the machine learning process, from data preprocessing to model training and evaluation. The steps are outlined       in the 'aml-pipelines-with-automated-machine-learning-step.ipynb' Jupyter notebook.
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/4902b140-383f-4d10-b955-9adfbd26b5aa">
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/3f8c8c11-fcfd-4509-a22a-db24e139a9aa">
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/7fe468c0-1e4d-46cb-b0a6-22a4f7b4b746">

12 pipeline-rest-endpoint
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/00284bf8-d315-48d0-9d22-72fd35eb8efb">

Project Recording link:
https://drive.google.com/file/d/1snfSLA6HvE8HYnsEB1KRnvb8oR8f9Ag5/view?usp=sharing

Future development and improvements
1. Use feature engineering and parallelisation to create new features based on combining or transforming the data given might help model to perform better.
2. We can do hyper parameter (as learned in assignemnt 1) tuning to see if the model performs better.
3. We can apply parallel running step in the pipeline to do the training faster.

