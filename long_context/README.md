# InternLM with Long Context

English | [简体中文](./README_zh-CN.md)

## InternLM with 1M Context Length



## Doc Chat with InternLM2.5-1M

This part provides a brief overview of how to chat with [InternLM2.5-7B-Chat-1M]() using an input document. For optimal performance, especially with extensively long inputs, we highly recommend using [LMDeploy]() for model serving.

## Supported Document Types

Currently, we support PDF, TXT, and Markdown files, with more file types to be supported soon!

- TXT and Markdown files: These can be processed directly without any conversions.
- PDF files: We have developed [Magic-Doc](https://github.com/magicpdf/Magic-Doc), a lightweight open-source tool, to convert multiple file types to Markdown.

## Installation

To get started, install the required packages:
```bash
pip install "fairy-doc[cpu]"
pip install streamlit
pip install lmdeploy
```

## Deploy the Model

Download our model from [link](xxx).

Deploy the model using the following command. You can specify the `session-len` (sequence length) and `server-port`.

```bash
lmdeploy serve api_server {path_to_hf_model} \
--model-name internlm2-chat \
--session-len 65536 \
--server-port 8000
```

## Launch the Streamlit Demo

```bash
streamlit run long_context/doc_chat_demo.py \
-- --base_url http://0.0.0.0:8000/v1
```

You can specify the port as you need. If you are running the demo locally, the URL could be `http://0.0.0.0:{your_port}/v1` or `http://localhost:{your_port}/v1`. If you are running on a virtual cloud machine, we highly suggest using VSCode for seamless port forwarding.


The effect is similar to below.

https://github.com/libowen2121/InternLM/assets/19970308/096bb4f9-7c29-428e-a335-7b18f101f43f


