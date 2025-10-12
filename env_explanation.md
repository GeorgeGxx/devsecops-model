# ⚠️ Full explanation of this .env file for production environment ⚠️

## AWS CLI

### Install

- Windows: https://awscli.amazonaws.com/AWSCLIV2.msi

### Setup

```bash
aws configure # --profile <your_profile_name>
# Give the following inputs:
# AWS Access Key ID [None]: <your_access_key_id>
# AWS Secret Access Key [None]: <your_secret_access_key>
# Default region name [None]: us-east-1
# Default output format [None]: json
```

----

### Create .env file with WSL Ubuntu or manually inside root folder of your project

```bash
# Pwsh
New-Item -Path . -Name ".env" -ItemType "file"
# Bash
touch .env
```

### Add .env file to .gitignore

```bash
echo ".env" >> .gitignore
```

----

### Variables

- Database (PostgreSQL)
```bash
DATABASE_URL= 
# Connection URL to the PostgreSQL database, includes:
# Username: db_prod_user
# Password: <db_password>
# Host (AWS RDS): <db_cluster_endpoint_name>.<cluster_identifier_suffix>.<aws_region>. rds . amazonaws . com
# Port: 5432
# Database name: <db_name>

DB_MAX_CONNECTIONS=100 # Maximum number of simultaneous connections to the database.
DB_IDLE_TIMEOUT=30000 # Time in milliseconds (30 seconds) that a connection can stay idle before being closed.
```

- AWS Credentials
```bash
AWS_ACCESS_KEY_ID= / AWS_SECRET_ACCESS_KEY= # AWS access keys required to authenticate API calls to services (S3, RDS, Lambda, etc.).
AWS_REGION=us-east-1 # AWS region where the resources are deployed (Virginia North).
```

- Redis (Cache / Sessions)
```bash
REDIS_URL= # Redis connection URL.
REDIS_PASSWORD= # Password to access Redis.
REDIS_MAX_CONNECTIONS=50 # Maximum simultaneous connections to Redis.
```

- Payment Gateway / Email
```bash
STRIPE_SECRET_KEY= # Secret key to process payments with Stripe (live environment = production).
SENDGRID_API_KEY= # API Key to send emails using SendGrid.
```

- Cloudflare (CDN / DNS / Security)
```bash
CLOUDFLARE_API_TOKEN= # API token to manage Cloudflare services (DNS, DDoS Protection, CDN).
```

- Runtime Environment
```bash
NODE_ENV=production # Defines that the application is running in a production environment (affects logging, optimizations, etc.).
PORT=8080 # Port where the application will listen.
API_VERSION=v2 # API version being used.
LOG_LEVEL=info # Log verbosity level (can be debug, info, warn, error).
```

- Security / Authentication
```bash
JWT_SECRET= # Secret key used to sign and verify JSON Web Tokens (JWT).
SESSION_SECRET= # Secret key used to encrypt user sessions.
COOKIE_SECRET= # Secret key used to sign cookies.
```

- Rate Limiting (Anti-DDoS)
```bash
RATE_LIMIT_WINDOW=900000 # Time window (in milliseconds) to apply the request limit (900,000 ms = 15 minutes).
RATE_LIMIT_MAX_REQUESTS=1000 # Maximum number of allowed requests within that window per IP.
```

- Observability / Monitoring
```bash
ELASTICSEARCH_URL= # Endpoint to Elasticsearch (stores logs, search data).
KIBANA_URL= # Kibana dashboard to visualize logs and metrics from Elasticsearch.
SENTRY_DSN= # Sentry DSN to capture and report runtime errors in production.
NEW_RELIC_LICENSE_KEY= # New Relic license key for performance monitoring.
DATADOG_API_KEY= # Datadog API Key to send metrics and logs.
```

- CDN (Content Delivery Network)
```bash
CDN_URL= # Base URL of a CDN (CloudFront in this case) to serve static assets (images, CSS, JS, etc.).
```

#envfile #bestpractices #production #security #aws #postgresql #redis #monitoring #devops

----

-> [Environment File Cleanup](env_cleanup.md)

[Home](README.md) <-