FROM nvidia/cuda:11.8.0-cudnn8-devel-ubuntu20.04

# Set non-interactive mode for apt
ENV DEBIAN_FRONTEND=noninteractive

# Install core utilities
RUN apt-get update && apt-get install -y \
    python3.8 python3.8-dev python3-pip \
    build-essential git wget libgl1-mesa-glx libglib2.0-0 && \
    rm -rf /var/lib/apt/lists/*

# Set Python 3.8 as default
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1

# Install pip and core Python dependencies
RUN python -m pip install --upgrade pip

# Install compatible PyTorch + TorchVision for CUDA 11.8
RUN pip install torch==2.0.1+cu118 torchvision==0.15.2+cu118 --extra-index-url https://download.pytorch.org/whl/cu118

# Install other GSplat dependencies
RUN pip install plyfile open3d numpy open3d matplotlib scikit-image tqdm

# Set working directory
WORKDIR /workspace

# Copy GSplat source code into container (adjust as needed)
COPY ../../gaussian-splatting /workspace/gsplat

# Default command
CMD ["/bin/bash"]
