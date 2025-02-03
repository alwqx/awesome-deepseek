# DeepSeek R1 模型部署与应用

## Ollama

1. 确认自己的 GPU 是否支持：访问 [ollama - GPU 列表](https://github.com/ollama/ollama/blob/main/docs/gpu.md) 页面，看自己的电脑显卡配置，是否在 ollama 的支持列表中，如果不支持，ollama 会使用 CPU 进行推理，速度很慢。

| Compute Capability | Family           | Cards                                                                                                                         |
| ------------------ | ---------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| 8.9                | GeForce RTX 40xx | `RTX 4090` `RTX 4080 SUPER` `RTX 4080` `RTX 4070 Ti SUPER` `RTX 4070 Ti` `RTX 4070 SUPER` `RTX 4070` `RTX 4060 Ti` `RTX 4060` |
| 8.6                | GeForce RTX 30xx | `RTX 3090 Ti` `RTX 3090` `RTX 3080 Ti` `RTX 3080` `RTX 3070 Ti` `RTX 3070` `RTX 3060 Ti` `RTX 3060` `RTX 3050 Ti` `RTX 3050`  |
| 7.5                | GeForce GTX/RTX  | `GTX 1650 Ti` `TITAN RTX` `RTX 2080 Ti` `RTX 2080` `RTX 2070` `RTX 2060`                                                      |

| Family         | Cards and accelerators                                                                                                                         |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| AMD Radeon RX  | `7900 XTX` `7900 XT` `7900 GRE` `7800 XT` `7700 XT` `7600 XT` `7600` `6950 XT` `6900 XTX` `6900XT` `6800 XT` `6800` `Vega 64` `Vega 56`        |
| AMD Radeon PRO | `W7900` `W7800` `W7700` `W7600` `W7500` `W6900X` `W6800X Duo` `W6800X` `W6800` `V620` `V420` `V340` `V320` `Vega II Duo` `Vega II` `VII` `SSG` |
| AMD Instinct   | `MI300X` `MI300A` `MI300` `MI250X` `MI250` `MI210` `MI200` `MI100` `MI60` `MI50`                                                               |

2. 安装 ollama：访问 https://ollama.com/ 下载对应平台的版本，进行安装
3. 运行 `deepseek-r1 蒸馏模型`

## DeepSeek-R1 本地蒸馏模型

满血版 R1 模型参数有 671B，消费级显卡内存太小了，无法运行。

这里我们运行通过 R1 蒸馏后的支持推理的模型，模型地址 https://ollama.com/library/deepseek-r1

| 模型             | 大小 | 蒸馏模型               |
| :--------------- | :--- | :--------------------- |
| deepseek-r1:1.5b | 1.1G | Qwen2.5-Math-1.5B      |
| deepseek-r1:7b   | 4.7G | Qwen2.5-Math-7B        |
| deepseek-r1:8b   | 4.9G | Llama-3.1-8B           |
| deepseek-r1:14b  | 9G   | Qwen2.5-14B            |
| deepseek-r1:32b  | 19G  | Qwen2.5-32B            |
| deepseek-r1:70b  | 42G  | Llama-3.3-70B-Instruct |

**根据自己的显卡内存大小，选择合适的参数模型，这里笔者选择 14b**

```shell
# 1. 下载模型权重
ollama pull deepseek-r1:14b
# 2. 运行模型
ollama run deepseek-r1:14b
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
2. 使用 [硅基流动 SiliconFlow](https://cloud.siliconflow.cn/models)，可以使用我的邀请连接注册，免费赠送 2000 万 tokens https://cloud.siliconflow.cn/i/kprJTcyG

## Demo

1. 天空为什么是蓝色的
2. 30 岁如何把握自己的人生，不碌碌无为，实现人生价值和阶级跨越
