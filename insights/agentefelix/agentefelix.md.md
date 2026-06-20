# Plano Mestre: CEO Agente Autônomo no Claude Code

Este documento estabelece a arquitetura técnica e o protocolo operacional para transformar o Claude Code de um assistente de codificação em um **CEO Agente Autônomo**. Inspirado no projeto Felix, o objetivo é a transição para um modelo de negócio "zero humanos", onde o proprietário atua apenas como a direção estratégica (os "bumpers" da pista de boliche), enquanto o agente assume 100% da execução técnica e operacional.

### 1. Visão Geral e Missão do Agente CEO

A missão é construir uma operação capaz de escalar até a meta de **$1 milhão de faturamento**, mantendo um **OPEX (Custo Operacional) otimizado de aproximadamente $1.500/mês**.

Nesta filosofia de "Vibe Coding", a delegação é absoluta. O humano fornece a visão via monólogos naturais (notas de voz via Telegram ou mensagens rambly no CLI), e o agente traduz essa "vibe" em infraestrutura, código e receita, operando de forma independente e proativa.

### 2. O Core de Identidade: Estrutura de Arquivos de Configuração

A autonomia exige uma identidade fixa e regras inegociáveis. No Claude Code, isso é consolidado em quatro arquivos fundamentais que servem de "manual de instruções" para o modelo:

- **CLAUDE.md (Raiz):** O ponto de entrada obrigatório. Este arquivo referencia o Manual de Operação e a auto-memória do sistema, servindo como a "âncora" de contexto para todas as sessões.
- **SOUL.md (Identidade):** Instruções sobre tom de voz, personalidade executiva, restrições de design e visão de longo prazo. É o "espírito" do CEO.
- **USER.md (Contexto):** Dados fixos críticos, como fuso horário (essencial para briefings matinais), chaves de API, preferências de stack tecnológica e contas ativas.
- **AGENTS.md (Protocolos de Segurança):** Regras de "corpo" e limites éticos. Inclui a obrigatoriedade de screenshots antes de submissões web e a proibição estrita de pagamentos não autorizados.

### 3. Arquitetura Operacional Híbrida (Três Camadas)

Diferente de assistentes simples, o Agente CEO utiliza uma estratégia de modelos híbridos para equilibrar custo e inteligência (OPEX vs. Performance).

|   |   |   |
|---|---|---|
|Camada|Componente|Implementação Técnica|
|**Canal (Channel)**|Escritório|CLI/Terminal do Claude Code e WhatsApp (via Evolution API).|
|**Cérebro (Brain)**|Orquestração|**Claude 3.5 Sonnet** (Tarefas complexas/Coding) + **Claude Haiku** (Heartbeat/Triagem).|
|**Corpo (Body)**|Execução|Ferramentas MCP, automação de browser (Playwright) e File System.|

### 4. Ciclo de Execução: O Loop de 7 Estágios (Framework OpenClaw)

Cada interação segue um fluxo rigoroso para garantir integridade de estado e evitar "slop" (geração de baixa qualidade):

1. **Normalização:** Padronização de entradas (texto ou voz transcrita).
2. **Roteamento e Command Queue:** Serialização de tarefas via fila de comandos para evitar corrupção de sessão durante execuções assíncronas.
3. **Montagem de Contexto:** Injeção automática do `CLAUDE.md` e arquivos de identidade.
4. **Inferência:** Chamada ao modelo com reserva estratégica de tokens de contexto.
5. **Loop ReAct:** O ciclo Decisão -> Ação -> Observação -> Repetição até a conclusão da meta.
6. **Skills On-Demand:** Carregamento de arquivos `SKILL.md` com **Load-time Dependency Filtering** (o agente verifica se binários como `jq` ou variáveis de ambiente existem antes de carregar a habilidade).
7. **Persistência:** Registro de memória em Markdown local e SQLite para aprendizado contínuo.

### 5. Manual de Operação: Heartbeat e Ritmos Diários

Para ser proativo, o Agente CEO não espera comandos; ele possui um **Heartbeat Loop** que opera em **Headless Mode** (via systemd no Linux ou LaunchAgent no macOS).

- **Rotina Proativa:** A cada 30 minutos, o agente "desperta" de forma assíncrona, dispara requisições HTTP para escanear Stripe (vendas), e-mails e GitHub.
- **Check-in Matinal:** Geração automática de um briefing de prioridades enviado ao humano.
- **Nightly Loop (Auto-Aperfeiçoamento):** Toda noite, o agente analisa os logs diários para **identificar intervenções humanas**. Ele deve propor novas automações ou "Custom Commands" para eliminar esses gargalos, aumentando sua autonomia no dia seguinte.
- **Comando de Saúde:** Antes de qualquer rotina, execute `openclaw doctor` para validar o ambiente.

### 6. Ecossistema MCP e Ferramentas Estratégicas

Utilize o Model Context Protocol para conectar o agente ao faturamento e à infraestrutura:

- **Stripe:** `claude mcp add --transport http stripe https://mcp.stripe.com` (Gestão financeira).
- **Vercel:** `claude mcp add --transport http vercel https://mcp.vercel.com` (Deploys automáticos).
- **GitHub:** Uso da CLI oficial (`gh`) para gestão de PRs e Issues.
- **Evolution API:** `claude mcp add --transport http evolution {URL}` (WhatsApp para comunicação externa e prevenção de bloqueios).

### 7. Estratégia 'Spiderweb Logic' e Modos de Execução

Para evitar erros em cascata, aplicamos a revisão de cada **Nó (Node)** da tarefa individualmente.

- **Plan Mode:** Obrigatório para "Hard Tasks" (novas funcionalidades, infra). O agente deve escrever um PRD/Plano, submetê-lo para aprovação do humano e só então iniciar a execução.
- **Normal Mode:** Exclusivo para trivialidades (correção de typos, ajustes de CSS simples).

**Plano de 5 Estágios (Nós):** 1. Infra, 2. Dev, 3. Financeiro (Stripe/Webhooks), 4. CRM (Evolution API), 5. QA/Deploy.

### 8. Segurança e Blindagem contra Injeção Indireta

Agentes com acesso ao terminal são alvos de **Indirect Prompt Injection** (instruções maliciosas escondidas em e-mails ou sites lidos pelo agente).

- **Lockdown de Arquivos:** Aplique `chmod 700` no diretório `.openclaw` e `chmod 600` nos arquivos de configuração.
- **Sanitização:** Regra no `AGENTS.md` para tratar todo dado externo como "não-confiável".
- **Gateway Security:** Ativação obrigatória de `gateway.token` no arquivo `openclaw.json`.
- **Auditoria:** Execução semanal do comando `openclaw audit` para detectar exfiltração de dados.

### 9. Roadmap de Escalabilidade (Abordagem Snowball)

O crescimento financeiro do negócio segue três fases de monetização baseadas na experiência Felix:

1. **Fase 1 (Info-produtos):** Criação e venda de ativos digitais (Ex: PDF "How to Hire an AI"). Valida o fluxo Stripe -> Entrega.
2. **Fase 2 (Marketplace):** Curadoria e venda de Skills no **Claw Mart**. O agente atua como intermediário, gerindo uma **taxa de intermediação de 10%** e assinaturas de criadores de **$20/mês**.
3. **Fase 3 (Consultoria Autônoma - Clawcommerce):** Venda de instâncias personalizadas do agente para outras empresas. O CEO gerencia o setup e cobra uma **taxa de manutenção recorrente de $500/mês**.