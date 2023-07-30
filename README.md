# End-to-End-MLOps
MLOps Development and Deployment

Repo base on: [Youtube Video](https://www.youtube.com/watch?v=pxk1Fr33-L4&t=20s&ab_channel=KrishNaik) by Krish Naik

## Structure

```bash
END-TO-END-MLOPS
   |-- Dockerfile   # Create a Image with MLOps project
   |-- app.py       # Application Interfaces
   |-- main.py      # Run project pipeline -Data Ingestion
   |                #                      -Data Validation
   |                #                      -Data Transformation
   |                #                      -Model Trainer
   |                #                      -Model Evaluation
   |-- setup.py
   |-- template.py # Create folder and empty files with project Structure
   |-- requirements.txt # Libraries needed for code
   |-- test.py
   |-- params.yaml
   |-- schema.yaml  # Input data format Columns, Types & Target
   |-- .github
   |   |-- workflows
   |   |   |-- main.yaml
   |-- config/
   |   |-- config.yaml      # Path of files for each stage
   |-- logs/
   |   |-- running_logs.log # File with console logs
   |-- research/            # Runs each pipeline stage on a Jupyter Notebook
   |   |-- trial.ipynb
   |   |-- 01_data_ingestion.ipynb
   |   |-- 02_data_validation.ipynb
   |   |-- 03_data_transformation.ipynb
   |   |-- 03_model_trainer.ipynb
   |-- src/
   |   |-- mlproject/
   |   |   |-- components/  # Define functions to be used on pipeline
   |   |   |   |-- data_ingestion.py        # Download input files as zip and unzip
   |   |   |   |-- data_validation.py       # Validate data schema and clean data
   |   |   |   |-- data_transformation.py   # Run any transformation need for data and split it
   |   |   |   |-- model_trainer.py
   |   |   |-- config/
   |   |   |   |-- configuration.py     # Create directories, files and validate input functions (Is not use on main, mmm)
   |   |   |-- constants/
   |   |   |   |-- __init__.py          # OS path for yaml files (config, schema, params)
   |   |   |-- entity/
   |   |   |   |-- config_entity.py     # Create class data (Need more info)
   |   |   |-- pipeline/    # Run Stage and write Logs
   |   |   |   |-- stage_01_data_ingestion.py       # Download input files as zip and unzip files
   |   |   |   |-- stage_02_data_validation.py      # Validate data schema and clean data
   |   |   |   |-- stage_03_data_transformation.py  # Run any transformation need for data and split it
   |   |   |   |-- stage_04_model_trainer.py
   |   |   |   |-- stage_05.py
   |   |   |-- utils/
   |   |   |   |-- common.py            # Validation for input type
   |   |   |-- __init__.py              # Logger information
   |-- templates/
   |   |-- index.html
```

<sup>[1](#structure) This folder structure is needed to run MLFlow Library</sup>

## Workflows

1. Update config.yaml
2. Update schema.yaml
3. Update params.yaml
4. Update the entity
5. Update the configuration manager in src config
6. Update the components
7. Update the pipeline 
8. Update the main.py
9. Update the app.py


# How to run by your self?
### STEPS:

Clone the repository

```bash
git clone https://github.com/Ferflogo/End-to-End-MLOps.git
```

<sup>[2](#jupyternb) If want to run code, but not implement the MLOps pipeline (MLFlow), can be run everything from the jupyter notebooks.</sup>

### STEP 01- Create an environment for python with conda or pyvenv

Don't mess with base python XD

```bash
conda create -n mlops python=3.8 -y
```

```bash
conda activate mlops
```

### STEP 02- install the requirements

```bash
pip install -r requirements.txt
```


```bash
# Finally run the following command
python app.py
```

Now,
```bash
open up you local host and port
```



## MLflow

[Documentation](https://mlflow.org/docs/latest/index.html)


##### cmd
- mlflow ui

### dagshub
[dagshub](https://dagshub.com/)

MLFLOW_TRACKING_URI=https://dagshub.com/entbappy/End-to-end-Machine-Learning-Project-with-MLflow.mlflow \
MLFLOW_TRACKING_USERNAME=entbappy \
MLFLOW_TRACKING_PASSWORD=6824692c47a369aa6f9eac5b10041d5c8edbcef0 \
python script.py

Run this to export as env variables:

```bash

export MLFLOW_TRACKING_URI=https://dagshub.com/entbappy/End-to-end-Machine-Learning-Project-with-MLflow.mlflow

export MLFLOW_TRACKING_USERNAME=entbappy 

export MLFLOW_TRACKING_PASSWORD=6824692c47a369aa6f9eac5b10041d5c8edbcef0

```



# AWS-CICD-Deployment-with-Github-Actions

## 1. Login to AWS console.

## 2. Create IAM user for deployment

	#with specific access

	1. EC2 access : It is virtual machine

	2. ECR: Elastic Container registry to save your docker image in aws


	#Description: About the deployment

	1. Build docker image of the source code

	2. Push your docker image to ECR

	3. Launch Your EC2 

	4. Pull Your image from ECR in EC2

	5. Lauch your docker image in EC2

	#Policy:

	1. AmazonEC2ContainerRegistryFullAccess

	2. AmazonEC2FullAccess

	
## 3. Create ECR repo to store/save docker image
    - Save the URI: 566373416292.dkr.ecr.ap-south-1.amazonaws.com/mlproj

	
## 4. Create EC2 machine (Ubuntu) 

## 5. Open EC2 and Install docker in EC2 Machine:
	
	
	#optinal

	sudo apt-get update -y

	sudo apt-get upgrade
	
	#required

	curl -fsSL https://get.docker.com -o get-docker.sh

	sudo sh get-docker.sh

	sudo usermod -aG docker ubuntu

	newgrp docker
	
# 6. Configure EC2 as self-hosted runner:
    setting>actions>runner>new self hosted runner> choose os> then run command one by one


# 7. Setup github secrets:

    AWS_ACCESS_KEY_ID=

    AWS_SECRET_ACCESS_KEY=

    AWS_REGION = us-east-1

    AWS_ECR_LOGIN_URI = demo>>  566373416292.dkr.ecr.ap-south-1.amazonaws.com

    ECR_REPOSITORY_NAME = simple-app




## About MLflow 
MLflow

 - Its Production Grade
 - Trace all of your expriements
 - Logging & tagging your model
