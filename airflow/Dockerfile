FROM apache/airflow:slim-latest

# Install required system/builder packages if needed (for compiling requirements)
USER airflow
ARG AIRFLOW_VERSION=3.1.2
# Now install core Python dependencies for Postgres+Celery
RUN pip install --no-cache-dir \
    asyncpg \
    psycopg2-binary \
    apache-airflow[celery]==${AIRFLOW_VERSION} \
    'apache-airflow-providers-postgres' \
    'apache-airflow-providers-redis' \
    'apache-airflow-providers-fab'

# Add any further providers/extras you need for your DAG integrations, e.g.:
# RUN pip install --no-cache-dir apache-airflow-providers-amazon apache-airflow-providers-google
