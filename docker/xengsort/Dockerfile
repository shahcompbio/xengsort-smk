FROM continuumio/miniconda3:24.7.1-0
LABEL authors="preskaa"

RUN git clone https://gitlab.com/genomeinformatics/xengsort.git

RUN cd xengsort && \
    conda create --name xengsort -c conda-forge -c bioconda -y \
    python>=3.12 \
    numpy>=1.24 \
    numba>=0.57 \
    pytest \
    pigz \
    jsonargparse

# Ensure conda environments can be used in non-interactive shells
SHELL ["conda", "run", "-n", "xengsort", "/bin/bash", "-c"]

# Activate the xengsort environment and install the package
RUN /bin/bash -c "source activate /opt/conda/envs/xengsort && cd xengsort && pip install -e ."

## Set the default command to activate the xengsort environment
SHELL ["conda", "run", "-n", "xengsort", "/bin/bash", "-c"]

ENV PATH="$PATH:/opt/conda/envs/xengsort/bin"