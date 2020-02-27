FROM pytorch/pytorch:1.4-cuda10.1-cudnn7-runtime
MAINTAINER kawarasoba

RUN set -x && \
    apt-get update && \
    apt-get install -y libglib2.0-0 libsm6 libxext6 libxrender1 libfontconfig1 zip git && \
    pip install numpy && \
    pip install pandas && \
    pip install opencv-python  && \
    pip install scikit-image &&  \
    pip install scikit-learn && \
    pip install matplotlib  && \
    pip install tqdm && \
    pip install absl-py && \
    pip install tensorboardX && \
    pip install albumentations && \
    pip install efficientnet_pytorch && \
    pip install pretrainedmodels && \
    git clone https://github.com/NVIDIA/apex && \
    cd apex && \
    pip install -v --no-cache-dir ./ && \
    cd ../