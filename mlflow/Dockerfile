FROM python:3.11-slim-buster
ARG MLFLOW_TRACKING_USERNAME
ARG MLFLOW_TRACKING_PASSWORD

COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt

COPY basic_auth.ini /tmp/basic_auth.ini
RUN sed -i 's/{{your_admin_username}}/'$MLFLOW_TRACKING_USERNAME'/g' /tmp/basic_auth.ini
RUN sed -i 's/{{your_admin_password}}/'$MLFLOW_TRACKING_PASSWORD'/g' /tmp/basic_auth.ini

RUN mv /tmp/basic_auth.ini /usr/local/lib/python3.11/site-packages/mlflow/server/auth/basic_auth.ini
