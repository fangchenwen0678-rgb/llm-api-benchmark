# LLM API Benchmark \& Inference Evaluation Toolkit

> A lightweight Python toolkit for benchmarking OpenAI-compatible LLM
> APIs and evaluating latency, token usage, response behavior, and
> inference characteristics. 一个轻量级 Python 大语言模型 API
> 基准测试工具，用于评估兼容 OpenAI 接口的 LLM API，在响应延迟、Token
> 使用量、响应行为及推理特征等方面的表现。

\---

## 1\. Project Overview｜项目简介

### English

This project is a lightweight API testing and benchmarking toolkit for
large language model (LLM) services.

The project focuses on building a reproducible testing workflow rather
than introducing a complex framework. It provides a standardized API
client, configurable model parameters, batch Prompt testing, response
metric collection, and CSV-based experiment logging.

The current implementation focuses on **API-side benchmarking**. A
future extension can use the same experimental framework to compare API
calls with web/UI-based inference workflows.

### 中文

本项目是一套面向大语言模型（LLM）服务的轻量级 API 测试与基准评测工具。

项目重点不是构建复杂的软件框架，而是建立一套**可重复、可对比的模型 API
实验流程**。目前支持标准化 API Client 封装、模型参数配置、批量 Prompt
测试、响应指标采集以及 CSV 实验结果记录。

当前版本主要聚焦于 **API
侧的基准测试**。后续可以在现有实验框架基础上进一步扩展 API 调用与网页/UI
推理流程之间的对比。

\---

## 2\. Research Objective｜研究目标

### English

The project is designed to support controlled experiments on LLM API
behavior, including:

* Comparing response latency under different API configurations
* Tracking first-token / first-chunk response latency for streaming
requests
* Recording token usage and model responses
* Collecting HTTP status codes and error information
* Persisting experimental results for subsequent analysis
* Providing a consistent basis for cross-model or cross-API comparison

### 中文

项目用于支持对大语言模型 API 行为进行受控实验，主要包括：

* 比较不同 API 配置下的响应延迟
* 记录流式请求中的首 Token / 首块返回延迟
* 记录 Token 使用量及模型输出
* 收集 HTTP 状态码和异常信息
* 将实验结果持久化，便于后续分析
* 为不同模型或不同 API 的横向比较提供统一实验基础

\---

## 3\. Core Features｜核心功能

\---

Feature                 English                 中文

\---

API Client              Standardized API client 标准化 API Client 封装
abstraction

Configurable Endpoint   API Key, Base URL and   支持 API Key、Base
model configuration     URL、模型配置

Generation Parameters   Temperature and max     支持 temperature、max\_tokens
tokens

Streaming               Streaming response      支持流式响应测试
testing

Batch Prompt Testing    Load multiple Prompts   从文本文件批量读取 Prompt
from a text file

Latency Measurement     End-to-end response     记录完整响应耗时
latency

First-token Latency     Track first response    追踪首 Token / 首块返回延迟
delay for streaming

Token Usage             Record token            记录 Token 消耗
consumption

Response Logging        Store model responses   保存模型回答及原始响应数据
and raw response data

Error Handling          Record HTTP status and  记录 HTTP 状态码及异常
errors

CSV Persistence         Save experiment results 将实验结果保存至 CSV
to CSV
---

\---

## 4\. Experimental Workflow｜实验流程

``` text
Test Prompts
     │
     ▼
Load Prompt File
     │
     ▼
Configure API Client
     │
     ├── API Key
     ├── Base URL
     ├── Model
     ├── Temperature
     ├── Max Tokens
     └── Streaming
     │
     ▼
Send API Request
     │
     ▼
Collect Metrics
     │
     ├── Response
     ├── Elapsed Time
     ├── First-token Delay
     ├── Token Usage
     ├── HTTP Status
     └── Error Information
     │
     ▼
Save Experiment Results
     │
     ▼
CSV / Further Analysis
```

\---

## 5\. Project Structure｜项目结构

``` text
llm-api-benchmark/
├── api\_benchmark.ipynb
├── testprompt.txt
├── README.md
├── requirements.txt
└── .gitignore
```

### File Description｜文件说明

* `api\_benchmark.ipynb` --- Core implementation of the API
benchmarking workflow.
* `testprompt.txt` --- Test Prompt dataset used for batch experiments.
* `README.md` --- Project documentation.
* `requirements.txt` --- Python package dependencies.
* `.gitignore` --- Files and local secrets that should not be
committed.

\---

## 6\. Key Design｜核心设计

### Standardized API Client

The project uses an `ApiClient` abstraction to separate API
configuration from the experimental workflow.

This makes it possible to configure:

* API name
* API key
* Base URL
* Model
* Temperature
* Max tokens
* Streaming mode
* Timeout

### Standardized Experiment Records

Each experiment can record information such as:

* Test method
* Timestamp
* Model
* Prompt
* End-to-end latency
* First-token latency
* Response content
* Token usage
* HTTP status code
* Raw response
* Error information

This structure provides a consistent data basis for later comparison and
analysis.

\---

## 7\. Current Scope｜当前阶段

The current version focuses on **API-side testing and benchmarking**.

It is intentionally lightweight and does not introduce unnecessary
frameworks or complex infrastructure. The main goal is to establish a
reliable experimental pipeline first.

### 当前版本重点

当前版本主要完成：

1. 通用 LLM API 请求封装
2. API 参数配置
3. Prompt 批量读取
4. API 请求循环测试
5. 响应指标采集
6. 实验结果 CSV 落盘

\---

## 8\. Future Work｜后续方向

Potential extensions include:

* System Prompt parameter experiments
* More systematic temperature / generation-parameter experiments
* Larger standardized Prompt test sets
* Automated result analysis and visualization
* Cross-model and cross-API comparison
* API inference vs. web/UI inference comparison

> Note: API-vs-UI comparison is a planned extension and is not claimed
> as a completed feature of the current version.

\---

## 9\. Technology Stack｜技术栈

* Python
* Jupyter Notebook
* OpenAI-compatible API
* CSV
* LLM evaluation / benchmarking

\---

## 10\. Project Status｜项目状态

**Current stage: API Benchmarking Prototype / Experimental Toolkit**

The core workflow is designed around lightweight, reproducible
experiments. Future development will focus on improving experimental
coverage and analysis rather than adding unnecessary framework
complexity.

**当前阶段：API 基准测试原型 / 实验工具**

项目目前以轻量化、可重复的 API
实验流程为核心。后续开发将重点放在实验覆盖范围和结果分析能力的完善，而不是引入不必要的复杂框架。

\---

## 11\. Security Note｜安全说明

API keys should be provided at runtime and should **not** be hard-coded
into source files or committed to GitHub.

If an API key has ever been exposed in notebook output or source code,
it should be revoked or rotated before publishing the repository.

\---

## 12\. Author｜作者

### **Fang Chenwen** 

##### **Applied Mathematics Student**

Interests: Python, Data Analysis, Artificial Intelligence, Large
Language Models, and Quantitative Applications.

