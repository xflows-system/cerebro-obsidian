---
tags: [pessoas, claude-code, skills, agentes-ia, context-engineering]
data: 2026-06-27
fonte: https://www.youtube.com/watch?v=6ZgQJ-_3Iwk
---

# Felipe Fontoura

Educador e consultor de IA, foco em Claude Code, sistemas de agentes e empacotamento de conhecimento de nicho.

## Tese central

O mercado de automação simples (n8n, chatbot, instalação de ferramentas) está morrendo. Empresário hoje tem acesso direto ao Claude. O diferencial agora é **empacotar conhecimento de nicho em skills** e entregar resultado estratégico, não ferramental.

> "Você não vende skills. Você vende resultado. O que a sua IA entrega de valor pro cliente num determinado nicho."

## O que ele ensina sobre Skills

### Segredo mora nas REFERÊNCIAS dentro da skill

Skill genérica → IA acessa cluster genérico de parâmetros → output mediano.

Skill com referências destiladas → IA acessa o "filé" do especialista → output especializado.

**Elementos de uma skill rica:**
- Canon (princípios fundamentais do especialista/método)
- Sete pilares do método
- O que ele acredita / teses centrais
- Formas de falar / voz específica
- Narrativa / arco de comunicação
- Protocolos de ação
- Diferenças de adaptação cultural (ex: Brasil vs. outros)

### Skill dentro de skill

*"É um prompt que você pode colocar as referências. Daí você vai colocando o canon dele, os sete pilares, o que que ele entende, as formas dele falar, as duas faces, a narrativa, o que ele acredita, a voz, os protocolos, os partners, as diferenças."*

### Personificação de especialistas

Felipe não usa "escreva como um redator de e-mail." Ele pesquisa especialistas reais:
- **Richard Feynman** → skill de revisão didática (explicação de conceitos complexos)
- **Alex Hormozi** → skill de ofertas (destilou 3 livros em EPUB + método)
- **Arthur Miller** → skill de narrativa (comprou e destilou o curso)

Coloca o especialista dentro da skill → IA acessa o cluster de parâmetros desse especialista especificamente.

### Paperclip — empresa de agentes

Sistema multi-agente organizado como empresa:
- Especialistas (skills personificadas)
- Squads
- Canons
- Sensores
- MCP servers

Você entrega uma "empresa de agentes" ao cliente, não uma skill avulsa.

## O que está morrendo

- Vender template de n8n / workflow avulso
- "Prompt engineer"
- Instalação de chatbot como serviço
- Ferramental sem estratégia

## O que está surgindo

- **Context engineer** — quem sabe estruturar contexto, não só prompt
- Skills calibradas por nicho com canon de especialistas
- Agentes que decidem seu próprio workflow (n8n vira braço de execução, não orquestrador)
- Vender resultado de nicho, não ferramenta

## O modelo Marcelo

Cliente real: especialista em reciclagem de eletrônicos. Usa Claude com prompts em Word + planilha. Não sabe o que é n8n. Empacotou conhecimento de nicho em sistema de agentes e vende como franquia. Fatura bem.

**Moral:** conhecimento profundo de nicho + Claude Code = produto escalável sem equipe técnica.

## Relação com XPLATFORM

O XPF já implementa o que Felipe está ensinando:
- Multi-agente (CC + Hermes + OPEN) = Paperclip
- Skills com canon = o que ele está construindo
- MASTER_RULES + hooks = context engineering em produção
- N8N como braço de execução = já na regra `automacao-vs-ia.md`

Felipe está construindo o produto. Jefferson já usa o sistema em produção como lab de resultados pessoais.

## Links e referências

- Vídeo: https://www.youtube.com/watch?v=6ZgQJ-_3Iwk
- Skills marketplace Claude Code: https://agentskills.io
- Paperclip: sistema de agentes (pesquisar mais)
