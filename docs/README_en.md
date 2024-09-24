<h2 align='center'>chatgpt-tool-hub</h2>
<p align='center'>Give ChatGPT wings to fly</p>

<p align="center">
  <a style="text-decoration:none" href="https://aianything.netlify.app" target="_blank">
    <img src="https://img.shields.io/badge/language-python-blue" alt="Language" />
  </a>
  <a style="text-decoration:none" href="https://github.com/KeJunMao" target="_blank">
    <img src="https://img.shields.io/github/license/goldfishh/chatgpt-tool-hub" alt="license " />
  </a>
  <a style="text-decoration:none" href="https://github.com/KeJunMao" target="_blank">
    <img src="https://img.shields.io/github/last-commit/goldfishh/chatgpt-tool-hub" alt="last commit " />
  </a>
</p>

<p align='center'>

</p>

---
<div align="center">

[简体中文](README.md) | **English**

</div>

> The emergence of LLM has amazed us with their abilities. ChatGPT has revolutionized NLP technology, and in addition, it has made me realize a new possibility of human-computer interaction.
<div>
    <h2 style="display:inline; margin:0; padding:0;">🌱 5.4 LLM-OS demo</h2>
  <div align="center">
    <a style="display:inline-block; align:center" src="https://colab.research.google.com/assets/colab-badge.svg" href="https://colab.research.google.com/drive/11nYPGFCYiaZ73H8nTHSN8ifbo0u3W_8p">
        <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="demo in Colab"/>
    </a>
    <br/>
    <a style="text-decoration:none" href="https://www.bilibili.com/video/BV1eL411h7Nk/" target="_blank">Bilibili Video</a>
<br/>
</div>
</div>

#### [Update Log](./docs/update_log.md) | [Q&A](./docs/q_and_a.md)

## Introduction

---

This is an execution engine that allows ChatGPT to use multiple magical tools. You can use natural language commands to use ChatGPT for networking, search, mathematical operations, computer control, code execution, and other tools, expanding the scope of ChatGPT usage and improving your productivity.

This project was born out of attention to the ChatGPT open plugin, which has poor customization and a closed ecosystem, which is not a good trend. I believe that in the future, LLMs in China will bloom in diversity. At the same time, I have seen the feasibility and potential value of using tools from ChatGPT, so I hope to create a tool ecosystem that is compatible with future LLMs.

If ChatGPT's plugin is compared to Apple's App Store, then the ultimate form of this project is the open ecosystem of Android OS, abbreviated as LLM-OS. In this ecosystem, all tools form an operating system, and users only need to input or transmit text to do anything.

Given the current situation, the positioning of this project is: an open-source ChatGPT tool ecosystem where you can integrate tools with ChatGPT and use natural language to accomplish anything.

<p align="center">
  <img src="/assets/llm-os.jpg" width="50%" height="50%">
</p>

## Features

---

#### 1. tool-hub can be used separately in LLM-OS demo
#### 2. Tool hub provides tool capabilities for [chatgpt-on-wechat](https://github.com/zhayujie/chatgpt-on-wechat) in the form of plugins. Please refer to the [Tool Plugin Usage Tutorial](https://github.com/goldfishh/chatgpt-on-wechat/tree/master/plugins/tool) for details.
#### 3. Support interaction between Chinese and English.
#### 4. Support contextual memory.
#### 5. Support proxy
#### 6. Support many tools [Tools Tutorial](./docs/tool_tutorial.md) 
#### 7. Support multiple tools to be called simultaneously and automatically, as well as tree arrangement tools

### ⛳ Take a look at the features of tool-hub future plan updates：[tool-hub todo-list](#plan) 
### 📭 Go to [issues](https://github.com/goldfishh/chatgpt-tool-hub/issues)

## ✈️ Quick start

---

### 1.  LLM-OS demo

#### (1). Fork repo

```bash
git clone https://github.com/goldfishh/chatgpt-tool-hub.git
cd chatgpt-tool-hub
```

#### (2). Install dependencies using pip

```bash
pip3 install -r requirements.txt
```

#### (3). Rename .env.template and  config.json.template, delete .template suffix then open the file and fill in the configuration parameters.

`.env` is used to configure global parameters.
```text
LLM_API_KEY=sk-xx          // Required, your OPENAI API Key. Please refer to Q&A for instructions on how to apply
MODEL_NAME=gpt-3.5-turbo      // Optional, OPENAI LLM model
THINK_DEPTH=3                 // Optional, default 3, control the maximum number of tool calls for LLM-OS, too large may not necessarily improve the quality of replies
REQUEST_TIMEOUT=90            // Optional, default 120, maximum time to wait for reply from OpenAI API
PROXY=http://192.168.7.1:7890 // Optional, you can fill in when you need a proxy to access OpenAI
DEBUG=false                   // Optional, debug mode
```

