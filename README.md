# README

*Leqi Li, The University of Science & Technology of China*

## Overview

This project successfully deploys LLaMA3 8B on a development board similar to a terminal smartphone (Huawei HH-SCDAYU200 Development Kit, OpenHarmony OS, CPU environment). The deployment process involves cross-compilation and static linking, enabling the migration of `llama.cpp` to the OpenHarmony system.

By applying quantization-aware fine-tuning, the inference speed on the edge device improved by approximately 60%. Additionally, various model compression techniques such as quantization, pruning, and distillation were explored. The project also examined vLLM technology and attempted to integrate it with `llama.cpp`.



## Technical Research

### OpenHarmony AI Subsystem

The OpenHarmony AI subsystem consists of four components:

- **ai_engine**: Provides a unified AI engine framework for seamless plugin integration.
- **intelligent_voice_framework**: Includes intelligent voice services and drivers, primarily for voice registration and wake-up functionalities.
- **mindspore**: A deep learning framework optimized for edge-cloud scenarios.
- **neural_network_runtime (NNRt)**: A runtime for cross-chip AI inference, bridging AI frameworks with hardware accelerators.

#### Neural Network Runtime (NNRt)

Neural Network Runtime (NNRt) serves as a middleware layer connecting AI inference frameworks with acceleration chips. It supports MindSpore Lite and provides native APIs for integration.

### Model Deployment Approach

- **Cross-compilation**: Successfully compiled `llama.cpp` for OpenHarmony.
- **Static linking**: Ensured compatibility with OpenHarmony’s runtime environment.
- **Quantization-aware fine-tuning**: Achieved a 60% increase in inference speed on edge devices.
- **vLLM integration**: Investigated and tested integration with `llama.cpp`.



## Performance Optimization Strategies

### 1. Memory Optimization: Paged Attention and KV Cache

#### 1.1 Paged Attention

PagedAttention improves memory efficiency by breaking KV cache into blocks accessible via lookup tables. This technique enables flexible memory management similar to an OS’s virtual memory system, reducing fragmentation and increasing GPU utilization.

#### 1.2 KV Cache Optimization

KV caching stores previously generated tokens to avoid redundant calculations, significantly accelerating transformer-based inference.

### 2. Model Compression Techniques

#### 2.1 Quantization

- **Weight-only quantization**: Reduces model size and improves inference speed.
- **Weight-activation quantization**: Balances accuracy and computational efficiency.
- **KV cache quantization**: Reduces memory consumption during inference.

#### 2.2 Pruning

- **Unstructured pruning**: Selectively removes redundant model weights.
- **Structured pruning**: Removes entire components to optimize execution speed.

#### 2.3 Knowledge Distillation

Transferring knowledge from a large model (teacher) to a smaller model (student) allows for efficient deployment while maintaining high accuracy.

#### 2.4 Low-rank Decomposition

Techniques such as LPLR and ASVD decompose large weight matrices to reduce computational complexity.



## LLaMA.cpp Integration

The `llama.cpp` framework simplifies deployment by providing efficient inference for LLaMA models. This project successfully migrated `llama.cpp` to OpenHarmony, enabling on-device execution.



## Results

- **Successful deployment** of LLaMA3 8B on OpenHarmony.
- **60% inference speedup** using quantization-aware fine-tuning.
- **Explored multiple model compression techniques**, including quantization, pruning, and distillation.
- **Tested vLLM integration** with `llama.cpp`.



## Future Work

- Further optimize memory management for large models on edge devices.
- Enhance vLLM and `llama.cpp` integration for better efficiency.
- Explore additional AI acceleration techniques for OpenHarmony.



## References

- OpenHarmony AI Subsystem: [Gitee - OpenHarmony](https://gitee.com/openharmony)
- Neural Network Runtime: [NNRt Documentation](https://gitee.com/openharmony/ai_neural_network_runtime)