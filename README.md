# DeepSeek R1 模型部署与应用

## Ollama

1. 确认自己的 GPU 是否支持：访问 [ollama - GPU 列表](https://github.com/ollama/ollama/blob/main/docs/gpu.md) 页面，看自己的电脑显卡配置，是否在 ollama 的支持列表中，如果不支持，ollama 会使用 CPU 进行推理，速度很慢。

2. 安装 ollama：访问 https://ollama.com/ 下载对应平台的版本，进行安装
3. 下载 `deepseek-r1 蒸馏模型`，模型地址 https://ollama.com/library/deepseek-r1

| 模型             | 大小 | 蒸馏模型               |
| :--------------- | :--- | :--------------------- |
| deepseek-r1:1.5b | 1.1G | Qwen2.5-Math-1.5B      |
| deepseek-r1:7b   | 4.7G | Qwen2.5-Math-7B        |
| deepseek-r1:8b   | 4.9G | Llama-3.1-8B           |
| deepseek-r1:14b  | 9G   | Qwen2.5-14B            |
| deepseek-r1:32b  | 19G  | Qwen2.5-32B            |
| deepseek-r1:70b  | 42G  | Llama-3.3-70B-Instruct |

## DeepSeek-R1 本地蒸馏模型

```shell
ollama run deepseek-r1:7b
```

## 使用 LobeChat Local 版本

1. 安装 docker
2. 直接在终端运行

```shell
docker run -d --name lobechat-local --net host --restart always \
    -e ACCESS_CODE=lobe666 \
    lobehub/lobe-chat:v1.49.15
```

浏览器访问 `localhost:3210` 做一些基本的设置，配置 deepseek-r1 模型，就可以使用了。

## DeepSeek-R1 满血模型

1. 使用 [DeepSeek 官方服务](https://www.deepseek.com/)
2. 使用 [硅基流动 SiliconFlow](https://cloud.siliconflow.cn/models)

## Demo

1. 天空为什么是蓝色的
2. 30 岁如何把握自己的人生，不碌碌无为，实现人生价值和阶级跨越
