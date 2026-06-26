---
tags: [youtube, automacao, open-source, tts, mcp, legendas]
data: 2026-06-26
contexto: alternativas gratuitas ao stack do vídeo de Nico (Claude + ElevenLabs + Midjourney + Nexle)
---

# Stack Open Source para YouTube Automatizado

## Problema
Stack do Nico (ElevenLabs + Midjourney + Nexle MCP) custa dinheiro.
Precisamos de alternativas funcionais para o [[canal-consciencia-digital]].

## 1. Voz (substitui ElevenLabs)

| Ferramenta | Tipo | Qualidade | Custo |
|---|---|---|---|
| **OmniVoice Studio** | Local/desktop | ★★★★★ | Grátis |
| **Kokoro** | Open source (82M params) | ★★★★ | Grátis |
| **Fish Audio S2 Pro** | API | ★★★★★ | Pago/freemium |
| **edge-tts** (atual) | CLI | ★★★ | Grátis |

**Recomendação imediata:** OmniVoice Studio
- Roda 100% local, sem API key
- 646 idiomas incluindo pt-BR
- Tem MCP server nativo (Claude o aciona direto)
- Suporta clonagem de voz
- Stack: FastAPI + WhisperX + Demucs
- GitHub: github.com/OmniVoice (ver MarkTechPost 2026-05-26)

**Para subir um nível sem custo:** Kokoro via HuggingFace ou rodando local.

## 2. MCP YouTube Studio (substitui Nexle)

Opções open source testadas/documentadas:

| Repo | Ferramentas | Nota |
|---|---|---|
| `mrchevyceleb/youtube-mcp` | 22 tools: analytics, thumbnails, metadata, captions | Mais completo |
| `adityaarsharma/youtube-mcp-server` | 21 AI commands + live channel MCP | Alternativa VidIQ/TubeBuddy |
| `i1s-abhishek/youtube-studio-mcp` | Analytics, uploads, comentários | OAuth direto |
| `wynandw87/claude-code-youtube-mcp` | Transcripts, trending, heatmaps, SponsorBlock | Mais leve |
| CDataSoftware/youtube-analytics-mcp | Somente analytics (read-only) | Mais simples |

**Recomendação:** `mrchevyceleb/youtube-mcp` — mais ferramentas, suporta Claude Code diretamente.
Configurar com OAuth Google → funciona com qualquer canal.

## 3. Legendas/Captions (substitui CapCut manual)

**cutcaption** — open source CLI (GitHub: `markbakos/cutcaption`)
- Instala via pip
- Usa faster-whisper para transcrição
- Gera legendas estilizadas burned-in (estilo CapCut/Reels)
- Sem API key, funciona local
- Input: MP4 → Output: MP4 com legendas animadas

Outras opções:
- **VEED** (online, freemium) — melhor sistema de captions automáticos do mercado
- **Descript** (pago) — edição baseada em transcrição, ótimo para talking head

## 4. Geração de Imagem para Thumbnails (substitui Midjourney)

- **FLUX** (local ou API) — qualidade próxima de Midjourney
- **Stable Diffusion** (local) — mais controle, mais setup
- **Ideogram** (freemium) — melhor para texto em imagem (thumbnails com palavras)

## Stack Recomendado Completo (zero custo)

```
Roteiro (Claude) 
→ OmniVoice Studio (voz local, pt-BR)
→ cutcaption (legendas automáticas animadas)
→ FLUX/Ideogram (thumbnail)
→ mrchevyceleb/youtube-mcp (analytics + upload)
→ Claude + YouTube Studio MCP (Channel Doctor)
```

## Próximos Passos para canal-consciencia-digital
1. Instalar OmniVoice Studio na VPS ou no Windows
2. Testar voz em pt-BR vs edge-tts atual
3. Instalar cutcaption — gera legendas animadas no MP4 do pipeline existente
4. Configurar youtube-mcp com OAuth do canal @seucerebromente
