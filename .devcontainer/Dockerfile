FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

# Install R (and dev headers) from Ubuntu repos; add anything else you need later
RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    r-base r-base-dev \
 && rm -rf /var/lib/apt/lists/*
