# Docker MiniCPM

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