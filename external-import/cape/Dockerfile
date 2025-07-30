FROM python:3.11-alpine
RUN apk add libmagic libxslt libxslt-dev libxml2 libxml2-dev

ENV CONNECTOR_TYPE=EXTERNAL_IMPORT
ARG CONNECTOR_NAME=cape

COPY src /opt/opencti-connector-${CONNECTOR_NAME}
WORKDIR /opt/opencti-connector-${CONNECTOR_NAME}
CMD ["python", "main.py"]

RUN pip3 install --no-cache-dir -r requirements.txt
