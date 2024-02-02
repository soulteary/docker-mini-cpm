# Docker MiniCPM

## 在线体验

Colab: [https://colab.research.google.com/drive/1tJcfPyWGWA5HezO7GKLeyeIso0HyOc0l?usp=sharing](https://colab.research.google.com/drive/1tJcfPyWGWA5HezO7GKLeyeIso0HyOc0l?usp=sharing)

## 模型支持

- [x] HuggingFace SFT / DPO (bf16/float32)
- [ ] vllm (WIP)



## 完整教程

WIP

## 容器构建

构建运行环境：

```bash
docker build -t soulteary/minicpm:hf . -f docker/Dockerfile.hf
```

如果你希望更快一些，可以配置国内镜像来做加速：

```bash
docker build --build-arg=USE_CHINA_MIRROR=true -t soulteary/minicpm:hf . -f docker/Dockerfile.hf
```

## 快速运行

简单运行：

```bash
docker run --rm -it -p 7860:7860 --gpus all --ipc=host --ulimit memlock=-1 -v `pwd`/models:/app/models soulteary/minicpm:hf python app.py --model_path=./models/OpenBMB/MiniCPM-「具体模型型号」/ --server_name=0.0.0.0
```

更高效运行，运行 float32 版本的 HF 模型。

```bash
docker run --rm -it -p 7860:7860 --gpus all --ipc=host --ulimit memlock=-1 -v `pwd`/models:/app/models soulteary/minicpm:hf python app.py --model_path=./models/OpenBMB/MiniCPM-2B-dpo-fp32/ --server_name=0.0.0.0 --torch_dtype=float32
```