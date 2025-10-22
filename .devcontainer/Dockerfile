# --- system deps helpful for many Bioc packages ---
RUN apt-get update && apt-get install -y --no-install-recommends \
    r-base r-base-dev build-essential gfortran \
    libcurl4-openssl-dev libxml2-dev libssl-dev \
    zlib1g-dev libbz2-dev liblzma-dev libzstd-dev \
    libpng-dev libjpeg-dev libtiff5-dev \
    libfontconfig1-dev libfreetype6-dev libharfbuzz-dev libfribidi-dev \
    libhdf5-dev libgit2-dev \
 && rm -rf /var/lib/apt/lists/*

# --- R packages (pin Bioc 3.18, set repos, parallel compile) ---
RUN R -q -e 'install.packages("BiocManager", repos="https://cloud.r-project.org"); \
             options(repos = BiocManager::repositories()); \
             options(Ncpus = max(1, parallel::detectCores()-1)); \
             BiocManager::install(version="3.18", ask=FALSE, update=FALSE); \
             BiocManager::install(c("DESeq2","DEXSeq","bambu","edgeR","tximport","BiocParallel"), ask=FALSE, update=FALSE); \
             install.packages(c("tidyverse","data.table"), repos="https://cloud.r-project.org")'
