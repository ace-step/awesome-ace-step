# Awesome ACE-Step [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of projects, tools, models, UIs, and resources for [ACE-Step](https://github.com/ace-step/ACE-Step) — the open-source music generation foundation model by ACE Studio and StepFun.

ACE-Step is a hybrid architecture combining a Language Model planner with a Diffusion Transformer to generate commercial-grade music from text prompts and lyrics. It runs locally on consumer hardware with as little as 4 GB VRAM, generating a full song in under 2 seconds on A100 or under 10 seconds on RTX 3090.

---

## Contents

- [Official Resources](#official-resources)
- [Official Models](#official-models)
- [Alternative UIs and Studios](#alternative-uis-and-studios)
- [Radio and Continuous Generation](#radio-and-continuous-generation)
- [ComfyUI Integration](#comfyui-integration)
- [C++ / GGML Implementation](#c--ggml-implementation)
- [Training and Fine-tuning](#training-and-fine-tuning)
- [Integrations and Extensions](#integrations-and-extensions)
- [Cloud and Serverless Deployment](#cloud-and-serverless-deployment)
- [Community Forks](#community-forks)
- [Related Projects](#related-projects)
- [Tutorials and Guides](#tutorials-and-guides)
- [Commercial Services](#commercial-services)
- [Papers](#papers)

---

## Official Resources

- [ace-step/ACE-Step](https://github.com/ace-step/ACE-Step) - Main repository with Gradio UI, REST API, CLI, and LoRA training. 4,100+ stars.
- [ACE-Step Project Page (v1.0)](https://ace-step.github.io/) - Original project page with architecture overview, demos, and benchmarks.
- [ACE-Step Project Page (v1.5)](https://ace-step.github.io/ace-step-v1.5.github.io/) - v1.5 release page covering the hybrid LM + DiT architecture and new capabilities.
- [HuggingFace Space Demo](https://huggingface.co/spaces/ACE-Step/ACE-Step) - Interactive online demo running on HuggingFace Zero GPU.
- [HuggingFace Organization](https://huggingface.co/ACE-Step) - All official model weights, LoRAs, and spaces.

## Official Models

### DiT Models (Diffusion Transformer)

| Model | Steps | Description |
|-------|-------|-------------|
| [acestep-v15-turbo](https://huggingface.co/ACE-Step/acestep-v15-turbo) | 8 | Distilled turbo model. Very high quality, very fast. **Recommended.** |
| [acestep-v15-turbo-continuous](https://huggingface.co/ACE-Step/acestep-v15-turbo-continuous) | 8 | Turbo variant optimized for continuous/streaming generation. |
| [acestep-v15-sft](https://huggingface.co/ACE-Step/acestep-v15-sft) | 50 | Supervised fine-tuned. High quality, medium diversity. |
| [acestep-v15-base](https://huggingface.co/ACE-Step/acestep-v15-base) | 50 | Pre-trained base model. Medium quality, high diversity, best for fine-tuning. |
| [ACE-Step-v1-3.5B](https://huggingface.co/ACE-Step/ACE-Step-v1-3.5B) | 50 | Original v1.0 model (3.5B parameters). |

### Language Models (Planner)

| Model | Base | Notes |
|-------|------|-------|
| [acestep-5Hz-lm-0.6B](https://huggingface.co/ACE-Step) | Qwen3-0.6B | Lightweight. For 6-8 GB VRAM setups. |
| [acestep-5Hz-lm-1.7B](https://huggingface.co/ACE-Step) | Qwen3-1.7B | Default. Full features, good quality. |
| [acestep-5Hz-lm-4B](https://huggingface.co/ACE-Step) | Qwen3-4B | Best quality. Strong audio understanding and composition. |

### LoRA Adapters

- [ACE-Step-v1-chinese-rap-LoRA](https://huggingface.co/ACE-Step/ACE-Step-v1-chinese-rap-LoRA) - RapMachine: Chinese rap/hip-hop LoRA with fine-grained vocal timbre and technique control.

### GGUF Quantized Models

- [Serveurperso/ACE-Step-1.5-GGUF](https://huggingface.co/Serveurperso/ACE-Step-1.5-GGUF) - Full GGUF quantization suite (Q4_K_M, Q5_K_M, Q6_K, Q8_0, BF16) for text encoder, LM, DiT, and VAE. Used by acestep.cpp.
- [calcuis/ace-gguf](https://huggingface.co/calcuis/ace-gguf) - Alternative GGUF model packaging.

## Alternative UIs and Studios

- [proximasan/tadpole-studio](https://github.com/proximasan/tadpole-studio) - Local-first AI music studio built with Next.js + FastAPI. Features AI DJ (chat-based generation), Radio mode, Library with playlists, LoRA training, 11 built-in themes, HeartMuLa backend support.
- [fspecii/ace-step-ui](https://github.com/fspecii/ace-step-ui) - Professional Spotify-inspired studio with dark/light modes, library management, integrated audio editor, stem extraction, and video generation. Supports all generation modes (text2music, cover, repaint, lego, extract, complete).
- [jpgallegoar/ACE-Step-UI](https://github.com/jpgallegoar/ACE-Step-UI) - Lightweight Gradio interface providing text-to-music, audio transformation with denoising controls, and song editing (inpainting, intros/outros). Drop-in addition to the main ACE-Step repo.
- [cocktailpeanut/ace-step-ui.pinokio](https://github.com/cocktailpeanut/ace-step-ui.pinokio) - One-click Pinokio launcher for ace-step-ui. Handles backend + frontend startup automatically.
- [pinokiofactory/ACE-Step](https://github.com/pinokiofactory/ACE-Step) - Pinokio script wrapper for the original ACE-Step Gradio UI.

## Radio and Continuous Generation

- [PasiKoodaa/ACE-Step-RADIO](https://github.com/PasiKoodaa/ACE-Step-RADIO) - Continuous AI radio station combining an LLM (Gemma) for lyrics generation with ACE-Step for music composition. Memory-optimized to run on RTX 3060 12GB. Configurable buffer for gap-free streaming.

## ComfyUI Integration

- [billwuhao/ComfyUI_ACE-Step](https://github.com/billwuhao/ComfyUI_ACE-Step) - ComfyUI custom nodes for ACE-Step. Supports generation, repainting, remixing, extending, LoRA, CPU offload, and multilingual lyrics conversion.
- [thezveroboy/ComfyUI_ACE-Step-zveroboy](https://github.com/thezveroboy/ComfyUI_ACE-Step-zveroboy) - Fork adding explicit model loading nodes for finer control over the ComfyUI workflow.
- [ComfyUI Native Workflow Guide](https://comfyui-wiki.com/en/tutorial/advanced/audio/ace-step/ace-step-v1) - Community wiki tutorial for setting up ACE-Step workflows in ComfyUI.
- [Comfy.org Official Example](https://docs.comfy.org/tutorials/audio/ace-step/ace-step-v1) - Official ComfyUI documentation with native ACE-Step example workflows.

## C++ / GGML Implementation

- [acestep.cpp](https://huggingface.co/Serveurperso/ACE-Step-1.5-GGUF) - Portable C++17 implementation of the full ACE-Step 1.5 pipeline using GGML. Two-stage pipeline: Qwen3 LM generates audio codes, then DiT + VAE synthesizes stereo 48kHz WAV. Runs on CPU, CUDA, Metal, and Vulkan. Supports batch generation and multiple quantization levels.

## Training and Fine-tuning

- [koda-dernet/Side-Step](https://github.com/koda-dernet/Side-Step) - Standalone LoRA/LoKR training toolkit for ACE-Step 1.5. Auto-detects model variant (turbo/base/sft) and applies correct timestep sampling strategy. Trains on 8 GB VRAM with gradient checkpointing and 8-bit optimizers. Includes interactive wizard and CLI. No base ACE-Step installation required.

## Integrations and Extensions

- [rsxdalv/tts-generation-webui](https://github.com/rsxdalv/tts-generation-webui) - Multi-model audio generation WebUI (2,900+ stars) supporting Bark, MusicGen, Tortoise, Stable Audio, and more. ACE-Step available via extension marketplace.
- [rsxdalv/extension_ace_step](https://github.com/rsxdalv/extension_ace_step) - ACE-Step extension for tts-generation-webui. Enables ACE-Step generation within the shared PyTorch context alongside other audio models.

## Cloud and Serverless Deployment

- [Replicate: andreasjansson/ace-step](https://replicate.com/andreasjansson/ace-step) - Serverless API running on Nvidia A100 (80 GB). Supports Node.js, Python, HTTP, Cog, and Docker clients.
- [fal.ai: ACE-Step](https://fal.ai/models/fal-ai/ace-step) - Serverless text-to-audio and audio-to-audio API with pay-per-use pricing and auto-scaling.
- [Modal: ACE-Step Example](https://modal.com/docs/examples/generate_music) - Full serverless deployment example with Gradio UI, model caching via Modal Volumes, and L40S GPU.
- [Vast.ai: ComfyUI ACE-Step Template](https://docs.vast.ai/documentation/serverless/comfyui-acestep) - Pre-configured serverless template with automatic S3 uploads and webhook support.
- [Olares: Self-hosted ACE-Step](https://docs.olares.com/use-cases/ace-step.html) - Deploy ACE-Step on your personal Olares cloud (self-hosted homelab OS).

## Community Forks

- [Decentralised-AI/ACE-Step-1.5-local-music](https://github.com/Decentralised-AI/ACE-Step-1.5-local-music) - Fork emphasizing local deployment with comprehensive documentation. 20 contributors.

## Related Projects

- [HeartMuLa/heartlib](https://github.com/HeartMuLa/heartlib) - Open-source LLM-based music generation model family (3,200+ stars). Includes HeartMuLa (song generation), HeartTranscriptor (lyric recognition), HeartCodec (12.5 Hz tokenizer), and HeartCLAP (audio-text alignment). Compatible as alternative backend in Tadpole Studio.
- [HeartMuLa-oss-3B](https://huggingface.co/HeartMuLa/HeartMuLa-oss-3B) - HeartMuLa 3B model weights (Apache 2.0).
- [HeartMuLa-RL-oss-3B](https://huggingface.co/HeartMuLa/HeartMuLa-RL-oss-3B-20260123) - RL-refined version with better style and tag control.
- [ACE-Step/acestep-transcriber](https://huggingface.co/ACE-Step/acestep-transcriber) - Qwen2.5 Omni-based audio transcription model for music-to-text tasks.

## Tutorials and Guides

- [DigitalOcean: Generate AI Music with ACE-Step 1.5](https://www.digitalocean.com/community/tutorials/ace-step-music-ai) - Step-by-step tutorial covering installation, generation, and LoRA customization.
- [ComfyUI Wiki: ACE-Step Workflow Guide](https://comfyui-wiki.com/en/tutorial/advanced/audio/ace-step/ace-step-v1) - Detailed walkthrough for building ACE-Step workflows in ComfyUI.
- [Comfy.org: ACE-Step Native Example](https://docs.comfy.org/tutorials/audio/ace-step/ace-step-v1) - Official ComfyUI documentation and example workflow.
- [DeepWiki: Docker Deployment](https://deepwiki.com/ace-step/ACE-Step/6.1-docker-deployment) - Docker deployment documentation for ACE-Step.
- [PandaiTech: Install ACE-Step 1.5 with UV](https://pandaitech.my/alpha/how-to-install-ace-step-15-using-git-and-the-uv-pa-ef9fe2df) - Installation guide using Git and the UV package manager.

## Commercial Services

- [ACE-Step Music Studio](https://acestep.app/) - Official cloud music studio with Inspiration and Professional modes. Free credits for new users.
- [ACE Studio](https://docs.acestudio.ai/) - Professional AI music production suite by the ACE-Step team.

## Papers

- [ACE-Step: A Step Towards Music Generation Foundation Model](https://arxiv.org/abs/2506.00045) - Original technical report (v1.0). Introduces the DCAE + linear transformer architecture with REPA training.
- [ACE-Step 1.5: Pushing the Boundaries of Open-Source Music Generation](https://arxiv.org/abs/2602.00744) - v1.5 technical report. Covers the hybrid LM planner + DiT architecture, intrinsic RL training, and comprehensive evaluation.

---

## Contributing

Contributions welcome! Please read the [contributing guidelines](CONTRIBUTING.md) first.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the authors have waived all copyright and related or neighboring rights to this work.
