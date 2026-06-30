---
tags: [video, claude-code, company-os, agentes, operacao]
source: https://www.youtube.com/watch?v=qsDX0PMKcaE
data: 2026-06-30
pessoa: Jiaona Zhang (CPO, Laurel)
canal: Aakash Gupta
duracao: 68 min
---

# Como construir um Company OS no Claude Code

**Jiaona Zhang** (ex-Airbnb, Webflow, Dropbox, Linktree) mostra o sistema operacional de empresa que construiu no Claude Code na Laurel — onde cada função de negócio tem playbooks em arquivos que agentes conseguem ler e executar.

---

## O que é um Company OS

Ponto de entrada mínimo:
- Inbox e workflows de review
- Hubs leves de compartilhamento de conhecimento
- Estrutura suficiente para pessoas *e* IA agirem

Caminho para alavanca:
**Operação manual → Shared structure → Participação distribuída → Agentes autônomos**

---

## A Estrutura — GitHub repo "Company-OS"

- Pastas por função: `customer-success/`, `account-management/`, `engineering/`, `product/`...
- Cada pasta tem arquivos de playbook descrevendo *como o trabalho funciona*
- Base: **Company Catalog** — planilha com todas as funções, categorias e tarefas repetíveis

Sequência correta: escreve o playbook primeiro → identifica o workflow → vira agente.

---

## O que fica na prática

**Agentes no Slack**
Canal `#ask-product`: alguém pergunta → Claude responde no thread com análise estruturada, referenciando PRDs e tickets. Sem instrução manual.

**GTM — Run Agent**
20+ botões prontos: Account Brief, Call Prep, Churn Prevention, Handoff Builder, Renewal Prep, Win/Loss Review... Qualquer CSM clica e o agente executa com contexto da conta.

**Scheduled tasks autônomas**
- Daily QA storytelling
- Product status update
- Internal roadmap sync
- Candidate recap check
- Daily trend analysis
- Morning action ping

**Email sequences geradas**
Claude produziu sequência de onboarding completa (Welcome → Mid-Trial → Upgrade Nudge) com subject lines, timing e alerta sobre evento faltando no backend.

**Design/Eng loop via Slack**
Designer pergunta → Claude inclui link do PR no GitHub + contexto + próximos passos. Sem reunião.

---

## Progressão Conceitual

```
Playbook (doc estruturado)
    ↓
Workflow (tarefa repetível identificada)
    ↓
Agente (executa o workflow autônomo)
```

---

## Visão Q1

- Empoderar CSMs de linha de frente para *desenvolver features* usando agentes
- Referência ao modelo Devin para times de produto
- Próximo passo: não é PM → agente. É **CSM → agente construindo feature**

---

## Aplicação para o XPF

- **Company Catalog como skill index**: o que a Jiaona chama de catálogo é o que o XPF precisa para resolver o problema de skill discovery do Hermes. Um index estruturado (função → categoria → tarefa) que o agente consulta antes de agir.
- **Scheduled tasks pattern**: a lista de tarefas autônomas dela é exatamente o que o Heartbeat standby do Hermes deveria executar após a primeira venda.
- **Playbook → Workflow → Agent**: a disciplina de escrever o playbook *antes* do código é o que falta para formalizar as skills XPF — muitas foram criadas sem o playbook base.
- **Run Agent como UX**: botões nomeados por caso de uso (não por tech) é a interface certa para operador não-técnico disparar tarefas.
