# DE & Services in GCP


## GCP Services Summary Table

| **Category** | **Service** | **Purpose / What It Does** | **Why It’s Important / Why It Exists** |
|--------------|-------------|-----------------------------|-----------------------------------------|
| **Compute** | Compute Engine | Virtual Machines (IaaS) | Full VM control, useful for legacy or custom workloads. |
|              | App Engine | Fully managed app platform (PaaS) | Lets devs focus on code, auto-scales apps easily. |
|              | Cloud Functions | Event-driven, serverless functions | Ideal for light, quick tasks without server management. |
|              | Cloud Run | Run containers in a serverless way | Scalable, container-based workloads without infrastructure ops. |
|              | Kubernetes Engine (GKE) | Managed Kubernetes | Simplifies container orchestration, supports modern microservices. |
| **Storage & Databases** | Cloud Storage (GCS) | Object storage for files, media, logs | Durable, scalable storage for unstructured data and backups. |
|              | BigQuery | Serverless data warehouse | Massive scale analytics, fast SQL queries on big data. |
|              | Cloud SQL | Managed MySQL/PostgreSQL/SQL Server | Simplifies relational DB setup with automatic backups and scaling. |
|              | Cloud Spanner | Globally distributed SQL DB | Combines strong consistency with global availability. |
|              | Firestore | Serverless NoSQL for mobile/web | Real-time sync and offline mode, built for apps. |
|              | Bigtable | NoSQL wide-column DB | Scalable and performant for IoT/time-series/analytics. |
| **Data & Analytics** | Dataflow | Serverless stream & batch processing | Unified ETL and real-time data handling with autoscaling. |
|              | Dataproc | Managed Spark/Hadoop clusters | Low-cost big data processing, easy migration for legacy systems. |
|              | Pub/Sub | Messaging and event ingestion | Enables event-driven architecture and service decoupling. |
|              | Data Fusion | Drag-and-drop data integration | Simplifies ETL/ELT pipelines without writing code. |
|              | Dataprep | Visual data preparation | Cleans/structures data before analysis, no coding needed. |
| **AI / ML** | Vertex AI | ML model building and deployment | End-to-end ML lifecycle management, supports AutoML. |
|              | AI APIs (Vision, Speech, NLP) | Pre-trained ML models | Easy to add AI to apps without building models. |
|              | Cloud TPU | Accelerated hardware for ML training | Speeds up training for deep learning workloads. |
| **Networking & Security** | VPC | Virtual Private Cloud | Isolates and secures resources within your network. |
|              | Cloud Load Balancing | Global traffic distribution | Ensures high availability and scalability. |
|              | Cloud CDN | Content caching | Reduces latency and accelerates content delivery. |
|              | Cloud Armor | DDoS protection & WAF | Protects apps from internet-based threats. |
|              | IAM | Identity & Access Management | Role-based access control for resources. |
|              | Cloud KMS | Key management | Manages encryption keys for data security and compliance. |
| **DevOps & Monitoring** | Cloud Build | CI/CD pipeline | Automates build, test, and deployment workflows. |
|              | Artifact Registry | Secure container/artifact storage | Stores Docker images, Maven/Node packages, etc. |
|              | Deployment Manager | Infrastructure as Code (IaC) | Automates GCP resource provisioning via YAML templates. |
|              | Cloud Monitoring | Metrics and performance insights | Monitors uptime and system health. |
|              | Cloud Logging | Centralized log collection | Debugging, auditing, and analysis across services. |
| **Serverless & Eventing** | Cloud Functions | Functions triggered by events | Automates workflows, light back-end logic. |
|              | Eventarc | Event routing between GCP services | Builds loosely coupled event-driven architectures. |
| **Identity & Compliance** | Cloud Identity | User authentication & SSO | Integrates with enterprise identity systems. |
|              | Resource Manager | Org-level project/folder control | Manages GCP resources and billing hierarchy. |
|              | Cloud Audit Logs | API and data access tracking | Crucial for security auditing and compliance. |
