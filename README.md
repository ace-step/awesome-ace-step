# Awesome ACE-Step [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of projects, tools, models, UIs, and resources for [ACE-Step](https://github.com/ace-step/ACE-Step) — the open-source music generation foundation model by ACE Studio and StepFun.

ACE-Step is a hybrid architecture combining a Language Model planner with a Diffusion Transformer to generate commercial-grade music from text prompts and lyrics. It runs locally on consumer hardware with as little as 4 GB VRAM, generating a full song in under 2 seconds on A100 or under 10 seconds on RTX 3090.

---

## Contents

- [Official Resources](#official-resources)
- [Models](#models)
- [UIs and Studios](#uis-and-studios)
- [ComfyUI](#comfyui)
- [Training and Fine-tuning](#training-and-fine-tuning)
- [Integrations and Extensions](#integrations-and-extensions)
- [Cloud and Deployment](#cloud-and-deployment)
- [Music Understanding](#music-understanding)
- [Related Projects](#related-projects)
- [Tutorials and Guides](#tutorials-and-guides)
- [Papers](#papers)

---

## Official Resources

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/ace-step/ACE-Step) | Main codebase with Gradio UI, REST API, CLI, and LoRA training. 4,100+ stars. |
| [Project Page (v1.0)](https://ace-step.github.io/) | Architecture overview, demos, and benchmarks. |
| [Project Page (v1.5)](https://ace-step.github.io/ace-step-v1.5.github.io/) | Hybrid LM + DiT architecture, new capabilities. |
| [HuggingFace Space](https://huggingface.co/spaces/ACE-Step/ACE-Step) | Interactive online demo on HuggingFace Zero GPU. |
| [HuggingFace Models](https://huggingface.co/ACE-Step) | All official model weights, LoRAs, and spaces. |
| [PyPI Package](https://pypi.org/project/ace-step/) | `pip install ace-step` — installable package with GUI support. |
| [Discord](https://discord.gg/PeWDxrkdj7) | Community chat and support. |

## Models

### DiT Models (Diffusion Transformer)

| Model | Steps | Quality | Speed | Features | Link |
|-------|:-----:|---------|-------|----------|------|
| **acestep-v15-turbo** | 8 | Very High | Very Fast | text2music, cover, repaint | [HF](https://huggingface.co/ACE-Step/acestep-v15-turbo) |
| acestep-v15-turbo-continuous | 8 | Very High | Very Fast | Optimized for streaming | [HF](https://huggingface.co/ACE-Step/acestep-v15-turbo-continuous) |
| acestep-v15-sft | 50 | High | Medium | All features | [HF](https://huggingface.co/ACE-Step/acestep-v15-sft) |
| acestep-v15-base | 50 | Medium | Medium | All features, best for fine-tuning | [HF](https://huggingface.co/ACE-Step/acestep-v15-base) |
| ACE-Step-v1-3.5B | 50 | Medium | Medium | Original v1.0 model | [HF](https://huggingface.co/ACE-Step/ACE-Step-v1-3.5B) |

### Language Models (Planner)

| Model | Base | VRAM | Capability | Link |
|-------|------|------|------------|------|
| acestep-5Hz-lm-0.6B | Qwen3-0.6B | 6-8 GB | Lightweight | [HF](https://huggingface.co/ACE-Step) |
| **acestep-5Hz-lm-1.7B** | Qwen3-1.7B | 8-16 GB | Default, full features | [HF](https://huggingface.co/ACE-Step) |
| acestep-5Hz-lm-4B | Qwen3-4B | 16+ GB | Best quality, audio understanding | [HF](https://huggingface.co/ACE-Step) |

### LoRA Adapters and Quantized Models

| Model | Type | Description | Link |
|-------|------|-------------|------|
| ACE-Step-v1.5-chinese-new-year-LoRA | LoRA | Chinese folk instruments (dizi, erhu), festive style. Trained on 12 songs | [HF](https://huggingface.co/ACE-Step/ACE-Step-v1.5-chinese-new-year-LoRA) |
| ACE-Step-v1-chinese-rap-LoRA | LoRA | Chinese rap/hip-hop with vocal timbre and technique control | [HF](https://huggingface.co/ACE-Step/ACE-Step-v1-chinese-rap-LoRA) |
| Serveurperso/ACE-Step-1.5-GGUF | GGUF | Full quantization suite (Q4-Q8, BF16) for acestep.cpp | [HF](https://huggingface.co/Serveurperso/ACE-Step-1.5-GGUF) |
| calcuis/ace-gguf | GGUF | GGUF packaging for v1 model, ComfyUI compatible | [HF](https://huggingface.co/calcuis/ace-gguf) |

## UIs and Studios

| Project | Tech Stack | Highlights | Link |
|---------|-----------|------------|------|
| **Tadpole Studio** | Next.js + FastAPI | AI DJ, Radio, Library, Playlists, LoRA training, HeartMuLa backend, 11 themes | [GitHub](https://github.com/proximasan/tadpole-studio) |
| **ace-step-ui** (fspecii) | Node.js + Python | Spotify-inspired, dark/light modes, audio editor, stem extraction, video gen. 560+ stars | [GitHub](https://github.com/fspecii/ace-step-ui) |
| ACE-Step-UI (jpgallegoar) | Python / Gradio | Lightweight: text2music, audio transform, song editor. Drop-in to ACE-Step | [GitHub](https://github.com/jpgallegoar/ACE-Step-UI) |
| ace-step-ui.pinokio | Pinokio | One-click launcher for ace-step-ui (v1.5), auto backend + frontend | [GitHub](https://github.com/cocktailpeanut/ace-step-ui.pinokio) |
| ACE-Step (pinokiofactory) | Pinokio | One-click launcher for original Gradio UI | [GitHub](https://github.com/pinokiofactory/ACE-Step) |
| **ACE-Step-RADIO** | Python / Gradio | Continuous AI radio with LLM lyrics. RTX 3060 12 GB optimized | [GitHub](https://github.com/PasiKoodaa/ACE-Step-RADIO) |

## ComfyUI

| Project | Description | Link |
|---------|-------------|------|
| **ComfyUI_ACE-Step** | Custom nodes: generation, repaint, remix, extend, LoRA, CPU offload, multilingual. 225+ stars | [GitHub](https://github.com/billwuhao/ComfyUI_ACE-Step) |
| **ComfyUI-FL-AceStep-Training** | LoRA training pipeline in ComfyUI: auto-label, tiled VAE, real-time loss charts | [GitHub](https://github.com/filliptm/ComfyUI-FL-AceStep-Training) |
| ComfyUI ACE-Step 1.5 Guide | Official docs with native v1.5 example workflows | [Docs](https://docs.comfy.org/tutorials/audio/ace-step/ace-step-v1-5) |
| ComfyUI Wiki Guide | Community tutorial for ACE-Step workflows | [Wiki](https://comfyui-wiki.com/en/tutorial/advanced/audio/ace-step/ace-step-v1) |

## Training and Fine-tuning

| Project | Description | Link |
|---------|-------------|------|
| **Side-Step** | Standalone LoRA/LoKR toolkit. Auto-detects variant, 8 GB VRAM training, interactive wizard + CLI | [GitHub](https://github.com/koda-dernet/Side-Step) |
| **ComfyUI-FL-AceStep-Training** | End-to-end LoRA training inside ComfyUI with auto-labeling and live monitoring | [GitHub](https://github.com/filliptm/ComfyUI-FL-AceStep-Training) |

## Integrations and Extensions

| Project | Description | Link |
|---------|-------------|------|
| **acestep.cpp** | Portable C++17 / GGML implementation. CPU, CUDA, Metal, Vulkan. Stereo 48 kHz WAV output | [GitHub](https://github.com/ServeurpersoCom/acestep.cpp) |
| tts-generation-webui | Multi-model audio WebUI (2,900+ stars). ACE-Step via extension marketplace | [GitHub](https://github.com/rsxdalv/tts-generation-webui) |
| extension_ace_step | ACE-Step extension for tts-generation-webui | [GitHub](https://github.com/rsxdalv/extension_ace_step) |

## Cloud and Deployment

| Platform | Type | Description | Link |
|----------|------|-------------|------|
| Replicate | Serverless API | Nvidia A100. Node.js, Python, HTTP, Cog, Docker clients | [Replicate](https://replicate.com/andreasjansson/ace-step) |
| fal.ai | Serverless API | Text-to-audio and audio-to-audio. Pay-per-use, auto-scaling | [fal.ai](https://fal.ai/models/fal-ai/ace-step) |
| Modal | Serverless | Full example with Gradio UI, model caching, L40S GPU | [Modal](https://modal.com/docs/examples/generate_music) |
| Vast.ai | Serverless | ComfyUI ACE-Step template with S3 uploads and webhooks | [Vast.ai](https://docs.vast.ai/documentation/serverless/comfyui-acestep) |
| Olares | Self-hosted | Deploy on personal Olares homelab cloud | [Olares](https://docs.olares.com/use-cases/ace-step.html) |

## Music Understanding

| Project | Description | Link |
|---------|-------------|------|
| **MuFun** | 9B music understanding model. Analyzes songs and outputs tags + lyrics for ACE-Step prompts | [GitHub](https://github.com/laitselec/MuFun) |
| MuFun-ACEStep | MuFun fine-tune specialized for reverse-engineering ACE-Step prompts from audio | [HF](https://huggingface.co/Yi3852/MuFun-ACEStep) |
| acestep-transcriber | Qwen2.5 Omni-based music transcription model | [HF](https://huggingface.co/ACE-Step/acestep-transcriber) |

## Related Projects

| Project | Description | Link |
|---------|-------------|------|
| **HeartMuLa** | LLM-based music generation family (500+ stars). Song gen, lyric recognition, codec, audio-text alignment | [GitHub](https://github.com/HeartMuLa/heartlib) |
| HeartMuLa-oss-3B | HeartMuLa 3B model weights (Apache 2.0) | [HF](https://huggingface.co/HeartMuLa/HeartMuLa-oss-3B) |
| HeartMuLa-RL-oss-3B | RL-refined version with better style/tag control | [HF](https://huggingface.co/HeartMuLa/HeartMuLa-RL-oss-3B-20260123) |

## Tutorials and Guides

| Title | Topic | Link |
|-------|-------|------|
| ACE-Step Prompt Guide | Detailed prompting tips: tags, lyrics structure, genre control | [Ambience AI](https://www.ambienceai.com/tutorials/ace-step-music-prompting-guide) |
| Generate AI Music with ACE-Step 1.5 | Installation, generation, LoRA customization | [DigitalOcean](https://www.digitalocean.com/community/tutorials/ace-step-music-ai) |
| ComfyUI ACE-Step 1.5 Guide | Official ComfyUI v1.5 workflow tutorial | [Comfy.org](https://docs.comfy.org/tutorials/audio/ace-step/ace-step-v1-5) |
| AMD ACE-Step 1.5 Local Guide | Running ACE-Step on AMD GPUs | [PromptGalaxy](https://promptgalaxyai.com/blog/amd-ace-step-local-music-ai) |
| Docker Deployment | Docker setup for ACE-Step | [DeepWiki](https://deepwiki.com/ace-step/ACE-Step/6.1-docker-deployment) |
| Install ACE-Step 1.5 with UV | Git + UV package manager setup | [PandaiTech](https://pandaitech.my/alpha/how-to-install-ace-step-15-using-git-and-the-uv-pa-ef9fe2df) |
| ACE-Step Music Studio | Official cloud studio (Inspiration + Professional modes) | [acestep.app](https://acestep.app/) |
| ACE Studio | Professional AI music production suite | [acestudio.ai](https://docs.acestudio.ai/) |

## Papers

| Paper | Version | Key Contribution | Link |
|-------|---------|-----------------|------|
| ACE-Step: A Step Towards Music Generation Foundation Model | v1.0 | DCAE + linear transformer, REPA training | [arXiv](https://arxiv.org/abs/2506.00045) |
| ACE-Step 1.5: Pushing the Boundaries of Open-Source Music Generation | v1.5 | Hybrid LM + DiT, intrinsic RL, comprehensive evaluation | [arXiv](https://arxiv.org/abs/2602.00744) |
| Advancing the Foundation Model for Music Understanding | MuFun | Audio understanding model, music-to-text, ACE-Step integration | [arXiv](https://arxiv.org/abs/2508.01178) |

---

## Contributing

Contributions welcome! Please read the [contributing guidelines](CONTRIBUTING.md) first.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the authors have waived all copyright and related or neighboring rights to this work.
