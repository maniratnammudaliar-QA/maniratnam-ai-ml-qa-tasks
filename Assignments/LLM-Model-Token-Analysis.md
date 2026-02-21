# 1) LLM Model Token Comparison

## Overview
This document compares context window, max output tokens, and calculated max input tokens across selected LLM models.

| Model | Context Window | Max Output Tokens | Max Input Tokens* | Infrastructure Provider |
|-------|---------------|------------------|-------------------|--------------------------|
| openai/gpt-5.2 | 400K | 128K | 272K | openai |
| openai/gpt-4o-mini | 128K | 16.4K | 111.6K | openai |
| openai/gpt-4.1-mini | 1.05M | 32.8K | 1,017.2K | openai |
| anthropic/claude-opus-4.6 | 1M | 128K | 872K | amazon-bedrock |
| anthropic/claude-sonnet-4.5 | 1M | 64K | 936K | google-vertex |
| anthropic/claude-haiku-4.5 | 200K | 64K | 136K | amazon-bedrock |
| qwen/qwen3-coder-next | 262.1K | 65.5K | 196.6K | chutes/bf16 |
| qwen/qwen3-32b | 41K | 20K | 21K | novita/fp8 |
| qwen/qwen3-30b-a3b | 41K | 41K | 0K | deepinfra/fp8 |

---
## Note:- Max Input Tokens are calculated as (Context Window − Max Output Tokens). Actual usable input depends on the output tokens requested. Input and output tokens share the same context window.

# 2) QWEN - Transformer or MOE?

Qwen models are built on the Transformer architecture.
The base versions of Qwen 1 and Qwen 2 use a standard dense Transformer, meaning all feed-forward layers are fully activated for every token.

Some newer Qwen 2.5 variants adopt a Mixture of Experts (MoE) design. In MoE models, multiple expert feed-forward networks are defined, but only a subset of experts are activated per token
