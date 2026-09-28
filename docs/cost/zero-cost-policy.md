============================================================
COST LOCK
============================================================

PROJECT BUDGET = 0 THB.

Never run or recommend commands that can create billable
cloud resources without stopping first.

Do not run:

terraform apply

against AWS / Azure / GCP.

Do not create:

EKS
AKS
GKE
EC2
RDS
NAT Gateway
Load Balancer
public IP
paid database
paid AI endpoint
paid hosted service

unless I explicitly say:

"I approve spending money."

Default replacement:

AWS/Azure/GCP → Local simulation
EKS → kind
RDS → PostgreSQL Docker
SQS → NATS/RabbitMQ
S3 → MinIO
CloudWatch → OpenTelemetry stack
Bedrock/OpenAI → Ollama
ALB → Nginx/Traefik

Learning cloud concepts is mandatory.
Paying for cloud resources is not.