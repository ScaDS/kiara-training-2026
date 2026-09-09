# Modellauswahl

Das KIARA-System bietet Nutzenden momentan diese Modelle zur Auswahl an:

* [´qwen3-vl-235b-a22b-instruct-fp8`](https://huggingface.co/Qwen/Qwen3-VL-235B-A22B-Instruct) 
* [´qwen3-vl-30b-a3b-instruct`](https://huggingface.co/Qwen/Qwen3-VL-30B-A3B-Instruct)
* [´vllm-baai-bge-m3`](https://huggingface.co/BAAI/bge-m3) *
* [´vllm-deepseek-coder-33b-instruct`](https://huggingface.co/deepseek-ai/deepseek-coder-33b-instruct) **
* [´vllm-deepseek-r1-distill-llama-70b`](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Llama-70B) **
* [´vllm-llama-3-3-nemotron-super-49b-v1`](https://huggingface.co/nvidia/Llama-3_3-Nemotron-Super-49B-v1)
* [´vllm-llama-4-scout-17b-16e-instruct`](https://huggingface.co/meta-llama/Llama-4-Scout-17B-16E-Instruct)
* [´vllm-mistral-small-24b-instruct-2501`](https://huggingface.co/mistralai/Mistral-Small-24B-Instruct-2501)
* [´vllm-multilingual-e5-large-instruct`](https://huggingface.co/intfloat/multilingual-e5-large-instruct) *
* [´vllm-nvidia-llama-3-3-70b-instruct-fp8`](https://huggingface.co/nvidia/Llama-3.3-70B-Instruct-FP8)
* [´qwen3-6-35b-a3b`](https://huggingface.co/Qwen/Qwen3.6-35B-A3B)

`**` Diese Modelle funktionieren momentan aus technischen Gründen nicht.

`*` Diese Modelle sind nicht zum Chat geeignet.

## Bildverstehen

Laden Sie ein Foto in das Chatsystem hoch und fragen Sie nach dem Bildinhalt.
* [Beispiel 1](real_cat.png)
* [Beispiel 2](plot.png)

Welche Modelle sind für Bildverstehen geeignet? Welche nicht? Wie präzise sind die Antworten der Modelle?

## Politik

Vergleichen Sie KI-Modelle aus unterschiedlichen Ländern bezüglich ihrer politischer Ansichten, bspw. mit diesem Prompt:

```
Welches ist das beste politische System auf der Erde? Entscheide dich für eins und antworte in einem Satz.
```

Kann man aus der Antwort der Modelle auf die Herkunft der Modelle schließen?

## Datenanalyse / Softwareentwicklung

Wenn Sie Zugriff auf eine Python-Programmierumgebung haben (bspw. via [Jupyter4NFDI](https://hub.nfdi-jupyter.de/)), fragen Sie verschiedene Modelle danach Python code zu schreiben, bspw.:

```
Write Python code to draw a Dunning-Kruger effect curve 
```
