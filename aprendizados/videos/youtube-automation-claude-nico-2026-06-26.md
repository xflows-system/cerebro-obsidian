---
tags: [youtube, automacao, claude, mcp, ia, referencia]
data: 2026-06-26
fonte: https://www.youtube.com/watch?v=nfqnPnpoN2k
criador: Nico (canal de automação/YouTube growth — argentino)
---

# Sistema Completo de YouTube com Claude — Benchmark

## O que é
Sistema de 9 passos usando Claude + MCP para criar e escalar canal YouTube do zero.
O criador chama de *"clonación de mi cerebro"* — Claude treinado no método pessoal dele de YouTube.

## Stack usado
- **Claude.ai** — interface principal com skills customizadas
- **Nexle** — conecta Claude ao MCP do ChatGPT (bidirecional)
- **YouTube Studio MCP** — Claude acessa métricas reais em tempo real
- **ElevenLabs** — narração com pausas e ênfases via tags `[pausa]` `[emphasizes]`
- **Midjourney** — geração de miniaturas

## Os 9 Passos

**Passo 1 — Identidade do Canal**
Claude com skill `identidad-de-canal`. Gera: perfil de audiência, descrição, tags, handle, roteiro de trailer.
Exemplo: canal "Caso Abierto" (true crime latinoamericano em espanhol).

**Passo 2 — Encontrar Ideias de Vídeo**
Claude + YouTube Studio MCP analisa outliers do nicho — vídeos com performance acima da média.
Identifica padrões de formato e ângulo que ativam o algoritmo.

**Passo 3 — Ângulo Assassino**
Claude gera 5 ângulos candidatos. Avalia cada um por: credibilidade, fascínio, impacto emocional.
Exemplo: pessoa que desapareceu em 1989 e reapareceu em 2024 sem envelhecer.

**Passo 4 — Concepto de Miniatura**
Claude gera conceito visual detalhado: split image, cor dominante, tipografia, regras de composição.

**Passo 5 — Prompt de Imagem + Validação**
Prompt Midjourney preciso. Validar miniatura com 5 pessoas (22–38 anos) antes de publicar.
Imagem gerada: retrato "1989 — 2024" lado a lado, preto e branco.

**Passo 6 — Plano de Edição**
Claude age como diretor: cena a cena com timing, subtítulos, B-roll, split screen, narração.
ElevenLabs com tags de pausa: `"Esta foto é de 1989. [pausa] Esta é de 2024. [emphasizes] É a mesma pessoa."`

**Passo 7 — Otimização Pré-Publicação**
10 keywords principais + 10 secundárias. Auditoria de risco (clickbait, verificabilidade).
Entrega metadados finais prontos para upload.

**Passo 8 — Channel Doctor**
Claude + YouTube Studio MCP analisa vídeo existente.
Exemplo bom: 62,5K impressões, CTR 6,1%, 5,3K views → "não toca em nada, replica o formato".
Exemplo ruim: 8,7K impressões, CTR 3,8% → "deveria ter mudado thumbnail a tempo, vídeo morto".

**Passo 9 — Dashboard Semáforo**
Agrupa métricas do YouTube Studio em Verde / Amarelo / Vermelho com prioridades numeradas.

## Produção Visual do Canal
- Fundo RGB roxo/azul, talking head close-up
- Legendas amarelas em bold (kinetic text — palavra por palavra)
- Corte para preto e branco em momentos dramáticos
- CTA: comunidade gratuita "Imperio Automatizado" (200+ membros)

## Alternativas Open Source (pesquisa 2026-06-26)
Ver nota [[youtube-automation-open-source-stack]]

## Por que é relevante
Template direto para o projeto [[canal-consciencia-digital]] — mesma estrutura de nicho + automação.
