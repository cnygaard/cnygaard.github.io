---
layout: post
title: E8 Lattice code book quantization of AI LLM large language models
date: 2026-06-13T21:11:14.617Z
thumbnail: https://upload.wikimedia.org/wikipedia/commons/f/fe/E8_graph.svg
---
Due to current high PC memory RAM prices being affected by AI companies buying up ram and wanting to run LLMs locally on more limited GPU memory devices such as gami ng GPU and workstation GPUs. I have with the help of AI code assistance created an open source library called glq which quantizes LLM model weights using E8 lattice so that the LLM model takes up less GPU VRAM. GLQ was inspired by ["](https://arxiv.org/pdf/2402.04396)Even Better LLM Quantization with
Hadamard Incoherence and Lattice Codebooks" [Quip#](https://arxiv.org/pdf/2402.04396).

Glq has an advantage compared to some other quantization methods at between 2- bits per word up to 4 bits per word.

For serving speed I have made it so that glq can run together with the open source LLM serving engine called vLLM.

I have quantized LLM models such as [Gemma-4 ](https://huggingface.co/google/gemma-4-31B-it)and [SmolLM](https://huggingface.co/HuggingFaceTB/SmolLM3-3B) from Huggingface.

Current lm-eval MMLU-Pro benchmark of Gemma 4 26B it although at sample small number of n=60 shows GLQ quanitzation at 93.3% vs bf16 91.7% within margin of error due to small sample size. But still an interesting result. In this benchmark at small sample rate glq is nearly lossless.

There is also E8 Key Value Cache quantization in glq which was inspired by [NexusQuant](https://github.com/jagmarques/nexusquant).

Comparsion of small open source LLM models by Artificial analysis

<https://artificialanalysis.ai/models/open-source/small>

Sphere packing

<https://en.wikipedia.org/wiki/Sphere_packing>

E8 Lattice[](https://en.wikipedia.org/wiki/E8_lattice)

<https://en.wikipedia.org/wiki/E8_lattice>





Opensource code E8 LLM compression library glq:

<https://github.com/cnygaard/glq>

Python pypi pip package called glq

<https://pypi.org/project/glq/>