`config.json` is used to configure tool parameters.
```json
{
  "tools": [],   // Fill in the additional tool name you want.
  "kwargs": {
      "no_default": false,   // Whether use default tools. By default, Python, terminal, url-get, meteo-weather
      "top_k_results": 2,  // Control some search tools (such as arxiv, wikipedia) to return only the first k records, it is not recommended to have too many
      // Fill in tools which need to apply for an additional API key here.
  }
}
```

An example of the config. json configuration for tools that require additional application can be found in [Tool Application Method and Configuration Instructions](./docs/apply_optional_tool.md)

#### (4). Run terminal_io.py

```bash
python3 terminal_io.py
```

#### (5). After entering LLM-OS, you can explore on your own or further browse the detailed tutorial: [LLM_OS demo instructions](https://github.com/goldfishh/llm-os/blob/main/README.md)

---

### 2. I developed tool plugins for [chatgpt-on-wechat](https://github.com/zhayujie/chatgpt-on-wechat)

> By using this method, you will be able to conveniently use tool-hub with WeChat as the front-end

#### Refer to the chatgpt-on-wechat documentation: [Project Introduction](https://github.com/zhayujie/chatgpt-on-wechat#%E7%AE%80%E4%BB%8B) and  [Quick Start](https://github.com/zhayujie/chatgpt-on-wechat#%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B)

#### Note: You need to install extension dependencies to use the tool plugin

#### [tool plugin tutorial](https://github.com/goldfishh/chatgpt-on-wechat/blob/master/plugins/tool/README.md)

---

### 3. You are a developer of another project and would like to access the engine of this tool

> This project has been released on PyPI, you only need to use `pip` to install it

#### (1). Install chatgpt-tool-hub

```bash
pip install -i https://pypi.python.org/simple chatgpt-tool-hub
```

#### (2). Quick Start

```python
import os
from chatgpt_tool_hub.apps import AppFactory
os.environ["LLM_API_KEY"] = "YOUR_LLM_API_KEY"  # 必填
os.environ["PROXY"] = "YOUR_PROXY_ADDRESS"            # 选填
app = AppFactory().create_app(tools_list=[], **{})
reply = app.ask("YOUR_QUESTION_TO_HERE")
print(reply)
```

#### (3). Integrating tool hub in the form of plugins can refer to the implementation of tool plugins

