
=================================================================================
                          Vehicle Project (ML project)
=================================================================================

In this project, we  implements a complete Machine Learning pipeline for vehicle data ingestion, validation, transformation, training, evaluation, and deployment. 
It leverages 
            MongoDB Atlas for data storage, 
            AWS services (S3, ECR, EC2) for model storage and deployment, and 
            integrates CI/CD for streamlined development deployment workflows.


Table of Contents

* [Project Setup]
* [MongoDB Atlas Setup]
* [Virtual Environment Setup]
* [Logging and Exception Handling]
* [Data Pipeline Components]
* [AWS Setup]
* [Model Evaluation and Deployment]
* [CI/CD Pipeline]
* [Contact](#contact)


Project Setup

1. Initialize project template
   Run `template.py` to generate the initial project structure.

2. Setup packaging metadata
   * Write `setup.py` and `pyproject.toml` for local package imports.

3. Create and activate virtual environment

4. MongoDB Atlas Setup

   * Sign up for [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) 
   * Create an M0 cluster 
   * Configure database user credentials.
   * Whitelist IP address `0.0.0.0/0` for global access.
   * Retrieve the connection string and replace `<password>`.
   * Add `notebook` folder and place your dataset in `data/`.
   * Use the `mongoDB_demo.ipynb` notebook for pushing and verifying data.


5. Logging and Exception Handling

   * Implement robust logging in `logger.py` and test in `demo.py`.
   * Implement custom exceptions in `exception.py` and validate functionality.

6. Data Pipeline Components

   * Data Ingestion: Configure MongoDB connection and fetch data as pandas DataFrame.
   * Data Validation: Use schema from `config.schema.yaml` for dataset validation.
   * Data Transformation: Implement feature engineering and prepare data for modeling.
   * Model Training: Train models using prepared data.
   * Follow stepwise integration and testing through `demo.py`.


7. AWS Setup

   * Configure AWS CLI credentials for user with Administrator Access.
   * Set environment variables:
   * Create S3 bucket for model storage.
   * Implement AWS S3 interaction 

8. Model Evaluation and Deployment

   * Develop model evaluation logic to measure performance change with thresholding.
   * Implement model pusher to deploy trained models to S3 bucket.
   * Structure prediction pipeline and expose REST API via `app.py`.
   * Add frontend resources in `static/` and `templates/` directories.


9. CI/CD Pipeline

   * Configure Docker environment with `Dockerfile` and `.dockerignore`.
   * Setup GitHub Actions workflow inside `.github/workflows/aws.yaml`.
   * Create IAM user (`usvisa-user`) for CI/CD access with appropriate permissions.
   * Setup ECR repository  and EC2 instance for deployment.
   * Connect EC2 with GitHub self-hosted runner for automated workflow execution.
   * Define GitHub Secrets for AWS credentials and ECR repository URI.

===========================================================================
                              Project Structure
===========================================================================

vehicle-insurance/
│
├── src/
│   ├── configuration/
│   ├── components/
│   ├── data_access/
│   ├── entity/
│   ├── aws_storage/
│   └── exception/
|   
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



Environment Variables
   * 'MongoDB_connection_URL'
   * `AWS_ACCESS_KEY_ID`
   * `AWS_SECRET_ACCESS_KEY`
   * `AWS_DEFAULT_REGION=us-east-1`

==========================================================================
                                   Contact
==========================================================================

For any questions, please contact:

* Email: hussnaintariq151@gmail.com)
* GitHub: (https://github.com/hussnaintariq151)



