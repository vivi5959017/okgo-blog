---
title: Ollama和Vllm部署模型方式！
description:   Model Scope。
pubDate: 2026-07-28
tags: ["ollama", "vllm"]
---
通过ollama安装模型到gpu卡服务

Ollama Linux安装：
通过vccode远程连接到云主机 auto dl
# 使用命令行前，请确保已经通过pip install modelscope 安装ModelScope。
打开文件夹进入root目录文件下，命令pwd，显示root目录下。
ls查看文件命令，显示autodl-pub  autodl-tmp  miniconda3  tf-logs
cd autodl-tmp命令切换到要下载的ollama包到该目录文件下
打开魔搭社区，搜索找到ollama linux安装，查看安装方式，复制以下命令下载：

modelscope download --model=modelscope/ollama-linux --local_dir ./ollama-linux --revision v0.17.5

# 运行ollama安装脚本
cd ollama-linux
sudo chmod 777 ./ollama-modelscope-install.sh
./ollama-modelscope-install.sh
开启ollama服务
ollama serve

另外打开一个终端窗口，ollama list查看下面有哪些模型
ollma list

进入ollama官网，选择需要下载的模型，已qwen3 0.6B为例，搜索模型，复制命令
ollama run qwen3:0.6b  进行模型安装
安装完毕后，模型已经开始服务，你可以进行对话。

如果要推出模型服务，输入/exit可退出对话

ollama list查看ollama下已存在该模型
root@autodl-container-f8b04497a5-bb8c1f0a:~# ollama list
NAME          ID              SIZE      MODIFIED      
qwen3:0.6b    7df6b6e09427    522 MB    5 minutes ago 

备注：ollama只适合个人部署，主要会做模型压缩。这里看到qwen大小才522MB， 而原始该模型GGUF 大小为1.5GB. 主要ollama做了量化。
只支持GGUF格式

如果要通过modelscope 下载qwen模型GGUF，进入官网找到模型的下载命令
终端下载：
在下载前，请先通过如下命令安装ModelScopepip install modelscope
下载模型库modelscope download --model Qwen/Qwen3.6-27B
modelscope download --model Qwen/Qwen3.6-27B README.md --local_dir ./dir


SDK下载通过vs code在云主机文件下autodl-tmp下心创建python文件，替换如下：
#模型下载
from modelscope import snapshot_download
model_dir = snapshot_download('Qwen/Qwen3.6-27B')

Vllm支持page attention机制和动态批处理，也支持量化

进入vllm官网，找到安装文档，vllm对硬件有些要求
GPU：算力 7.5 或更高（例如 T4、RTX20xx、A100、L4、H100、B200 等）
conda安装方式：
需要先创建虚拟环境，在该环境下安装：
conda create -n vllm python=3.12 -y  创建虚拟环境
conda init
conda activate vllm  激活
pip install vllm  安装

vllm serve /root/.cache/modelscope/models   模型具体存放路径         激活模型服务


模型下载   终端命令

先安装modelscope    
pip install modelscope
modelscope download --model Qwen/Qwen3.5-4B

#模型下载    SDK
from modelscope import snapshot_download
model_dir = snapshot_download('Qwen/Qwen3.5-4B')

