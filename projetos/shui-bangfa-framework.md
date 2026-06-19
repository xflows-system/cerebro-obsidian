# PHILOSOPHY.md — Shui-Bangfa (水兵法)

*Arquitetura de sistema derivada de filosofia chinesa. Desenvolvida por Jefferson (Xflows AI).*
*Princípio central: macro e micro aplicam os mesmos padrões. Zoom in ou zoom out — o framework se repete.*

---

## Propósito

| Dimensão | O que resolve |
|---|---|
| **Humano** | Liberta o Operador do trabalho maquinal e repetitivo — foco no estratégico |
| **Mercado** | Transforma automação em método proprietário — ativo valioso, não commodity |
| **Criador** | Maestria sobre o caos — ordenar entropia tecnológica em rio digital sustentável |

---

## Princípio: Fratabilidade (Macro no Micro)

O mesmo framework governa todos os níveis simultaneamente.

| Nível | Exemplo |
|---|---|
| Sistema | Como Hermes decide se dispara uma campanha |
| Módulo | Como o qualificador classifica um lead |
| Nó | Como uma condição individual é avaliada (booleano → score) |
| Coluna de DB | Regra de higienização de input |

**No Micro (A Célula):** cada nó, coluna ou função cumpre papel cego, rígido e isolado.
**No Macro (O Organismo):** a soma dessas regras micro, governadas pela mesma filosofia, faz o ecossistema ganhar autonomia. O cliente final não enxerga código — enxerga um agente inteligente.

Fractal: a mesma lógica de Shui, Wu Wei e Bangfa opera em todos os níveis.

---

## Shui (水) — Resiliência e Fluxo

**Princípio filosófico:** Água encontra caminho, não força passagem. Adapta forma ao container. Erode com persistência, não com força.

**Tradução técnica:** O dado deve contornar obstáculos. O fluxo deve chegar ao fim — sem travar, sem duplicar, sem perder informação.

### Implementação

- Error handling robusto em todos os nós — nunca deixar o fluxo morrer silenciosamente
- Condicionais (IFs) e modos de contingência: `Append + Continue se Vazio` em vez de falha
- Garantir que o webhook de resposta sempre dispara, mesmo em caminho alternativo
- Retry com backoff exponencial — nunca hammer
- Escala por demanda — não ligado 24/7 gastando recurso

### Qi Score

Score contínuo 0–100 que representa o estado energético de uma entidade (lead, projeto, campanha).

**Fórmula base:**

```
Qi = (W_interacao × score_interacao)
   + (W_resposta   × score_resposta)
   + (W_tempo      × score_decaimento_temporal)
```

| Componente | Peso padrão | O que mede |
|---|---|---|
| `score_interacao` | 0.5 | Frequência e profundidade de contato |
| `score_resposta` | 0.3 | Velocidade e qualidade da resposta |
| `score_decaimento_temporal` | 0.2 | Recência — Qi decai com inatividade |

> Pesos são ajustáveis por projeto. Defaults acima são para pipeline de leads WhatsApp/Instagram.

**Intervalos de referência:**

| Qi | Estado | Interpretação |
|---|---|---|
| 70–100 | Flowing | Ação natural permitida |
| 40–69 | Potential | Monitorar, não forçar |
| 15–39 | Stagnant | Intervenção só se Bangfa autorizar |
| 0–14 | Dead/Transmuted | Não deletar — arquivar com estado `transmuted` |

### Quatro Fases — State Machine

```
new → flowing → stagnant → dead → transmuted
        ↑______________|
        (reativação por evento)
```

| Transição | Gatilho |
|---|---|
| `new → flowing` | Primeiro contato + Qi > 40 |
| `flowing → stagnant` | Qi < 40 por N dias (padrão: 7) |
| `stagnant → dead` | Sem interação por M dias (padrão: 30) |
| `dead → transmuted` | Arquivamento explícito — dados preservados |
| `stagnant → flowing` | Evento de reativação + Qi volta acima de 40 |

> **Regra inviolável:** nunca hard-delete. `transmuted` é o estado final — dado vira aprendizado.

---

