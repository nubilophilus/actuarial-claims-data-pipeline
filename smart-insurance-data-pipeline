# Claims + Actuarial Data Pipeline: Technical Overview

## 🎯 Objective
Create a reliable and scalable data pipeline that integrates claims-level data with actuarial forecasts to improve reserve adequacy and pricing accuracy.

## 🧱 Tech Stack
- **Ingestion**: AWS Lambda + API Gateway (for real-time feeds)
- **ETL**: AWS Glue (PySpark), Pandas, SQL
- **Storage**: S3 (raw), Redshift (curated), Athena (ad hoc)
- **Modeling**: SageMaker (GLM + XGBoost ensemble)
- **Orchestration**: AWS Step Functions

## 🔗 Data Sources
| Source              | Description                           |
|---------------------|---------------------------------------|
| FNOL feed           | First Notice of Loss from claims API  |
| Payment/reserve tbl | Historical loss and reserve amounts   |
| Policy data         | Policyholder info, coverages, limits  |
| LDF tables          | Actuarial loss development factors    |

## ⚙️ Pipeline Flow
1. **Ingest** data via Lambda functions (event-driven)
2. **Validate** formats, schema, and missing values
3. **Join** claims to policies via `policy_id` and `claim_number`
4. **Calculate** LDFs and exposure metrics
5. **Stage** features into model-ready tables for SageMaker

## 📈 Output Metrics
- Reserve Adequacy Score: delta between actual and projected reserves
- Forecast Lift: improvement over baseline GLM
- Latency: <30s for real-time ingestion, <1hr batch window

## ✅ QA & Monitoring
- Data quality checks via Great Expectations
- Retry logic and failure alerts via SNS
