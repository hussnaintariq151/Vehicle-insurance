---

# Vehicle Data Ingestion and ML Pipeline Project

## Overview

This project implements a complete Machine Learning pipeline for vehicle data ingestion, validation, transformation, training, evaluation, and deployment. It leverages MongoDB Atlas for data storage, AWS services (S3, ECR, EC2) for model storage and deployment, and integrates CI/CD for streamlined development and deployment workflows.


Table of Contents

* [Project Setup](#project-setup)
* [MongoDB Atlas Setup](#mongodb-atlas-setup)
* [Virtual Environment Setup](#virtual-environment-setup)
* [Logging and Exception Handling](#logging-and-exception-handling)
* [Data Pipeline Components](#data-pipeline-components)
* [AWS Setup](#aws-setup)
* [Model Evaluation and Deployment](#model-evaluation-and-deployment)
* [CI/CD Pipeline](#cicd-pipeline)
* [Project Structure](#project-structure)
* [Environment Variables](#environment-variables)
* [Contact](#contact)


Project Setup

1. Initialize project template
   Run `template.py` to generate the initial project structure.

2. Setup packaging metadata

   * Write `setup.py` and `pyproject.toml` for local package imports.
   * Refer to `crashcourse.txt` for detailed guidance on packaging.

3. Create and activate virtual environment

   ```bash
   conda create -n vehicle python=3.10 -y
   conda activate vehicle
   pip install -r requirements.txt
   ```

4. MongoDB Atlas Setup

1. Sign up for [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) and create a new project.
2. Create an M0 cluster with default settings.
3. Configure database user credentials.
4. Whitelist IP address `0.0.0.0/0` for global access.
5. Retrieve the connection string and replace `<password>`.
6. Add `notebook` folder and place your dataset in `data/`.
7. Use the `mongoDB_demo.ipynb` notebook for pushing and verifying data.


Virtual Environment Setup

* Use `requirements.txt` with `-e .` to install local packages inside your virtual environment.
* Ensure your packages are correctly installed with `pip list`.


Logging and Exception Handling

* Implement robust logging in `logger.py` and test in `demo.py`.
* Implement custom exceptions in `exception.py` and validate functionality.


Data Pipeline Components

* Data Ingestion: Configure MongoDB connection and fetch data as pandas DataFrame.
* Data Validation: Use schema from `config.schema.yaml` for dataset validation.
* Data Transformation: Implement feature engineering and prepare data for modeling.
* Model Training: Train models using prepared data with appropriate estimator classes.
* Follow stepwise integration and testing through `demo.py`.


AWS Setup

1. Configure AWS CLI credentials for user with AdministratorAccess.
2. Set environment variables:

   * `AWS_ACCESS_KEY_ID`
   * `AWS_SECRET_ACCESS_KEY`
3. Create S3 bucket (`my-model-mlopsproject`) in `us-east-1` region for model storage.
4. Implement AWS S3 interaction logic inside `src/aws_storage` and define related entities in `entity/s3_estimator.py`.


Model Evaluation and Deployment

* Develop model evaluation logic to measure performance change with thresholding.
* Implement model pusher to deploy trained models to S3 bucket.
* Structure prediction pipeline and expose REST API via `app.py`.
* Add frontend resources in `static/` and `templates/` directories.


CI/CD Pipeline

* Configure Docker environment with `Dockerfile` and `.dockerignore`.
* Setup GitHub Actions workflow inside `.github/workflows/aws.yaml`.
* Create IAM user (`usvisa-user`) for CI/CD access with appropriate permissions.
* Setup ECR repository (`vehicleproj`) and EC2 instance (`vehicledata-machine`) for deployment.
* Connect EC2 with GitHub self-hosted runner for automated workflow execution.
* Define GitHub Secrets for AWS credentials and ECR repository URI.


Project Structure

vehicle-project/
│
├── src/
│   ├── configuration/
│   ├── components/
│   ├── data_access/
│   ├── entity/
│   ├── aws_storage/
│   └── ...
├── notebook/
│   ├── mongoDB_demo.ipynb
│   └── data/
├── static/
├── templates/
├── requirements.txt
├── setup.py
├── pyproject.toml
├── Dockerfile
├── .github/workflows/aws.yaml
├── demo.py
├── logger.py
├── exception.py
└── README.md
```


Environment Variables

Set the following environment variables according to your operating system before running the project:

* **MongoDB connection URL:

  * Bash: `export MONGODB_URL="mongodb+srv://<username>:<password>@cluster0.mongodb.net/mydb"`
  * PowerShell: `$env:MONGODB_URL = "mongodb+srv://<username>:<password>@cluster0.mongodb.net/mydb"`

* AWS Credentials:

  * `AWS_ACCESS_KEY_ID`
  * `AWS_SECRET_ACCESS_KEY`
  * `AWS_DEFAULT_REGION=us-east-1`



Contact

For any questions or support, please contact:

* Email: [your.email@example.com]hussnaintariq151@gmail.com)
* GitHub: [github.com/yourusername](https://github.com/hussnaintariq151)

---

This project follows best practices for scalable machine learning pipelines integrated with cloud services and CI/CD workflows.


