FROM nvidia/cuda:10.0-cudnn7-devel
MAINTAINER @kawarasoba

ENV DEBIAN_FRONTEND=noninteractive
ENV LD_LIBRARY_PATH $LD_LIBRARY_PATH:"/usr/local/cuda-10.0/compat"
ENV LD_LIBRARY_PATH $LD_LIBRARY_PATH:"/usr/local/cuda-10.0/lib64"


RUN set -x && \
    apt-get update && apt-get install -y --no-install-recommends \
    sudo \
    git \
    wget && \ 
    #libopencv-dev python3-opencv && \
    rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y libssl-dev && \
    cd opt && \
    wget https://github.com/Kitware/CMake/releases/download/v3.16.6/cmake-3.16.6.tar.gz && \
    tar xvf cmake-3.16.6.tar.gz && \
    cd cmake-3.16.6 && \
    ./bootstrap && make && make install

RUN set -x && \
    apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    pkg-config \
    libgtk-3-dev \
    libavcodec-dev \
    libavformat-dev \
    libswscale-dev \
    libv4l-dev \
    libxvidcore-dev \
    libx264-dev \
    libjpeg-dev \
    libpng-dev \
    libtiff-dev \
    gfortran \
    openexr \
    libatlas-base-dev \
    python3-dev \
    python3-numpy \
    libtbb2 \
    libtbb-dev \
    libdc1394-22-dev

RUN cd root && \
    mkdir opencv_build && cd opencv_build && \
    git clone https://github.com/opencv/opencv.git && \
    git clone https://github.com/opencv/opencv_contrib.git && \
    cd opencv && \
    mkdir build && cd build && \
    cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_C_EXAMPLES=ON \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_GENERATE_PKGCONFIG=ON \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_build/opencv_contrib/modules \
    -D BUILD_EXAMPLES=ON .. && \
    make -j8 && \
    sudo make install

RUN cd root && \
    git clone https://github.com/AlexeyAB/darknet.git && \
    cd darknet && \
    sed -i -e 's/GPU=0/GPU=1/g' Makefile && \
    sed -i -e 's/CUDNN=0/CUDNN=1/g' Makefile && \
    sed -i -e 's/OPENCV=0/OPENCV=1/g' Makefile && \
    sed -i -e 's/NVCC=nvcc/NVCC=\/usr\/local\/cuda-10.0\/bin\/nvcc/g' Makefile && \
    sed -i -e 's/-gencode\ arch=compute_52,code=\[sm_52,compute_52]\ \\/-gencode\ arch=compute_52,code=\[sm_52,compute_52]/g' Makefile && \
    sed -i -e 's/-gencode\ arch=compute_61,code=\[sm_61,compute_61]/#-gencode\ arch=compute_61,code=\[sm_61,compute_61]/g' Makefile && \
    make && \
    cp darknet /usr/local/bin && \
    cd ..
    # && \
    #rm -rf darknet
    #wget https://pjreddie.com/media/files/darknet53.conv.74



#RUN apt-get update && apt-get install -y libssl-dev && \
#    cd opt && \
#    wget https://github.com/Kitware/CMake/releases/download/v3.16.6/cmake-3.16.6.tar.gz && \
#    tar xvf cmake-3.16.6.tar.gz && \
#    cd cmake-3.16.6 && \
#    ./bootstrap && make && make install

#RUN cd root && \ 
#    git clone https://github.com/AlexeyAB/darknet.git && \
#    cd darknet && \
#    mkdir build-release && \
#    cd build-release && \
#    cmake .. && \
#    make && \
#    make install && \ 
#    cd .. &&\
#    wget https://pjreddie.com/media/files/darknet53.conv.74