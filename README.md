
# 📈 Stock Market ETL Pipeline with Airflow, Spark, MinIO, PostgreSQL & Metabase

## 🔍 Project Overview

This project is a **real-world, production-grade ETL pipeline** built to showcase end-to-end **Data Engineering principles and practices** using modern open-source tools.

### 💡 What It Does

- Fetches **daily stock market data** from the **Yahoo Finance API**
- Stores the raw data in **object storage (MinIO)** as JSON
- Transforms that data using **Apache Spark**
- Converts it into clean, tabular format (CSV)
- Loads it into a **PostgreSQL data warehouse**
- Visualizes and explores the data in **Metabase**
- Sends real-time **Slack notifications** on success/failure

Every step is orchestrated using **Apache Airflow**, making this a fully **automated, resilient, and modular pipeline**.

---

## 🧠 Why It’s Useful for Data Engineering

This project is a **perfect microcosm** of the real-world responsibilities of a **Data Engineer**:

| 🔧 Component | 💬 Description |
|-------------|----------------|
| **Data Ingestion** | Connects to external APIs to simulate real-world data integration |
| **Workflow Orchestration** | Uses Airflow for task dependency management and scheduling |
| **Data Lake Layer** | Stores raw data in MinIO (compatible with AWS S3 APIs) |
| **Data Processing** | Transforms raw JSON to structured CSV with Apache Spark |
| **Data Warehouse Layer** | Loads transformed data into PostgreSQL for analytics |
| **Observability** | Sends Slack alerts for DAG success/failure |
| **BI Layer** | Connects Metabase for dashboarding and data exploration |

This is **not a toy project** — it's a **miniature production data platform** with clear architectural separation and extensibility.

---

## 🎯 Key Takeaways for Data Engineers

### ✅ Gain Experience In:
- Writing DAGs using **Apache Airflow decorators and operators**
- Building containerized **Spark jobs** with Docker
- Configuring **MinIO as an S3-compatible object store**
- Using **Astro SDK** to move data between storage and PostgreSQL
- Creating **custom Python + DockerOperator-based transformations**
- Building **end-to-end automation with observability** (Slack alerts)

### 🚀 Learn Industry Best Practices:
- **Modular project structure** (e.g., `dags/`, `include/`, `spark/`)
- Separating **raw vs. cleaned vs. BI-ready** data layers
- Handling **API response validation** with sensors
- Managing secrets and credentials using **Airflow Connections**
- Designing **scalable, fault-tolerant ETL pipelines**
- Using **Docker Compose** to simulate a mini data stack locally

---

## 🛠️ Tools and Technologies Used

| Layer            | Tool/Service                   |
|------------------|--------------------------------|
| Workflow         | Apache Airflow, Astro SDK      |
| Ingestion        | Yahoo Finance API              |
| Raw Storage      | MinIO (S3-compatible)          |
| Processing       | Apache Spark (via Docker)      |
| Data Warehouse   | PostgreSQL                     |
| BI & Dashboards  | Metabase                       |
| Notification     | Slack (via Airflow callbacks)  |
| Containerization | Docker, Docker Compose         |

---

## 📁 Project Structure

```bash
.
├── dags/
│   └── stock_market.py        # Main DAG definition
├── include/
│   ├── stock_market/
│   │   └── tasks.py           # Helper functions for ETL tasks
│   └── data/
│       └── minio/             # MinIO data volume
│       └── metabase/          # Metabase data volume
├── spark/
│   ├── notebook/
│   │   └── stock_transform.py # Spark application
│   ├── master/                # Spark master Docker config
│   └── worker/                # Spark worker Docker config
├── Dockerfile                 # For Spark job container
├── requirements.txt           # Python dependencies
├── airflow_settings.yaml      # Airflow connections & variables
└── docker-compose.yaml        # Entire orchestration stack
````

---

## ▶️ How to Run Locally (via Astro CLI)

1. **Start the project**

   ```bash
   astro dev start
   ```

2. **Trigger the DAG manually**

   * Access Airflow UI: [http://localhost:8080](http://localhost:8080)
   * Run the `stock_market` DAG

3. **Access Metabase**

   * [http://localhost:3000](http://localhost:3000)

4. **Check MinIO**

   * [http://localhost:9001](http://localhost:9001)
   * Username: `minio`, Password: `minio123`

---

## 🧪 Run Tests

```bash
pytest tests/
```

---

## 📊 Dashboards & Insights

Once the DAG completes:

* Processed stock prices for `NVDA` are available in PostgreSQL
* Metabase can be used to create dashboards such as:

  * Historical price trends
  * Daily volume spikes
  * Moving averages

---

## 🚨 Slack Alerts

Slack notifications are sent via Airflow's callback feature:

* On DAG success: ✅ “DAG succeeded”
* On DAG failure: ❌ “DAG failed”

Set your Slack webhook via Airflow connection: `slack`

---

## ✅ Final Thoughts

This project is an excellent **interview-ready portfolio piece** and offers **practical, hands-on skills** across the entire modern data pipeline stack. Whether you're learning or practicing, it’s built to **mirror real-world use cases**.
