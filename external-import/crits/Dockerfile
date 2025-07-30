FROM python:3.11-alpine
RUN apk add --no-cache libmagic libxslt libxslt-dev libxml2 libxml2-dev

ENV CONNECTOR_TYPE=EXTERNAL_IMPORT
ARG CONNECTOR_NAME=crits.py

WORKDIR /opt/opencti-connector-${CONNECTOR_NAME}
CMD ["python", "crits.py"]

COPY src/requirements.txt /opt/opencti-connector-${CONNECTOR_NAME}
RUN pip3 install --no-cache-dir -r requirements.txt
COPY src /opt/opencti-connector-${CONNECTOR_NAME}
