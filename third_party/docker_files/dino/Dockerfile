FROM nvidia/cuda:11.8.0-cudnn8-devel-ubuntu20.04

# Non-interactive apt
ENV DEBIAN_FRONTEND=noninteractive

# Install system packages
RUN apt-get update && apt-get install -y \
    python3.8 python3.8-dev python3-pip \
    build-essential git wget libgl1-mesa-glx libglib2.0-0 && \
    rm -rf /var/lib/apt/lists/*

# Set Python 3.8 as default
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1

# Install pip
RUN python -m pip install --upgrade pip

# Install PyTorch 1.13.1 + cu118
RUN pip install torch==1.13.1+cu118 torchvision==0.14.1+cu118 --extra-index-url https://download.pytorch.org/whl/cu118

# Install DINO dependencies
RUN pip install numpy scipy matplotlib scikit-learn opencv-python timm

# Set working directory
WORKDIR /workspace

# Copy DINO code
COPY ./dino /workspace/dino

# Default command
CMD ["/bin/bash"]
