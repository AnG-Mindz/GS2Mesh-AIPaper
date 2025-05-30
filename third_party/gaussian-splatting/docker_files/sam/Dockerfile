FROM nvidia/cuda:11.8.0-cudnn8-devel-ubuntu20.04

# Non-interactive apt
ENV DEBIAN_FRONTEND=noninteractive

# Install system dependencies
RUN apt-get update && apt-get install -y \
    python3.10 python3.10-dev python3-pip \
    build-essential git wget libgl1-mesa-glx libglib2.0-0 && \
    rm -rf /var/lib/apt/lists/*

# Set Python 3.10 as default
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.10 1

# Install pip and base Python tools
RUN python -m pip install --upgrade pip

# Install compatible PyTorch + TorchVision for CUDA 11.8
RUN pip install torch==2.1.0+cu118 torchvision==0.16.0+cu118 --extra-index-url https://download.pytorch.org/whl/cu118

# Install Segment Anything dependencies
RUN pip install numpy opencv-python matplotlib scikit-image onnx onnxruntime

# Set working directory
WORKDIR /workspace

# Copy SAM-2 source code into container (adjust path accordingly)
COPY ./sam /workspace/sam

# Default command
CMD ["/bin/bash"]
