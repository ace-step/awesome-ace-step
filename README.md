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
- [Data Annotation](#data-annotation)
- [Integrations and Extensions](#integrations-and-extensions)
- [Open-Source Music Generation Landscape](#open-source-music-generation-landscape)
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
| [Discord](https://discord.gg/PeWDxrkdj7) | Community chat and support. |

## Models

### DiT Models (Diffusion Transformer)

| Model | Steps | Quality | Speed | Features | Link |
|-------|:-----:|---------|-------|----------|------|
| **acestep-v15-turbo** | 8 | Very High | Very Fast | text2music, cover, repaint | [HF](https://huggingface.co/ACE-Step/acestep-v15-turbo) |
| acestep-v15-turbo-continuous | 8 | Very High | Very Fast | Optimized for streaming | [HF](https://huggingface.co/ACE-Step/acestep-v15-turbo-continuous) |
| acestep-v15-sft | 50 | High | Medium | All features | [HF](https://huggingface.co/ACE-Step/acestep-v15-sft) |
| acestep-v15-base | 50 | Medium | Medium | All features, best for fine-tuning | [HF](https://huggingface.co/ACE-Step/acestep-v15-base) |

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
| Serveurperso/ACE-Step-1.5-GGUF | GGUF | Full quantization suite (Q4-Q8, BF16) for acestep.cpp | [HF](https://huggingface.co/Serveurperso/ACE-Step-1.5-GGUF) |

## UIs and Studios

| Project | Tech Stack | Highlights | Link |
|---------|-----------|------------|------|
| **ace-step-ui** (fspecii) | Node.js + Python | Spotify-inspired, dark/light modes, audio editor, stem extraction, video gen. 560+ stars | [GitHub](https://github.com/fspecii/ace-step-ui) |
| **Tadpole Studio** | Next.js + FastAPI | AI DJ, Radio, Library, Playlists, LoRA training, HeartMuLa backend, 11 themes | [GitHub](https://github.com/proximasan/tadpole-studio) |
| ace-step-ui.pinokio | Pinokio | One-click launcher for ace-step-ui (v1.5), auto backend + frontend | [GitHub](https://github.com/cocktailpeanut/ace-step-ui.pinokio) |

## ComfyUI

| Project | Description | Link |
|---------|-------------|------|
| **ComfyUI Native Support** | ACE-Step 1.5 built into ComfyUI core. AIO and split model workflows | [Docs](https://docs.comfy.org/tutorials/audio/ace-step/ace-step-v1-5) |
| **ComfyUI-AceMusic** | 15-node full-featured integration: generation, cover, repaint, extend, edit, LoRA, HeartMuLa compatible | [GitHub](https://github.com/hiroki-abe-58/ComfyUI-AceMusic) |
| **ComfyUI-FL-AceStep-Training** | LoRA training pipeline in ComfyUI: auto-label, tiled VAE, real-time loss charts | [GitHub](https://github.com/filliptm/ComfyUI-FL-AceStep-Training) |

## Training and Fine-tuning

| Project | Description | Link |
|---------|-------------|------|
| **Side-Step** | Standalone LoRA/LoKR toolkit for v1.5. Auto-detects variant, 8 GB VRAM training, interactive wizard + CLI | [GitHub](https://github.com/koda-dernet/Side-Step) |
| **ComfyUI-FL-AceStep-Training** | End-to-end LoRA training inside ComfyUI with auto-labeling and live monitoring | [GitHub](https://github.com/filliptm/ComfyUI-FL-AceStep-Training) |

## Data Annotation

| Project | Description | Link |
|---------|-------------|------|
| **acestep-captioner** | 11B music captioning model (Qwen2.5 Omni). 1000+ instruments, timbre, structure analysis. Accuracy surpasses Gemini Pro 2.5 | [HF](https://huggingface.co/ACE-Step/acestep-captioner) |
| **acestep-transcriber** | Qwen2.5 Omni-based music transcription. Structure annotation, lyrics transcription, 50+ languages | [HF](https://huggingface.co/ACE-Step/acestep-transcriber) |

## Integrations and Extensions

| Project | Description | Link |
|---------|-------------|------|
| **acestep.cpp** | Portable C++17 / GGML implementation of ACE-Step 1.5. CPU, CUDA, Metal, Vulkan. Stereo 48 kHz WAV output | [GitHub](https://github.com/ServeurpersoCom/acestep.cpp) |

## Open-Source Music Generation Landscape

A comparison of notable open-source music generation projects alongside ACE-Step.

| Project | Architecture | Capability | License | Link |
|---------|-------------|------------|---------|------|
| **ACE-Step** | LM + DiT | Text/lyrics → full song (vocal + BGM), cover, repaint, LoRA. <4 GB VRAM | Apache-2.0 | [GitHub](https://github.com/ace-step/ACE-Step) |
| **YuE** | LLaMA2 autoregressive | Lyrics → full song, multi-genre, multi-lingual, voice cloning, style transfer | Apache-2.0 | [GitHub](https://github.com/multimodal-art-projection/YuE) |
| **AudioCraft / MusicGen** | Autoregressive transformer | Text → music/audio, melody conditioning, style conditioning (JASCO) | MIT | [GitHub](https://github.com/facebookresearch/audiocraft) |
| **Amphion** | Multiple (SVC, TTS, TTA) | Singing voice conversion, text-to-audio, vocoders, research toolkit | MIT | [GitHub](https://github.com/open-mmlab/Amphion) |
| **Riffusion** | Stable Diffusion (spectrograms) | Real-time text → music via spectrogram diffusion | MIT | [GitHub](https://github.com/riffusion/riffusion) |
| **Stable Audio Tools** | DiT + flow matching | Text → variable-length stereo audio (up to 47 s) | MIT | [GitHub](https://github.com/Stability-AI/stable-audio-tools) |
| **DiffRhythm** | Latent diffusion (DiT + VAE) | Lyrics → full-length song (up to 4 min 45 s) in ~10 s | Apache-2.0 | [GitHub](https://github.com/ASLP-lab/DiffRhythm) |
| **HeartMuLa** | LLM-based codec | Song gen, lyric recognition, audio codec, audio-text alignment | Apache-2.0 | [GitHub](https://github.com/HeartMuLa/heartlib) |

## Tutorials and Guides

| Title | Topic | Link |
|-------|-------|------|
| ACE-Step Prompt Guide | Detailed prompting tips: tags, lyrics structure, genre control | [Ambience AI](https://www.ambienceai.com/tutorials/ace-step-music-prompting-guide) |
| Generate AI Music with ACE-Step 1.5 | Installation, generation, LoRA customization | [DigitalOcean](https://www.digitalocean.com/community/tutorials/ace-step-music-ai) |
| ComfyUI ACE-Step 1.5 Guide | Official ComfyUI v1.5 workflow tutorial | [Comfy.org](https://docs.comfy.org/tutorials/audio/ace-step/ace-step-v1-5) |
| AMD ACE-Step 1.5 Local Guide | Running ACE-Step on AMD GPUs | [PromptGalaxy](https://promptgalaxyai.com/blog/amd-ace-step-local-music-ai) |
| Install ACE-Step 1.5 with UV | Git + UV package manager setup | [PandaiTech](https://pandaitech.my/alpha/how-to-install-ace-step-15-using-git-and-the-uv-pa-ef9fe2df) |
| ACE Studio | Professional AI music production suite | [acestudio.ai](https://docs.acestudio.ai/) |

## Papers

| Paper | Version | Key Contribution | Link |
|-------|---------|-----------------|------|
| ACE-Step: A Step Towards Music Generation Foundation Model | v1.0 | DCAE + linear transformer, REPA training | [arXiv](https://arxiv.org/abs/2506.00045) |
| ACE-Step 1.5: Pushing the Boundaries of Open-Source Music Generation | v1.5 | Hybrid LM + DiT, intrinsic RL, comprehensive evaluation | [arXiv](https://arxiv.org/abs/2602.00744) |

---

## Contributing

Contributions welcome! Please read the [contributing guidelines](CONTRIBUTING.md) first.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the authors have waived all copyright and related or neighboring rights to this work.
