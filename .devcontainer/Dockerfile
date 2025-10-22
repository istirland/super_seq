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
