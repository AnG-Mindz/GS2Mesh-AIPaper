FROM nvidia/cuda:11.8.0-cudnn8-devel-ubuntu20.04

ENV DEBIAN_FRONTEND=noninteractive

# Install system dependencies
RUN apt-get update && apt-get install -y \
    python3.8 python3.8-dev python3-pip \
    build-essential git wget unzip \
    libglib2.0-0 libsm6 libxext6 libxrender1 \
    && rm -rf /var/lib/apt/lists/*

# Set Python 3.8 as default
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1

# Upgrade pip
RUN python -m pip install --upgrade pip

# Install torch + torchvision for CUDA 11.8
RUN pip install torch==2.3.1 torchvision==0.18.1 --extra-index-url https://download.pytorch.org/whl/cu118

# Install REQUIRED_PACKAGES (with updated versions where applicable)
# RUN pip install numpy==2.0.0 tqdm==4.66.2 hydra-core==1.3.2 iopath==0.1.10 pillow==10.3.0

# Install demo dependencies (EXTRA_PACKAGES["demo"]) with updated versions
# RUN pip install matplotlib==3.8.4 jupyter==1.0.0 opencv-python==4.9.0.80

# Set working directory
WORKDIR /workspace

# Copy SAM-2 source code

#COPY third_party/segment-anything-2 /workspace/sam

# Create SageMaker input/output folders
# RUN mkdir -p /opt/ml/input /opt/ml/output

# Default command
CMD ["/bin/bash"]
