# InternLM with Long Context

## 使用 InternLM2.5-1M 进行文档chat

这部分内容提供了如何使用 [InternLM2.5-7B-Chat-1M]() 并给定文档进行交流的简要概述。特别是对于长文本输入，我们强烈推荐使用 [LMDeploy]() 进行模型部署，以获得最佳性能。

## 支持的文档类型

目前，我们支持 PDF、TXT 和 Markdown 文件，很快会支持更多文件类型！

- TXT 和 Markdown 文件：可以直接处理，无需转换。
- PDF 文件：我们开发了 [Magic-Doc](https://github.com/magicpdf/Magic-Doc)，一个轻量级开源工具，可以将多种文件类型转换成 Markdown。

## 安装

开始安装所需的软件包：
```bash
pip install "fairy-doc[cpu]"
pip install streamlit
pip install lmdeploy
```

## 部署模型

[下载](xxx)我们的模型。

使用以下命令部署模型。您可以指定 `session-len`（sequence- length）和 `server-port`（服务端口）。

```bash
lmdeploy serve api_server {path_to_hf_model} \
--model-name internlm2-chat \
--session-len 65536 \
--server-port 8000
```

## 启动 Streamlit 演示

```bash
streamlit run long_context/doc_chat_demo.py \
-- --base_url http://0.0.0.0:8000/v1
```

您可以根据需要指定端口。如果您在本地运行演示，URL 可以是 `http://0.0.0.0:{your_port}/v1` 或 `http://localhost:{your_port}/v1`。如果您在云服务器上运行，我们强烈建议使用 VSCode，可以实现无缝端口转发。

效果如下：

https://github.com/libowen2121/InternLM/assets/19970308/096bb4f9-7c29-428e-a335-7b18f101f43f