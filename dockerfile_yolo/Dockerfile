#FROM nvidia/cuda:8.0-cudnn5-devel

FROM nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04
MAINTAINER @kawarasoba

ENV DEBIAN_FRONTEND=noninteractive
ENV LD_LIBRARY_PATH $LD_LIBRARY_PATH:"/usr/local/cuda-10.0/compat"

RUN set -x && \
    apt-get update && apt-get install -y --no-install-recommends \
    sudo \
    git \
    wget \
    libopencv-dev

RUN apt-get update && apt-get install -y libssl-dev && \
    cd opt && \
    wget https://github.com/Kitware/CMake/releases/download/v3.16.6/cmake-3.16.6.tar.gz && \
    tar xvf cmake-3.16.6.tar.gz && \
    cd cmake-3.16.6 && \
    ./bootstrap && make && make install

RUN cd root && \ 
    git clone https://github.com/AlexeyAB/darknet.git && \
    cd darknet && \
    mkdir build-release && \
    cd build-release && \
    cmake .. && \
    make && \
    make install && \ 
    cd .. &&\
    wget https://pjreddie.com/media/files/darknet53.conv.74

WORKDIR /root/darknet