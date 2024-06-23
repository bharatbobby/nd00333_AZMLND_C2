# Machine learning with Azure - BankMarketing.

In this project of of the course "Machine Learning Engineer with Microsoft Azure", I used Microsoft Azure Machine Learning Studio Automated ML to create a model based on a dataset, deployoed that to a web service, consumed the endpoints to get the results back and also automated the flow using pipelines (created using a notebook)

# An overview of the project
First we uploaded the BankMarketing dataset (csv file). The dataset was then combined with an AutomatedML step. The best model from the automl run was registered which came to be Voting Ensemble with accuracy of 94.617%. We deployed this model to a webservice using Azure Container Instance. We enabled the logging and enabled the application insights. We also consumed the deployed model using Swagger and used the endpoint.py script to interact with the trained model. We will fully automate the process by creating a Azure ML Pipeline via Python SDK to have Automation and Efficiency.
The main point of the model is determine if the user will subscribe - yes or no.

# Architectural Diagram
![image](https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/efbc43cb-4e3f-4bc6-8bac-1a31d531bef1)

# Key Steps
1. Create a dataset in Azure ML: Here is the data loaded into the ML workspace
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/ad5b9ff4-937c-45d3-93cd-340c24f792cb">
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/36215300-a38b-4639-b72e-fddaee181ad7">

2.	Run an Auto ML experiment in azure portal: Using the Bank-marketing dataset, Automated ML was used on a binary classification
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/9ff14410-cadb-4033-a9bd-d17a0dc86dbe">

3.	Completed Auto ML experiment:
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/7a78dce2-e96c-46fc-87b0-4784a69730df">

4. See the best Model and its parameters- Voting Ensemble
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/bf4330c8-4ff8-48ea-bca1-51e4952cb24b">

5. Deploy this model to give an endpoint so that we can consume
(Currently - application insights enabled is false): Deploying a machine learning model using Azure Container Instance (ACI) allows me to create a scalable, serverless environment where we can interact with the model via HTTP POST requests.
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/1f9a9264-2dd1-4974-9cdb-3963d258b032">
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/f7436126-f641-401f-a79c-16440cb5a1ed">

6. To enable application insights - I used python script logs.py
<img width="777" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/cc5d1c12-ef18-4ea6-8ffe-f5373cfee3e1">   

8. Now after running the logs.py script - application insights enabled becomes true:
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/73bb00dc-8cb3-4b56-90bc-fa6dcd99bf77">

9. See logs: By enabling Application Insights logging, we can monitor the performance and diagnose issues with your deployed model in ACI. The combination of proper logging and configuring ACI to use Application Insights ensures comprehensive monitoring and logging capabilities.
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/30f0618b-da0b-4b9b-8433-443df494b8fa">

10. Deploy swagger to local machine using docker image and use swagger.json file from our model deployment to see documentation about endpoints:
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/1eb49652-8f47-4bef-b02e-abbeaee372d6">
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/178c1493-16a1-4c1a-b82c-1761d68e6837">

11. Consume the endpoint giving 2 inputs and see the result using python script:
    Serve.py executed
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/9f4c22a0-5964-48a1-9c48-86a1542b20c0">
Consume model
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/9a636cfe-c355-4c62-b484-6f9ddcb8d8e7">


13. Pipeline creation and running: Fully automate the process by creating a Azure ML Pipeline via Python SDK.
Automation and Efficiency - Pipelines help manage the various stages of the machine learning process, from data preprocessing to model training and evaluation. The steps are outlined       in the 'aml-pipelines-with-automated-machine-learning-step.ipynb' Jupyter notebook.
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/02ab03cf-0794-4d1f-a75e-1867161aca0e">
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/6f7ac237-6fb3-4a2c-b2bf-aaddf5f16e81">

Running pipeline

<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/97cebd3f-3d19-4b32-84ec-4f5a318c0637">

Completed Pipeline

<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/be2c1cc4-7967-4a53-8a0f-2cb81d8ff7cd">
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/f0d90c4c-4dda-4d91-852c-c427a7bada7a">

12 pipeline-rest-endpoint

<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/69820121-6dba-4284-bc38-d8ef008e943c">
<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/f00143be-17bc-4e85-8e86-121ddfc2cc40">

Published Pipeline overview

<img width="452" alt="image" src="https://github.com/bharatbobby/nd00333_AZMLND_C2/assets/46679136/37b78301-41ea-47ee-904e-1b5da6121089">


# Project Recording link:
https://drive.google.com/file/d/1APelYfOkcfRqIKQgtx1_sjctZ433cmdL/view?usp=sharing

# Future development and improvements
1. Use feature engineering and parallelisation to create new features based on combining or transforming the data given might help model to perform better.
2. We can do hyper parameter (as learned in assignemnt 1) tuning to see if the model performs better.
3. We can apply parallel running step in the pipeline to do the training faster.
