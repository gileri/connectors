FROM python:3.11-alpine
RUN apk add --no-cache libmagic libxslt libxslt-dev libxml2 libxml2-dev

ENV CONNECTOR_TYPE=INTERNAL_EXPORT_FILE
ARG CONNECTOR_NAME=export-report-pdf

WORKDIR /opt/opencti-connector-${CONNECTOR_NAME}
CMD ["python", "export-report-pdf.py"]

RUN apk --no-cache add zlib-dev tiff-dev jpeg-dev openjpeg-dev zlib-dev \
    freetype-dev lcms2-dev libwebp-dev tcl-dev tk-dev harfbuzz-dev fribidi-dev libimagequant-dev \
    libxcb-dev libpng-dev pango weasyprint

COPY src/requirements.txt /opt/opencti-connector-${CONNECTOR_NAME}
RUN pip3 install --no-cache-dir -r requirements.txt
COPY src /opt/opencti-connector-${CONNECTOR_NAME}
