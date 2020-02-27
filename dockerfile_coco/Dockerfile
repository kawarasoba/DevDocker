FROM pytorch/pytorch:1.4-cuda10.1-cudnn7-runtime
MAINTAINER kawarasoba

CMD ["echo", "PyTorch-1.4 Customized"]

RUN set -x && \
    apt-get update && \
    apt-get install -y libglib2.0-0 libsm6 libxext6 libxrender1 libfontconfig1 zip git && \
    pip install numpy && \
    pip install pandas && \
    pip install opencv-python  && \
    pip install scikit-image &&  \
    pip install scikit-learn && \
    pip install matplotlib  && \
    pip install cython && \
    git clone https://github.com/cocodataset/cocoapi.git && \
    cd cocoapi/PythonAPI && \
    python setup.py build_ext install && \
    rm -rf build && \
    git clone https://github.com/NVIDIA/apex && \
    cd apex && \
    pip install -v --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./ && \
    cd ../ && \
    pip install tqdm && \
    pip install absl-py && \
    pip install tensorboardX && \
    pip install albumentations && \
    pip install efficientnet_pytorch && \
    pip install pretrainedmodels && \
    pip install segmentation_models_pytorch