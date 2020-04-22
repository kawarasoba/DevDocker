FROM pytorch/pytorch:1.4-cuda10.1-cudnn7-runtime
MAINTAINER @kawarasoba

RUN set -x && \
    apt-get update && \
    apt-get install -y cmake zip git wget && \
    pip install opencv-python

RUN pip install cmake && \
    git clone https://github.com/AlexeyAB/darknet.git && \
    cd darknet && \
    mkdir build-release && \
    cd build-release && \
    cmake .. && \
    make && \
    make install

RUN cd darknet && \
    wget https://pjreddie.com/media/files/darknet53.conv.74