[tool.py](https://github.com/goldfishh/chatgpt-on-wechat/blob/master/plugins/tool/tool.py)

> If there is a need, I will update the document for more detailed access. Please feel free to raise any issues

---

## Tool tutorial

### 🚀 [Tool tutorial](./docs/tool_tutorial.md)

---

## Principle

---

The principle of the tool engine is essentially **Chain-of-Thought**：[Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://arxiv.org/abs/2201.11903)

I will explain the working principle of chatgpt-tool-hub through 6 self-asked and self-answered questions.

#### 1. Where do transactional tools (such as terminal, Python) run and how do they execute them

Transactional tools run locally and are essentially functions written in Python. Terminal, Python, and URL get tools use functions that encapsulate calls to the subprocess library, Python interpreter, and requests library, respectively.

---

#### 2. How ChatGPT triggers the calling of these functions

With the help of the temperature parameter provided by the ChatGPT API, the lower the parameter, the more concentrated and deterministic the output of ChatGPT will be. When temperature is 0, the same question will receive a unified answer.

I will provide ChatGPT with a list of tools used during prompt construction, each tool information including: tool name and tool description:

```text
TOOLS:  
------  
  
You have access to the following tools:  

> Python REPL: A Python shell. Use this to execute python commands. 
> url-get: A portal to the internet. Use this when you need to get specific content from a website. 
> Terminal: Executes commands in a terminal. 
> Bing Search: A wrapper around Bing Search. Useful for when you need to answer questions about current events. 
```

With the tool prompt, ChatGPT can understand the names and usage scenarios of these tools, and calling transaction functions requires further refinement of the communication protocol between me and ChatGPT (still through prompt):
The communication protocol restricts the format of content returned by ChatGPT when using the tool, and can only return content with three prefixes:

```text
1. Thought: Do I need to use a tool? Yes or No
2. Action: Name of tool
3. Action Input: Input of tool
```

Complete prompt for communication protocol: 
```text
To use a tool, please use the following format:


Thought: Do I need to use a tool? Yes
Action: the action to take, should be one of [Python REPL, url-get, Terminal, Bing Search]
Action Input: the input to the action
Observation: the result of the action
```

At this point, the tool engine has a dedicated text parsing module responsible for parsing these contents. When parsing is successful, it will be scheduled to be executed by a specific transaction function and return a result with a fixed prefix:

```text
Observation: The content returned when the transaction function completes execution
```

The content prefixed with Observation is often the answer that users using transactional tools want to know.

---

#### 3. How does ChatGPT know which tools and inputs to use, and whether it strictly generates formatted content according to prompts every time

During the fine-tuning of ChatGPT, extensive Q&A, CoT prediction learning, and RLHF tuning are conducted. Currently, ChatGPT ensures the quality of tools and content generation.
But currently it is not 100% because there may be low-quality prompts or inappropriate tool inputs, which will be robustly processed by the tool engine to ensure the stability of the generated content.

I will create an issue that allows everyone to easily access and share interesting problems and ideas solved using the tool process, prompt techniques for each tool, and solutions to problems encountered.
[Discussion on better skills for using tools](https://github.com/goldfishh/chatgpt-tool-hub/issues/3)

---

#### 4. If multiple tools need to work together alternately to solve a problem, how does the engine do it

After the transaction function completes processing and returns the result, it will not be directly returned to the user by default. Instead, based on the result content CoT, there are two sub prompts in the entire prompt responsible for user conversation history and intermediate results.

User conversation history:
```text
Human: A question
AI: A answer
......
```

Intermediate result:
```text
Thought: Do I need to use a tool? Yes
Action: Wolfram Alpha
Action Input: gdp china vs. usa
Observation: China\nUnited States | GDP | nominal \nAnswer: China | $14.72 trillion per year\nUnited States | $20.95 trillion per year\n(2020 estimates)
Thought:
```

Each round of tool CoT process will serve as the basis for the next inference and judgment tool, iteratively performing tool judgment and execution. Finally, when a specific prefix is identified, the CoT result will be returned to the user.

CoT end prompt:
```text
When you have a response to say to the Human, or if you do not need to use a tool, you MUST use the format:

Thought: Do I need to use a tool? No
AI: the response to the original input question in chinese

```


The process of using ChatGPT tool is not smooth: when the number of iterations reaches the preset value, it will return the final result to the user based on the historical process.

---

#### 5. Is there any unforeseeable danger in handing over transactional tools to ChatGPT

Yes, when you use transactional tools, you give ChatGPT the right to run programs locally, and you need permission restrictions to avoid possible risks.
If you cannot trust ChatGPT to dominate your machine, please do not use it.

---

#### 6. What is the implementation principle of non transactional tools

See in [ChatGPT official plugins](https://github.com/openai/chatgpt-retrieval-plugin)，Non transactional tools, also known as plug-in tools, can be considered as open ChatGPT plugins.

---


## 🎯 Plans

<span id="plan"></span>

---

### feature todolist

[✓] Explanatory output of results ->LLM-OS's inner monologue  
[✓] A frontend demo ->LLM-OS  
[✓] Long Text Scene ->Summary Tool  
[✓] Long tool sequence control ->Implemented toolintool mechanism  
[✓] Granularity Configuration ->LLM encapsulated by each tool can be independently configured   
[○] Token calculation, precise management   
[○] gpt_index long text (pdf, html) retrieval  
[○] Interface concurrency support  
[○] Connect to domestic LLM  
[○] Compatible with scenarios that do not use tools  
[○] Mutual exclusion tool control  
[○] Subtree dynamic registration&anti registration  
[○] Tool Interruption  
[○] Scheduled scheduling  
[○] Voice input and output  

### tool todolist  

[○] Stable diffusion Chinese prompt translation  
[✓] ImageCaptioning    
[○] Xiaomi Smart Home Control  
[○] Support ChatGPT official plugin  
[○] Let LLM implement the tool  
[○] Support image processing tools  
[○] Support video processing tools  
[✗] Wechat  

## Tool Development Guide

---

At present, tools are divided into two categories: transactional tools and plugin tools.

[Tool Development Guide](./docs/tool_development_guide.md)

## Background

I will update this section soon.

---

## ☕ Advertising

#### If you want to support this project, please feel free to give the project a star, raise an issue, and provide a PR.
#### If you want to further support the project author in reducing hair loss and working hard in development, you can give a cup to my partner who developed the project with me or to me alone ☕

<table><tr>
<td><img src="/assets/buy_me_a_coffee.jpg" width="200" height="200" border=0 /></td>
</tr></table> 

---

## Thanks

Thank you for the strong support provided to this project by the following projects:

#### 1. [langchain](https://github.com/hwchase17/langchain) 

Inspired by Langchain, this project rewrote the implementation related to Langchain v0.0.123 tool.

#### 2. [Auto-GPT](https://github.com/Significant-Gravitas/Auto-GPT)

Inspired the cross platform implementation of browser tool, JSON communication of tool engine, and partial prompt description.

#### 3. [chatgpt-in-terminal](https://github.com/xiaoxx970/chatgpt-in-terminal)
- wolfram-alpha(you need wolfram_alpha_appid from https://developer.wolframalpha.com/)
- google-search(you need google_api_key and google_cse_id described here https://cloud.google.com/docs/authentication/api-keys?visit_id=638154342880239948-3750907574&rd=1&hl=zh-cn)
