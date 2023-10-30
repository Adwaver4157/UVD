FROM nvidia/cudagl:11.3.0-devel-ubuntu20.04

SHELL ["/bin/bash", "-c"]

RUN apt-get update && apt-get install -y \
    sudo \
    wget \
    git \
    vim \
    libosmesa6-dev \
    libgl1-mesa-glx \
    libglfw3 \
    libjpeg-dev \
    zlib1g-dev \
    libtiff-dev \
    patchelf \
    x11-apps

WORKDIR /opt

RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh && \
    sh Miniconda3-latest-Linux-x86_64.sh -b -p /opt/miniconda3 && \
    rm -r Miniconda3-latest-Linux-x86_64.sh

ENV PATH /opt/miniconda3/bin:$PATH

WORKDIR /app

RUN pip install --upgrade pip && \
    conda create -n uvd python==3.9 -y && \
    conda init && \
    echo "conda activate uvd" >> ~/.bashrc

ENV CONDA_DEFAULT_ENV uvd && \
    PATH /opt/conda/envs/uvd/bin:$PATH

# RUN git clone https://github.com/facebookresearch/vip.git
# RUN cd vip && pip install -e .
# RUN python -c "from vip import load_vip; vip = load_vip()"
