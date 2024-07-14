FROM python:3.11-alpine
ENV CONNECTOR_TYPE=EXTERNAL_IMPORT

RUN apk update && apk upgrade && \
    apk --no-cache add libmagic libxslt libxslt-dev libxml2 libxml2-dev

# Expose and entrypoint
COPY entrypoint.sh /
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

# Copy the connector
COPY src /opt/opencti-abuse-ssl

# Install Python modules
# hadolint ignore=DL3003
RUN apk --no-cache add git build-base && \
    cd /opt/opencti-abuse-ssl && \
    pip3 install --no-cache-dir -r requirements.txt && \
    apk del git build-base && \
    rm -rf /var/cache/apk/*
