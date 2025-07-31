# syntax=docker/dockerfile:1

ARG PYTHON_VERSION=3.12.5
FROM python:${PYTHON_VERSION}-bookworm AS base

# Prevents Python from writing pyc files.
ENV PYTHONDONTWRITEBYTECODE=1

# Keeps Python from buffering stdout and stderr to avoid situations where
# the application crashes without emitting any logs due to buffering.
ENV PYTHONUNBUFFERED=1

# Where to install Playwright browsers
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

WORKDIR /app

RUN pip install --no-cache-dir pycti==6.7.8

# Install dependencies
# Avoid an image layer for those files.
RUN --mount=type=bind,source=src/requirements.txt,target=requirements.txt \
    python -m pip install --no-cache-dir -r requirements.txt

# Execute the connector
CMD [ "python", "main.py" ]

# Install Playwright and its dependencies
# Then clean up unnecessary files
RUN playwright install chromium --with-deps --only-shell && \
    apt-get clean && rm -rf /var/lib/apt/lists/* && \
    rm -rf /root/.cache && \
    find . -type d -name __pycache__ -exec rm -rf {} + && \
    find . -type f -name '*.pyc' -delete

# Copy the connector
COPY src .

ENV CONNECTOR_TYPE=INTERNAL_ENRICHMENT
