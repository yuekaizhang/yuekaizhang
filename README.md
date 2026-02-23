# Hi, I'm Yuekai Zhang

Speech AI @ NVIDIA. Working on training and deployment for speech models.

WeChat: `ykzhang2020` | Email: zhangyuekai@foxmail.com

---

## Pre-training

| Recipe | Description | Link |
|--------|-------------|------|
| Whisper Fine-tuning | Fine-tune Whisper large-v2 on multi Chinese datasets using icefall | [icefall/whisper](https://github.com/yuekaizhang/icefall/tree/emilia/egs/multi_zh-hans/ASR/whisper) |
| Speech LLM | Whisper encoder + Qwen2 LLM for Chinese ASR (Qwen-Audio style) | [icefall/ASR_LLM](https://github.com/yuekaizhang/icefall/tree/emilia/egs/speech_llm/ASR_LLM) |
| Speech-to-Speech | Qwen2.5-Omni-Like: Whisper → Adapter → Thinker LLM → Talker LLM → CosyVoice2 | [mair-hub/qwen_omni_like](https://github.com/nvidia-china-sae/mair-hub/tree/main/speech-llm/qwen_omni_like) |

## Post-training

| Direction | Method | Framework | Link |
|-----------|--------|-----------|------|
| Speech Understanding | GRPO on Qwen2-Audio / Qwen2.5-Omni | WeST | [west/examples/grpo](https://github.com/wenet-e2e/west/tree/main/examples/grpo) |
| Speech Generation | GRPO / DAPO on CosyVoice2 LLM (veRL + SenseVoice reward) | veRL | [mair-hub/cosyvoice_llm](https://github.com/nvidia-china-sae/mair-hub/tree/main/rl-tutorial/cosyvoice_llm) |

## Deployment

All solutions use **NVIDIA Triton Inference Server** with Docker Compose quick-start.

### ASR

| Model | Backend | Streaming | Link |
|-------|---------|:---------:|------|
| Whisper | TensorRT-LLM | — | [sherpa/triton/whisper](https://github.com/k2-fsa/sherpa/tree/master/triton/whisper) |
| Fun-ASR-Nano | vLLM | — | [Fun-ASR-vllm](https://github.com/yuekaizhang/Fun-ASR-vllm) |
| FireRedASR-AED | TensorRT-LLM | — | [FireRedASR/triton_tensorrt](https://github.com/FireRedTeam/FireRedASR/tree/main/runtime/triton_tensorrt) |
| FireRedASR2-AED | TensorRT-LLM | — | [FireRedASR2S/triton_tensorrt](https://github.com/FireRedTeam/FireRedASR2S/tree/main/runtime/triton_tensorrt) |
| SenseVoice / Paraformer | ONNX | — | [FunASR/triton_gpu](https://github.com/modelscope/FunASR/tree/main/runtime/triton_gpu) |
| Conformer (WeNet) | ONNX | Yes | [wenet/runtime/gpu](https://github.com/wenet-e2e/wenet/tree/main/runtime/gpu) |
| Zipformer (Transducer) | TensorRT / ONNX | Yes | [sherpa/triton](https://github.com/k2-fsa/sherpa/tree/master/triton) |

### TTS

| Model | Type | Streaming | Link |
|-------|------|:---------:|------|
| F5-TTS | Diffusion | — | [F5-TTS/triton_trtllm](https://github.com/SWivid/F5-TTS/tree/main/src/f5_tts/runtime/triton_trtllm) |
| Spark-TTS | LLM | Yes | [Spark-TTS/triton_trtllm](https://github.com/SparkAudio/Spark-TTS/tree/main/runtime/triton_trtllm) |
| CosyVoice 2 | LLM + Diffusion | Yes | [CosyVoice/triton_trtllm](https://github.com/FunAudioLLM/CosyVoice/tree/main/runtime/triton_trtllm) |
| ZipVoice | Diffusion (distilled) | — | [ZipVoice/nvidia_triton](https://github.com/k2-fsa/ZipVoice/tree/master/runtime/nvidia_triton) |

### Tools

| Tool | Description | Link |
|------|-------------|------|
| Triton-ASR-Client | Benchmarking client with CER/WER eval, streaming & concurrency support | [Triton-ASR-Client](https://github.com/yuekaizhang/Triton-ASR-Client) |
| Triton-OpenAI-Speech | OpenAI-compatible `/v1/audio/speech` API for Triton TTS backends | [Triton-OpenAI-Speech](https://github.com/yuekaizhang/Triton-OpenAI-Speech) |
