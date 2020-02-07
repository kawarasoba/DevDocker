FROM nvidia/cuda:10.1-cudnn7-devel-ubuntu16.04

MAINTAINER "@kawarasoba"

ARG PYTHON_VERSION=3.7

ENV PATH /opt/conda/bin:$PATH
# Changing PATH must be done before pip so that requirements.txt is available

RUN sed -i 's@archive.ubuntu.com@ftp.jaist.ac.jp/pub/Linux@g' /etc/apt/sources.list

RUN apt-get update \
     && apt-get upgrade -y \
     && apt-get install --no-install-recommends -y \
          curl \
          git-all \ 
          unzip \
     && apt-get clean\
     && rm -rf /var/lib/apt/lists/*

RUN curl -o ~/miniconda.sh -O  https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh　\
     && chmod +x ~/miniconda.sh \
     && ~/miniconda.sh -b -p /opt/conda \
     && rm ~/miniconda.sh \
     && /opt/conda/bin/conda install -y python=$PYTHON_VERSION ipython \
     && /opt/conda/bin/conda install -y pytorch torchvision cudatoolkit=10.0 -c pytorch \
     && /opt/conda/bin/conda install -y absl-py \
     && /opt/conda/bin/conda install -y opencv -c conda-forge \
     && /opt/conda/bin/conda clean -ya

RUN pip install tensorboardX \
     setuptools \
     numpy \
     pandas \
     cython \
     opencv-python \
     tqdm \
     matplotlib \
     albumentations \
     scikit-image \
     scikit-learn \
     segmentation_models_pytorch

RUN git clone https://github.com/cocodataset/cocoapi.git \
     && cd cocoapi/PythonAPI \
     && python setup.py build_ext install \
     && rm -rf build