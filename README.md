# GS2Mesh-AIPaper
Implementation of GS2Mesh Code.
# 🧩 Gs2Mesh Docker Pipeline

This repository packages the [Gs2Mesh](https://github.com/limacv/Gs2Mesh) pipeline into a modular, Dockerized setup for easy deployment and integration with other 3D reconstruction stages like stereo depth estimation and shape completion.

## 📦 What's Included

- Dockerfile for setting up Gs2Mesh and dependencies
- Scripts for running the pipeline end-to-end
- Notebook(s) for testing with custom inputs
- Output-ready directory structure
- Planned integration with point cloud completion methods (e.g., SeedFormer, PCN)

---

## 🚀 Getting Started

### Prerequisites

- Docker
- Python 3.8+
- CUDA 11.8 (if running with GPU support)

### 🛠 Setup

Clone this repo:
```bash
git clone https://github.com/
cd gs2mesh-docker-pipeline
```
Build Docker 
```bash

docker build -t gs2mesh-pipeline
```

Run the Container:
```bash
docker run --gpus all -it --rm -v $(pwd):/workspace gs2mesh-pipeline
```

Run Your Pipeline Inside the Container:
```bash
cd /workspace
python run_pipeline.py
# or open custom_data.ipynb
```
🧾 Credits
This work builds upon the excellent open-source project Gs2Mesh by @limacv, which generates watertight 3D meshes from sparse point clouds using signed distance fields.

Original Gs2Mesh repo: https://github.com/limacv/Gs2Mesh

License: BSD 3-Clause License

Any modifications in this repo are experimental and meant for testing and extension purposes only.

🧪 Status

- ✅ Dockerized core pipeline
- ✅ Working with synthetic stereo depth
- 🔄 Integrating point completion
- 📌 Planned: Full stereo → mesh pipeline with fill-in

🤝 Contributions
If you'd like to contribute to this repo or upstream improvements, feel free to open an issue or submit a pull request.

📄 License
This repo uses the same BSD 3-Clause License as the original Gs2Mesh project. Please respect the original licensing term
