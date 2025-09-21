FROM python:3.11-slim

ENV DEBIAN_FRONTEND=noninteractive

# System deps for GUI and tooling
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    openssh-client \
    procps \
    wget \
 && rm -rf /var/lib/apt/lists/*

# uv (Python package manager) binary
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

WORKDIR /workspaces/ml_zoomcamp

# Use project venv when present
ENV PATH="/workspaces/ml_zoomcamp/.venv/bin:${PATH}"

# Auto-activate venv in interactive shells
RUN echo 'if [ -f /workspaces/ml_zoomcamp/.venv/bin/activate ]; then . /workspaces/ml_zoomcamp/.venv/bin/activate; fi' >> /root/.bashrc