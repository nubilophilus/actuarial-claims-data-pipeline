# 🧮 Actuarial Claims Data Pipeline

A scalable, end-to-end data pipeline that ingests claims-level insurance data, integrates actuarial development factors, and generates reserve adequacy and pricing forecasts using machine learning. Designed for reliability, modularity, and real-time performance.

## 🎯 Objective

Improve actuarial reserving and pricing precision by automating the ingestion, transformation, and modeling of claims data using a modern cloud-based data stack.

## 🧱 Tech Stack

| Component       | Technology                          |
|----------------|--------------------------------------|
| Ingestion       | AWS Lambda, API Gateway              |
| ETL             | AWS Glue (PySpark), Pandas, SQL      |
| Storage         | S3 (raw), Redshift (curated), Athena |
| Modeling        | Amazon SageMaker (GLM + XGBoost)     |
| Orchestration   | AWS Step Functions                   |
| QA & Monitoring | Great Expectations, AWS SNS          |

## 🔗 Data Sources

- **FNOL Feed**: Real-time claims intake via API
- **Payments/Reserves**: Historical claims payments and reserve data
- **Policy Information**: Coverage limits, insured characteristics
- **Actuarial LDF Tables**: Used for loss development modeling

## ⚙️ Pipeline Workflow

1. **Ingest** structured and semi-structured claim events (Lambda + API Gateway)
2. **Validate** schema, completeness, and formats
3. **Join** claims to policy and reserve data
4. **Calculate** actuarial metrics including LDFs, exposure, earned premiums
5. **Stage** enriched features for ML training
6. **Model** reserve forecasts using ensemble of GLM and XGBoost
7. **Monitor** quality and reliability with alerts and validation

## 📈 Output Metrics

- **Reserve Adequacy Score**: Delta between predicted and actual reserves
- **Forecast Lift**: Improvement vs. baseline GLM
- **Pipeline Latency**: <30 seconds (real-time), <1 hour (batch)

## ✅ QA & Monitoring

- Schema and business rule validation with **Great Expectations**
- **Retry logic** and **alerting** via AWS SNS
- Automated tests for critical joins and aggregations

## 📌 Use Cases

- Actuarial reserve forecasting and IBNR estimation
- Claims triage and fraud detection pre-filtering
- Enhanced pricing models with real-time claim signals

---

## 📂 Repository Structure

```bash
.
├── ingestion/             # Lambda functions and API Gateway configs
├── etl/                   # Glue jobs, PySpark scripts, data joins
├── modeling/              # ML training and inference logic (SageMaker)
├── config/                # Schema definitions, LDF tables
├── monitoring/            # Great Expectations, alerting setup
├── tests/                 # Unit and integration tests
└── README.md              # Project overview
