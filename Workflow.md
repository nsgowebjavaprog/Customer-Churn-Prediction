1️⃣ End-to-End ML Pipeline Flowchart

```
                ┌──────────────────────────┐
                │   Business Requirement   │
                │  (Reduce churn by 10%)   │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │   Data Collection (CSV)  │
                │  Telecom Customer Data   │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │  Upload to AWS S3 Bucket │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │   Data Ingestion Module  │
                │   (Fetch from S3)        │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │   Data Validation        │
                │  Schema + Drift Check    │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │   Feature Engineering    │
                │ Encoding, Scaling, SMOTE │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │    Model Training        │
                │  XGBoost / RF / LR       │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │   Model Evaluation       │
                │ Recall, F1, ROC-AUC      │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │   Model Registry (S3)    │
                │  model_v1.pkl            │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │    FastAPI Prediction    │
                │    Service               │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │ Dockerize Application    │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │ Push to AWS ECR          │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │ Deploy on EC2 / ECS      │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │  Monitoring (CloudWatch) │
                │  Logs + Drift Detection  │
                └──────────────────────────┘
```

2️⃣ AWS Architecture Workflow Diagram (Professional Version)

```
                        ┌────────────────────┐
                        │     End User       │
                        │  (Marketing Team)  │
                        └─────────┬──────────┘
                                  │ API Request
                                  ▼
                        ┌────────────────────┐
                        │   Load Balancer    │
                        └─────────┬──────────┘
                                  ▼
                        ┌────────────────────┐
                        │   EC2 / ECS        │
                        │  (Docker Container)│
                        │   FastAPI App      │
                        └─────────┬──────────┘
                                  │
                    ┌─────────────┴─────────────┐
                    ▼                           ▼
          ┌──────────────────┐        ┌──────────────────┐
          │  Preprocessor    │        │  Trained Model   │
          │  (preprocess.pkl)│        │  (model_v1.pkl)  │
          └─────────┬────────┘        └─────────┬────────┘
                    │                             │
                    └──────────────┬──────────────┘
                                   ▼
                        ┌────────────────────┐
                        │   Prediction       │
                        │  Churn / Not Churn │
                        └────────────────────┘
```

3️⃣ Training Pipeline Architecture (Offline Flow)

```
        ┌────────────────────┐
        │   Raw CSV Data     │
        └─────────┬──────────┘
                  ▼
        ┌────────────────────┐
        │  AWS S3 Storage    │
        └─────────┬──────────┘
                  ▼
        ┌────────────────────┐
        │  EC2 Training Job  │
        └─────────┬──────────┘
                  ▼
        ┌────────────────────┐
        │ Data Validation    │
        └─────────┬──────────┘
                  ▼
        ┌────────────────────┐
        │ Feature Engineering│
        └─────────┬──────────┘
                  ▼
        ┌────────────────────┐
        │ Model Training     │
        │ (MLflow Tracking)  │
        └─────────┬──────────┘
                  ▼
        ┌────────────────────┐
        │ Best Model Select  │
        └─────────┬──────────┘
                  ▼
        ┌────────────────────┐
        │ Save to S3 Model   │
        │ Registry           │
        └────────────────────┘

```

4️⃣ Real-Time Prediction Flow

```
User Input → API → Data Preprocessing → Model Prediction → Return Probability → Business Action

Example:
Customer ID 101 →
Churn Probability = 0.82 →
Send Discount Offer
```


> “Explain your architecture.”
> You say:

> “We built a production-grade churn prediction system using AWS S3 for storage, EC2 for training, MLflow for experiment tracking, Dockerized FastAPI service deployed via ECR, and monitored using CloudWatch. The pipeline is modular and supports retraining and model versioning.”
---
Designed and deployed an end-to-end production-grade churn prediction system on AWS with automated retraining, drift detection, MLflow tracking, and business impact analytics, reducing simulated churn by 12%.
