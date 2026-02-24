# Large Language Models

## DeepSeek

### Text Generation

```
$ ollama pull deepseek-r1:7b

$ lms get deepseek/deepseek-r1-0528-qwen3-8b
```

### Code Generation

```
$ ollama pull deepseek-coder:6.7b

$ lms get TheBloke/deepseek-coder-6.7B-instruct-GGUF
```

## Qwen

8 billion parameters.

```
$ ollama pull qwen3:8b

$ lms get qwen/qwen3-8b
```

4 billion parameters.

```
$ ollama pull qwen3:4b

$ lms get qwen/qwen3-4b-2507
```

## Gemma

Contains reasoning that allows developers to understand what the model is thinking.

```
$ ollama pull gemma3:4b

$ lms get google/gemma-3-4b
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

$ ollama pull ministral-3:3b
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

#### Text Generation

8 billion parameters.

```
$ ollama pull dolphin3:8b

$ lms get dphn/Dolphin-X1-8B-GGUF
```

#### Code Generation

7 billion parameters.

```
$ ollama pull dolphincoder:7b
```

### Wizard Vicuna

```
$ ollama pull wizard-vicuna-uncensored:7b

$ lms get TheBloke/Wizard-Vicuna-7B-Uncensored-GGUF
```

### DeepHat

> [!INFO]
> This is literally hacker's favorite model for pentesting.

```
$ ollama pull DeepHat/DeepHat-V1-7B

$ lms get mradermacher/DeepHat-V1-7B-GGUF
```

---
## References

### Source Repositories

- [eugeneyan: open-llms](https://github.com/eugeneyan/open-llms)

### Eric Hartford

- [Eric Hartford: Uncensored Models](https://erichartford.com/uncensored-models)