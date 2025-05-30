FROM nvidia/cuda:11.8.0-cudnn8-devel-ubuntu20.04

# Non-interactive apt
ENV DEBIAN_FRONTEND=noninteractive

# Install system dependencies
RUN apt-get update && apt-get install -y \
    python3.8 python3.8-dev python3-pip \
    build-essential git wget libgl1-mesa-glx libglib2.0-0 && \
    rm -rf /var/lib/apt/lists/*

# Set Python 3.8 as default
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1

# Install pip
RUN python -m pip install --upgrade pip

# Install PyTorch 1.10.0 + cu113 (stable for many stereo repos)
RUN pip install torch==1.10.0+cu113 torchvision==0.11.1+cu113 --extra-index-url https://download.pytorch.org/whl/cu113

# Install Stereo dependencies
RUN pip install numpy opencv-python matplotlib pillow scikit-image tqdm

# Set working directory
WORKDIR /workspace

# Copy Stereo module code
# COPY ./stereo /workspace/stereo

# Default command
CMD ["/bin/bash"]
