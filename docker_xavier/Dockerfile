# Nobrainer container specification.

# Use "gpu-py3" to build GPU-enabled container and "py3" for non-GPU container.
ARG TF_ENV="gpu-py3"
FROM tensorflow/tensorflow:1.10.0-${TF_ENV}

WORKDIR /opt/nobrainer
COPY . .
RUN apt-get update -qq \
    && apt-get install -yq --no-install-recommends imagemagick \
    && apt-get clean \
    && pip3 install --upgrade pip \
    && pip3 install --no-cache-dir \
        https://www.github.com/keras-team/keras-contrib/tarball/master \
        scikit-image \
        seaborn \
        opencv-python \
        floodfill \
        numba \
        gym \
        torch \
        torchvision \
        tensorboardx \
    && apt-get install -yq locales \
    && export LC_ALL="en_US.UTF-8" \
    && export LC_CTYPE="en_US.UTF-8" \
    && dpkg-reconfigure locales \
    && apt update && apt install -y libsm6 libxext6 libxrender-dev \
    && rm -rf ~/.cache/pip/* \
    && useradd --no-user-group --create-home --shell /bin/bash neuro

ENV PATH="$PATH:/opt/nobrainer/bin"

USER neuro
WORKDIR /home/neuro

LABEL maintainer="Syed Suleman Abbas Zaidix <ssazaidi@mit.edu>"
