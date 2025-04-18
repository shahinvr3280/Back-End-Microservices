# Shahidi.VR Secure Messaging Back-End

This repository provides:

1. **telemetry-api** (Go 1.22): A high‑concurrency HTTP API that ingests real‑time telemetry (head‑pose and ECG) and writes to Amazon Timestream.
2. **analytics-service** (Python 3.11 + FastAPI): Periodically reads raw telemetry from Timestream and session logs from Aurora PostgreSQL 15, computes analytics (e.g. HRV, session metrics), and exposes JSON endpoints.

## Prerequisites
- **Go 1.22** installed (https://go.dev/dl/)
- **Python 3.11** installed
- AWS credentials with write access to Timestream
- Aurora PostgreSQL 15 endpoint, credentials
- `GIT_ROOT` directory structure as above

## Configuration (environment variables)

Create a `.env` file in the project root with:

```dotenv
# AWS Timestream
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=YOUR_KEY
AWS_SECRET_ACCESS_KEY=YOUR_SECRET
TIMESTREAM_DATABASE=ShahidiTelemetry
TIMESTREAM_TABLE=SessionData

# Aurora PostgreSQL
PG_HOST=aurora-instance.cluster-xxxxxxxx.us-east-1.rds.amazonaws.com
PG_PORT=5432
PG_USER=youruser
PG_PASSWORD=yourpassword
PG_DATABASE=shahidi_analytics
