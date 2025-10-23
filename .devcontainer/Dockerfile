FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

# Install R (and dev headers) from Ubuntu repos; add anything else you need later
RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    r-base r-base-dev \
 && rm -rf /var/lib/apt/lists/*

# Install CRAN & Bioconductor packages
RUN R -q -e 'install.packages(c("BiocManager","remotes"), repos="https://cloud.r-project.org")' \
 && R -q -e 'BiocManager::install(c("DESeq2","edgeR","tximport","BiocParallel"), ask=FALSE, update=FALSE)' \
 && R -q -e 'install.packages(c("tidyverse","data.table"), repos="https://cloud.r-project.org")'
RUN R -q -e 'BiocManager::install("DEXSeq", dependencies=TRUE, ask=FALSE, update=FALSE)'
RUN R -q -e 'BiocManager::install("bambu",  dependencies=TRUE, ask=FALSE, update=FALSE)'
RUN R -q -e 'install.packages(c("tidyverse","data.table"), repos="https://cloud.r-project.org")'

# modkit v0.5.1 (latest as of Oct 2025)
ARG MODKIT_VERSION=0.5.1
RUN curl -L -o /tmp/modkit.tar.gz \
      https://github.com/nanoporetech/modkit/releases/download/v${MODKIT_VERSION}/modkit_linux_x86_64_v${MODKIT_VERSION}.tar.gz \
    && tar -xzf /tmp/modkit.tar.gz -C /usr/local/bin --strip-components=1 \
    && rm /tmp/modkit.tar.gz
