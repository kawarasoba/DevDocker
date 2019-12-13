FROM nvidia/cuda:10.1-cudnn7-devel-ubuntu16.04

MAINTAINER "@kawarasoba"

ARG PYTHON_VERSION=3.7

ENV PATH /opt/conda/bin:$PATH
# This must be done before pip so that requirements.txt is available

RUN apt-get update && apt-get install -y --no-install-recommends curl && \
     rm -rf /var/lib/apt/lists/*

RUN curl -o ~/miniconda.sh -O  https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh  && \
     chmod +x ~/miniconda.sh && \
     ~/miniconda.sh -b -p /opt/conda && \
     rm ~/miniconda.sh && \
     /opt/conda/bin/conda install -y python=$PYTHON_VERSION ipython && \
     /opt/conda/bin/conda install -y pytorch torchvision cudatoolkit=10.0 -c pytorch && \
     /opt/conda/bin/conda install -y absl-py && \
     /opt/conda/bin/conda install -y opencv -c conda-forge && \
     /opt/conda/bin/conda clean -ya

RUN pip install tensorboardX \
     numpy \
     pandas \
     opencv-python \
     tqdm \
     matplotlib \
     albumentations \
     pretrainedmodels \
     efficientnet_pytorch \
     scikit-image \
     scikit-learn