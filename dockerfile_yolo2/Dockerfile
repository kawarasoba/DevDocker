FROM daisukekobayashi/darknet:gpu-cv
RUN set -x && \
    apt-get update && apt-get install -y --no-install-recommends \
    sudo \
    wget \
    unzip && \
    rm -rf /var/lib/apt/lists/*

RUN wget https://pjreddie.com/media/files/darknet53.conv.74