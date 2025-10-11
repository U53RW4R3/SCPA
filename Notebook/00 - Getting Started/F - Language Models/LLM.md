# Large Language Models

## DeepSeek

### General

```
$ lms get deepseek/deepseek-r1-0528-qwen3-8b

$ ollama pull deepseek-r1:7b
```

### Code Generation

```
$ lms get TheBloke/deepseek-coder-6.7B-instruct-GGUF

$ ollama pull deepseek-coder:6.7b
```

## Qwen

8 billion parameters.

```
$ lms get qwen/qwen3-8b

$ ollama pull qwen3:8b
```

4 billion parameters.

```
$ lms get qwen/qwen3-4b-2507

$ ollama pull qwen3:4b
```

## Phi

```
$ ollama pull phi4-mini:3.8b
```

Contains reasoning that allows developers to understand what the model is thinking.

```
$ lms get microsoft/phi-4-mini-reasoning

$ ollama pull phi4-mini-reasoning:3.8b
```

## Dolphin

### Llama

8 billion parameters.

```
$ ollama pull dolphin3:8b
```

## Uncensored Models

### Mistral

```
$ ollama pull mistral:7b
```

#### Code Generation

```
$ ollama pull dolphin-mistral:7b
```

### DeepSeek

8 billion parameters.

```
$ ollama pull huihui_ai/deepseek-r1-abliterated:8b
```

7 billion parameters.

```
$ lms get DevQuasar/huihui-ai.DeepSeek-R1-Distill-Qwen-7B-abliterated-GGUF

$ ollama pull huihui_ai/deepseek-r1-abliterated:7b
```

### Qwen

8 billion parameters.

```
$ lms get DavidAU/Qwen3-8B-192k-Josiefied-Uncensored-NEO-Max-GGUF

$ ollama pull goekdenizguelmez/JOSIEFIED-Qwen3:8b
```

4 billion parameters.

```
$ lms get Goekdeniz-Guelmez/Josiefied-Qwen3-4B-abliterated-v1-gguf

$ ollama pull goekdenizguelmez/JOSIEFIED-Qwen3:4b
```

### Dolphin

#### General

##### Llama

8 billion parameters.

```
$ ollama pull huihui_ai/dolphin3-abliterated:8b
```

##### Mistral

7 billion parameters.

```
$ ollama pull dolphin-mixtral:8x7b

$ ollama pull dolphin-mistral:7b
```

#### Code Generation

```
$ ollama pull dolphincoder:7b
```

### Wizard Vicuna

```
$ lms get TheBloke/Wizard-Vicuna-7B-Uncensored-GGUF

$ ollama pull wizard-vicuna-uncensored:7b
```

### DeepHat

> [!INFO]
> This is literally hacker's favorite model for pentesting.

```
$ lms get mradermacher/DeepHat-V1-7B-GGUF

$ ollama pull DeepHat/DeepHat-V1-7B
```

---
## References

### Source Repositories

- [eugeneyan: open-llms](https://github.com/eugeneyan/open-llms)

### Eric Hartford

- [Eric Hartford: Uncensored Models](https://erichartford.com/uncensored-models)