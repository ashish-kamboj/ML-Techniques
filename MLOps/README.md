## Methods of Model Deployment

1.   **PyCaret** - Once a model is finalized it can can be consumed locally using **save_model** functionality which save the transformation pipeline and trained model which can be consumed by end user applications as a binary pickle file. Alternatively, models can be deployed on cloud (e.g. AWS) by simply writing deploy_model (before that need to configure aws environment variables).


2.   **MLflow** - MLflow keep track of the model experiments, parameter and artifacts. MLflow can deploy the trained model locally as local REST API endpoints or to directly score files. In addition, MLflow can package models as self-contained Docker images with the REST API endpoint. 


3.   **AWS Sagemaker**: We can deploy in AWS using below two methods
    - Notebook Instance (basically a Jupyter notebook)
    - Amazon Sagemaker Studio


4.   **MLflow + AWS Sagemaker**
    - We have to build a container for this in order to push on Amazon ECR (the docker registery service) which Sagemaker use to create the endpoints and load the model
    - MLflow provides an API to create the container very easily
    - Once we create the container then call another API for deploying the model
    - Go to the Sagemaker and check for the endpoints (once the deployment is done)

6.   **Deploying Using Microsoft Azure ML**


5.   **Flask** - Deploying Model using Flask application
    - Need to create a final model object (we can save model object in some directory in local, it can be hdfs or s3 bucket)
    - Load the model object in flask application
    - Start Flask server
    - Based on the user input from flask application generate the prediction
    - Also, we can deploy this whole flask application on Heroku or any other cloud services (or Platform-as-a-Service applications)
    
    
6.   **PyWebIO** - Similar to the flask and steps will be same for deplying the ML model. Difference is
 - Easy to build web app with just simple python code (no need to knoe HTML, CSS and javascript)
 - Provide support integration into existing web services Flask, Django, Tornado, FastAPI(Starlette) framework etc.
 - Support Data Visualization which will be helpful in displaying the prediction results
 - Also, you can deploy PyWenIO application on Heroku or any other cloud services (or Platform-as-a-Service applications)
    
    
7.   **FastAPI** - a web framework for building microservices with python.Deploying machine learning models as microservice-based architecture, make code components re-usable, highly maintained, ease of testing, and of-course the quick response. It has a data validation system that can detect any invalid data type at the runtime.
    - Once We have ML model ready save it as .pkl file
    - Create API using FastAPI framework
    - Execute the app, which will open an UI where we'll get the API endpoints. We can test it out by inputting the values


8.   **Apache Airflow** - Apache Airflow is a workflow orchaestration tool for scheduling the jobs. Dependencies between tasks and thus complex workflows can be mapped quickly and efficiently.So, using this we can create and end-to-end ML pipeline from Data Cleaning to Data processing, Generating Features to Model Building.
    - So, Once we have model we can deploy it by creating an separate DAG which wil pull the saved (Model can be saved in hdfs, s3 etc.) model object and make the predictions using that model which can be easily automated/scheduled.
    - We can also create a separate DAG for updating the model (continuous training) based on the available new data.
    - In case of the multiple experiments and multiple models we can use **MLflow** along with the **Airflow** for saving the params, logs and model artifacts and then we can use MLflow API for fetching the model details