## Wu Wei (無為) — Eficiência e Event-Driven

**Princípio filosófico:** Não é "não fazer nada". É "não forçar". Ação emerge do momento certo, não da vontade de agir.

**Tradução técnica:** O sistema só ativa quando há evento real. Evita desperdício de processamento, memória e custo de tokens.

### Implementação

- Filtros iniciais obrigatórios antes de qualquer processamento com IA:
  - `fromMe = false` — não processar mensagens próprias
  - Restrição de grupos — só processar o que é relevante
  - Verificação de sinal de interesse antes de qualquer outbound
- Broadcast só quando Qi > 30 — nunca por volume ou agenda arbitrária
- IA entra apenas onde há julgamento — automação pura onde a regra é clara

### Gate de Execução

Antes de qualquer ação automática:

```
Existe sinal natural de interesse recente?
  SIM → executa (flow)
  NÃO → Wu Wei: bloqueia — aguarda sinal ou escala para Bangfa
```

Toda ação bloqueada é logada como `type: flow | result: blocked | reason: wu_wei`.
Bloqueios são tão importantes quanto execuções — auditar o que *não* aconteceu revela saúde do sistema.

---

## Bangfa (兵法) — Governança e Rigidez

**Princípio filosófico:** A lei militar não é brutalidade — é disciplina que permite vitória sem desperdício.

**Tradução técnica:** A base sólida onde a IA pisa. Regras determinísticas e inabaláveis que tornam o sistema previsível e auditável.

### Implementação

- Regras determinísticas no banco (Supabase/Postgres) — sem lógica implícita fora do schema
- Higienização rigorosa de inputs: `replace("'", "''")`, tratamento de nulos, validação na borda
- Proibição de nós genéricos ou soltos na arquitetura — cada componente tem responsabilidade única
- Schema como contrato — o que não está definido, não existe

### Terreno

Classificação de alvos antes de agir:

| Terreno | Critério | Ação |
|---|---|---|
| Alto/Fácil | Qi > 70 + histórico positivo | Entrar direto |
| Alto/Difícil | Qi > 70 + resistência conhecida | Preparar antes de avançar |
| Baixo/Fácil | Qi 40–70 + sem objeções | Nutrir, não fechar |
| Baixo/Difícil | Qi < 40 + resistência | Wu Wei — não gastar energia |

### Override de Wu Wei (Fogo)

Bangfa pode forçar ação que Wu Wei bloquearia — mas com obrigações:

1. Operador aprova — ou
2. Log obrigatório: `type: battle | result: forced | authorized_by: [quem]`

Bangfa nunca age silenciosamente. O que foi forçado fica registrado.

---

## Tabelas de Log

| Log | Tabela | Quando |
|---|---|---|
| `flow` | `rituals` | Ação aconteceu naturalmente (Qi aprovado) |
| `battle` | `campaigns` | Ação foi forçada por Bangfa |
| `blocked` | `rituals` | Wu Wei bloqueou — também é evento |

---

## Mapeamento na Stack XPLATFORM

| Conceito | Status |
|---|---|
| Wu Wei gate | ✅ ATIVO — `~/.hermes/SOUL.md §3.5` |
| Qi score | A implementar — fórmula definida, aguarda dados reais |
| State machine | A implementar — estados de lead/projeto |
| Bangfa/Governança | Parcial — schema Supabase quando projeto escalar |
| flow log | A implementar |
| battle log | A implementar |

---

## O que NÃO é este framework

- Não é gamificação — Qi não é recompensa, é medição
- Não é budismo — é pragmatismo com vocabulário preciso
- Não substitui métricas de negócio — convive com elas

---

## Ordem de Implementação

1. **Wu Wei gate** ✅ — portão de ação natural (ativo no Hermes)
2. **State machine** — 4 estados + transições automáticas
3. **Qi score** — fórmula concreta + decaimento temporal (só quando houver dados)
4. **flow log** — registrar tudo que acontece naturalmente
5. **Bangfa + battle log** — só quando há escala para justificar

*Shui primeiro. Bangfa depois. Essa é a sequência natural.*
