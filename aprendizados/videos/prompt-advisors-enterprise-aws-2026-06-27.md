---
tags: [agentes-ia, aws, enterprise, arquitetura, produto, custo]
data: 2026-06-27
fonte: https://www.youtube.com/watch?v=T17DYl_4Z-U
criador: Prompt Advisors (Mark)
duracao: 36min
---

# Enterprise AI OS no AWS Bedrock — Prompt Advisors

## O que é

Sistema multi-agente enterprise construído em AWS Bedrock. Dashboard próprio ("ClaudeClaw"), voz, compliance, multi-tenant. Levou 1+ mês e ~10M tokens para construir. Vende como curso premium + repo.

## Slide central — mapeamento Hermes → Enterprise AWS

| Pessoal (Hermes/OpenClaw) | Enterprise (AWS) |
|---|---|
| Hosted model API | Amazon Bedrock |
| Local files | S3 |
| One operator | IAM + roles |
| Local DB / Supabase | DynamoDB + KMS |
| `.env` secrets | Secrets Manager |
| Sem audit | Guardrails + audit log |

> "Don't throw the agent OS away. Swap each piece for a secure one."

## 5 variáveis do enterprise

Transparência · Simplicidade · Escalabilidade · Segurança · Custo

## Features do sistema

- **Jarvis** — agente de voz read-only que navega dashboard e explica métricas. Não executa, só explica. Nova Sonic (áudio) + Claude (raciocínio).
- **Cost caps** — hard stop automático quando gasto diário atinge limite. Agentes bloqueados até quota do dia seguinte.
- **Kill switches** — toggle por serviço + botão pânico que desliga tudo.
- **Compliance score** — SOC 2 / HIPAA com remediation brief gerado por IA. Lê regulamentações via Claude e compara com setup real.
- **Leak scanning** — scan de mensagens para AWS access keys, Slack tokens, credit cards, GitHub PATs antes de propagar resposta.
- **Multi-tenant** — admin / operador / viewer. Invite por magic link via SES (AWS email service).
- **RAG compartilhado** — Titan Embed → S3 → hive mind DynamoDB, todos os agentes acessam os mesmos arquivos.
- **MCP marketplace AWS** — Slack, Salesforce, Jira, Confluence nativos e seguros dentro do ambiente.

## Modelo de produto do criador

```
Vídeo educacional (gratuito, YouTube)
→ Blueprint + slide deck + prompts (gratuito, lead magnet)
→ Curso "Claude Code Living Course" (premium, módulo novo por semana)
→ Repo do OS enterprise (premium anual)
```

## Frase-chave

> "Planejei 2 semanas antes de começar a buildar. Cada nova fase: mais 2 semanas de planejamento antes da próxima iteração."

## O que NÃO se aplica ao modelo solopreneur

- AWS Bedrock (caro, overkill para solo)
- IAM roles, SOC 2, HIPAA
- Multi-tenant com membros externos
- Infraestrutura com custo fixo mensal

## O que se extrai para uso pessoal/negócio

Ver nota: [[aprendizados-prompt-advisors-xpf]]
