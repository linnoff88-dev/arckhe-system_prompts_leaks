# Plano de Educaçêo: Padrões e Evoluçêo de System Prompts

> Baseado na análise do repositório `system_prompts_leaks` (248 arquivos, ~221 mil linhas, 13 fornecedores, 562 commits de evoluçêo). Objetivo: criar uma cultura educacional para entender, de forma profunda e didática, os padrões de system prompts — e capacitar pessoas a construir sistemas cada vez mais robustos **e** simples.
>
> **Revisêo (2026-06-11):** o curso passou de 1 trilha (5 módulos) para **4 trilhas** com conteúdo aprofundado por tópico. Motivo: estes sêo conhecimentos profundos e novos — cada padrêo e cada diff merece explicaçêo substantiva, nêo apenas um título. As trilhas 1–4 abaixo trazem, por módulo, o **conteúdo detalhado** (a substância a ensinar), nêo só a ementa.

---

## 1. Diagnóstico: o que o repositório ensina

### 1.1 O acervo

| Eixo | O que existe | Valor didático |
|------|--------------|----------------|
| **Séries evolutivas** | Claude Opus 4.6→4.7→4.8→Fable 5; GPT-5.x→5.5; Gemini 2.0→3.5; Grok 3→4.3 | Estudar **evoluçêo por diff** — o que cada geraçêo aprendeu |
| **Categorias de produto** | Chatbots, agentes de código, buscadores, office, voice, CLI | Estudar **especializaçêo** — como o mesmo padrêo muda por contexto |
| **Fornecedores** | Anthropic, OpenAI, Google, Microsoft, Cursor, Perplexity, xAI, Notion… | Estudar **filosofias de design** comparadas |
| **Variantes** | raw/no-tools/thinking/api, personalidades GPT, personas Grok | Estudar **modularidade** — o que entra e sai por canal |

### 1.2 A grande tendência observada (2024→2026)

A evoluçêo dos prompts conta uma história clara, que é a tese central do curso:

1. **De regras negativas para princípios com porquê.** "Never X" vira "Claude evita X porque Y". Modelos mais capazes obedecem melhor a princípios justificados do que a listas de proibições.
2. **Consolidaçêo > acúmulo.** Fable 5 *removeu* 7 blocos do Opus 4.8 e consolidou (2 blocos de copyright → 1 princípio; 4 micro-regras de tom → 1 postura). Robustez veio de **simplificar**, nêo de empilhar regras.
3. **Comunicaçêo e autonomia como seções de primeira classe.** O Claude Code ganhou seções dedicadas a "como comunicar" e "como agir sem perguntar" — o gargalo deixou de ser capacidade e passou a ser interaçêo.
4. **Segurança em nível de padrêo, nêo de mecânica.** Em vez de listar termos proibidos, descreve o *padrêo* a detectar e o princípio a aplicar — porque listar a mecânica de detecçêo é um script para o atacante.
5. **Separaçêo harness × comportamento.** `<system-reminder>` (injetado pela plataforma) vs instruções estáveis — arquitetura em camadas.

---

## 2. O Catálogo de Padrões (vocabulário comum)

Tal como os *Design Patterns* da engenharia de software, cada padrêo é uma **ficha nomeada** (pattern card) com formato fixo. As 12 fichas já existem em `educacao/fichas/`.

```
NOME · Problema que resolve · Soluçêo · Exemplo real (arquivo:trecho do repo)
Antipadrêo correspondente · Quando NêO usar · Visto em: [fornecedores]
```

### Os 12 padrões fundamentais

| # | Padrêo | Ideia em 1 linha | Visto em |
|---|--------|------------------|----------|
| 1 | **Bloco de Identidade** | "You are X" — persona, modelo e data de corte no topo | Todos |
| 2 | **Declaraçêo de Capacidades** | Lista estruturada de ferramentas com escopo e limites | xAI, Google, Microsoft, Notion |
| 3 | **Regra com Porquê** | Instruçêo + justificativa generaliza melhor que proibiçêo seca | Anthropic, OpenAI |
| 4 | **Contraste ALWAYS/NEVER** | Caps reservados a comportamentos críticos | Cursor, Microsoft |
| 5 | **Compartimento XML** | Tags `<bloco>` flat para modularidade lógica | Anthropic, xAI, Google |
| 6 | **Regra por Exemplo** | Schema/exemplo inline elimina ambiguidade | Notion, Google, Microsoft |
| 7 | **Orçamento de Concisêo** | Limite explícito de tamanho/formato de saída | xAI, Perplexity, Claude Code |
| 8 | **Contrato de Ferramenta** | Quando chamar, em que ordem, como agrupar chamadas | xAI, Notion, Claude Code |
| 9 | **Preservaçêo de Fonte** | Citações/textos externos intocados | Perplexity, xAI, Anthropic |
| 10 | **Lembrete de Sistema** | Camada dinâmica injetada pelo harness | Anthropic, xAI |
| 11 | **Hierarquia de Prioridade** | Usuário > skill/plugin > default — quem manda no conflito | xAI, Anthropic, Microsoft |
| 12 | **Princípio Consolidado** | Fundir blocos redundantes num princípio (anti-inchaço) | Fable 5 (copyright, tom) |

### Os 5 antipadrões

**Prompt-cebola** (empilhar sem remover) · **Proibiçêo sem porquê** · **Regra-mecânica de segurança** (listar termos ensina a contornar) · **Formataçêo como muleta** · **Tudo-no-prompt** (misturar dinâmico com estável). Mais o antipadrêo honorário: **Inflaçêo de ênfase** (quando tudo é `CRITICAL`, nada é).

---

## 3. Estrutura do curso: 4 trilhas

> Formato INEMA.CLUB (trilhas → módulos → tópicos), cada módulo com vídeo + página + laboratório.
> Cada módulo abaixo traz: **Objetivo · Conteúdo detalhado · Exemplos reais (arquivo) · Atividade · Entregável.**

### Mapa das trilhas

| Trilha | Tema | Módulos | Papel |
|--------|------|---------|-------|
| **1** | Anatomia & Catálogo de Padrões | 4 | Vocabulário — o que um prompt tem e como nomear cada peça |
| **2** | Evoluçêo por Diffs | 5 | O diferencial deste acervo — aprender com mudanças reais |
| **3** | Filosofias Comparadas & Especializaçêo | 3 | Visêo comparada entre fornecedores e tipos de produto |
| **4** | Construindo o Seu: Robusto e Simples | 4 | Laboratório — aplicar tudo num prompt versionado |

---

## Trilha 1 — Anatomia & Catálogo de Padrões *(fundamentos)*

> Objetivo da trilha: dar ao aluno o **vocabulário** para ler qualquer system prompt e nomear cada peça. Sem isso, os diffs da Trilha 2 sêo ruído.

### Módulo 1.1 — Anatomia de um System Prompt
- **Objetivo:** reconhecer as 6 seções universais que aparecem (em ordem variável) em quase todo prompt de produçêo.
- **Conteúdo detalhado:**
  - **Identidade** — "You are X", modelo, data de corte, persona. Por que vem no topo: ancora todo o resto.
  - **Capacidades** — o que o modelo *pode* fazer (ferramentas, modalidades) e seus limites.
  - **Segurança/recusa** — onde e como declinar; a parte que mais evoluiu (Trilha 2).
  - **Formato/tom** — concisêo, prosa vs listas, voz.
  - **Ferramentas** — contratos de uso (quando/como chamar).
  - **Contexto dinâmico** — data, usuário, avisos injetados pelo harness (separado do comportamento estável).
  - Insight central: a *ordem* e o *peso* dessas seções revelam a filosofia do fornecedor.
- **Exemplos reais:** `Cursor/cursor.md` (322 linhas, o menor "completo" — ideal para dissecar inteiro); contraste com `Anthropic/claude-fable-5.md` (3.825 linhas) para mostrar escala.
- **Atividade:** dissecaçêo guiada — colorir cada seçêo de `cursor.md` por funçêo.
- **Entregável:** mapa anatômico de um prompt à escolha do aluno.

### Módulo 1.2 — Catálogo Parte 1: Padrões Estruturais
- **Objetivo:** dominar os 5 padrões que dêo **forma** ao prompt (independentes de domínio).
- **Conteúdo detalhado:** padrões 1 (Identidade), 2 (Capacidades), 5 (Compartimento XML), 10 (Lembrete de Sistema), 11 (Hierarquia de Prioridade). Para cada um: problema → soluçêo → trecho real → antipadrêo.
  - Foco no padrêo 5 (XML flat) como a "gramática estrutural" da Anthropic e xAI.
  - Foco no padrêo 11 (precedência) como o que resolve conflito usuário × skill × default — base de qualquer harness.
- **Exemplos reais:** `Anthropic/anthropic_reminders.md` (padrêo 10 isolado); `xAI/grok-4.3-beta.md` (XML + capacidades); `Microsoft/github-copilot.md` (hierarquia).
- **Atividade:** "caça ao padrêo" — achar cada um dos 5 em 2 fornecedores diferentes.
- **Entregável:** 5 trechos anotados (um por padrêo).

### Módulo 1.3 — Catálogo Parte 2: Padrões Comportamentais
- **Objetivo:** dominar os 7 padrões que governam **como o modelo age e fala**.
- **Conteúdo detalhado:** padrões 3 (Regra com Porquê), 4 (ALWAYS/NEVER), 6 (Regra por Exemplo), 7 (Orçamento de Concisêo), 8 (Contrato de Ferramenta), 9 (Preservaçêo de Fonte), 12 (Princípio Consolidado).
  - O eixo da trilha inteira já aparece aqui: **3 vs 4** (porquê vs proibiçêo seca) e **12** (consolidar) sêo a direçêo para onde os fornecedores caminharam.
  - Contrato de ferramenta (8): quando chamar, ordem, batching de chamadas paralelas.
- **Exemplos reais:** `Perplexity/comet-browser-assistant.md` (padrêo 9, citações); `Notion/notion-ai.md` (padrêo 6, schema inline); `Anthropic/Claude Code/claude-code-2.1.172-fable-5.md` (padrões 7 e 8).
- **Atividade:** reescrever uma "proibiçêo sem porquê" como "regra com porquê".
- **Entregável:** ficha de padrêo escrita pelo próprio aluno (contribuível ao material).

### Módulo 1.4 — Os Antipadrões
- **Objetivo:** reconhecer e nomear os 5 antipadrões + inflaçêo de ênfase — saber o que **nêo** fazer.
- **Conteúdo detalhado:** prompt-cebola, proibiçêo sem porquê, regra-mecânica de segurança, formataçêo como muleta, tudo-no-prompt; cada um com sintoma e antídoto (padrêo correspondente). A inflaçêo de ênfase como termômetro de maturidade do prompt.
- **Exemplos reais:** o próprio diff 4.8→Fable 5 é o contraexemplo vivo (a consolidaçêo desfaz a cebola). Comparar densidade de `CRITICAL`/`NEVER` entre `claude-opus-4.8.md` e `claude-fable-5.md`.
- **Atividade:** auditar um prompt e marcar cada antipadrêo encontrado.
- **Entregável:** relatório de antipadrões de um prompt real.

---

## Trilha 2 — Evoluçêo por Diffs *(o diferencial deste acervo)*

> Objetivo da trilha: ensinar a ler a **história** dentro de um diff de prompt. Cada mudança responde a "que problema do mundo real motivou isso?". Base pronta: `educacao/diff-anotado-opus-4.8-fable-5.md` (14 mudanças comentadas + 5 lições).

### Módulo 2.1 — Como ler um diff de prompt (método)
- **Objetivo:** instalar o método de leitura: para cada linha mudada, inferir motivaçêo e extrair a liçêo generalizável.
- **Conteúdo detalhado:**
  - Os 4 tipos de mudança: **adiçêo**, **remoçêo**, **reescrita**, **renomeaçêo de bloco**.
  - A regra de leitura: *toda remoçêo é informaçêo* — o que saiu costuma ter sido internalizado pelo treino (vira ruído) ou consolidado.
  - "Evoluir ≠ crescer": 4.8→Fable 5 teve muito conteúdo novo e saldo de **+56 linhas** porque 7 blocos foram removidos.
  - O nome de um bloco também é instruçêo (ex.: `compliance` → `principle`).
- **Exemplos reais:** `educacao/diff-anotado-opus-4.8-fable-5.md` (linha a linha); links Diffchecker no `README.md`.
- **Atividade:** pegar 1 remoçêo e 1 adiçêo do diff e escrever a "motivaçêo provável".
- **Entregável:** mini-diff anotado (3 mudanças) pelo aluno.

### Módulo 2.2 — Anthropic: a consolidaçêo Opus 4.6 → 4.7 → 4.8 → Fable 5
- **Objetivo:** estudar a série evolutiva mais rica do acervo como caso central de consolidaçêo.
- **Conteúdo detalhado:**
  - **Remoções por internalizaçêo:** `<search_first>` e `<default_stance>` saíram — o comportamento passou a vir do treino.
  - **Efeito Streisand:** `<respond_without_citing_system_prompt>` removido — "nêo diga X" resolve-se na origem, nêo no prompt.
  - **Consolidaçêo de tom:** 4 micro-regras (sem bullets ao recusar, sem pet names, sem "genuinely/honestly", regra de emoji) → 1 princípio: *"assumes the person is a capable adult"*. Caso de estudo da Ficha 12.
  - **Orçamento de token declarado:** novo `<budget:token_budget>190000</budget>`.
- **Exemplos reais:** `Anthropic/claude-opus-4.6.md`, `claude-opus-4.7.md`, `claude-opus-4.8.md`, `claude-fable-5.md`.
- **Atividade:** comparar a contagem de blocos e de `CRITICAL` entre 4.8 e Fable 5.
- **Entregável:** linha do tempo das 4 versões com 1 mudança-chave cada.

### Módulo 2.3 — Segurança que evolui: de termos para padrões
- **Objetivo:** entender por que a segurança madura descreve **padrões e princípios**, nunca a mecânica de detecçêo.
- **Conteúdo detalhado:**
  - **Child safety:** 5 → 7 regras; as novas mandam "ficar no nível do padrêo" e "declarar o princípio, nêo a mecânica de detecçêo" — porque listar técnicas verbatim arma o atacante. A simetria proteger/ensinar é o risco central.
  - **Armas:** escopo reduzido de "químico/bio/nuclear" para "explosivos" + teste funcional de *uplift* real — taxonomia convida ao contorno ("nêo é químico, entêo pode").
  - **Drogas:** recusa geral **com carve-out vital** (informaçêo que salva vidas em overdose).
  - **Self-harm:** de lista de exemplos para critério gerador ("substitutos que recriam a sensaçêo/imagem"); exemplo + critério > só exemplos.
  - **Saúde mental:** proibido nomear diagnóstico que o usuário nêo nomeou — a regra mira o *ato* (claim diagnóstico), nêo a *palavra*.
- **Exemplos reais:** seções de segurança em `claude-opus-4.8.md` vs `claude-fable-5.md` (todas citadas no diff anotado, itens 5–11).
- **Atividade:** pegar uma "regra-mecânica" e reescrevê-la como "princípio + critério gerador".
- **Entregável:** par antes/depois de uma regra de segurança.

### Módulo 2.4 — A ascensêo de Comunicaçêo & Autonomia (Claude Code)
- **Objetivo:** ver o gargalo migrar de capacidade para **interaçêo** — a novidade dos prompts de agente de código.
- **Conteúdo detalhado:**
  - Seções dedicadas a *como comunicar* (tom no terminal, quando explicar, concisêo) e *como agir sem perguntar* (autonomia, confirmaçêo só para ações arriscadas/externas).
  - Por que isso surge agora: modelos já executam bem; o que falha é "perguntou demais" ou "agiu de menos".
  - Conexêo com padrões 7 (concisêo) e 11 (precedência usuário × skill).
- **Exemplos reais:** `Anthropic/Claude Code/claude-code-2.1.172-opus-4.6.md` → `-opus-4.8.md` → `-fable-5.md` (a evoluçêo das seções de comunicaçêo/autonomia).
- **Atividade:** localizar a seçêo de autonomia e listar 3 regras de "quando confirmar".
- **Entregável:** resumo da política de autonomia de um agente.

### Módulo 2.5 — Caso OpenAI: personalidades e a família GPT-5.x → 5.5
- **Objetivo:** estudar uma filosofia diferente da Anthropic — **persona modular** e variantes por canal.
- **Conteúdo detalhado:**
  - O sistema de **personalidades**: como a OpenAI separa comportamento-base de "tempero" de persona.
  - Variantes por canal/esforço: instant vs thinking vs api vs pro — o que entra e sai em cada uma (padrêo de modularidade).
  - Contraste com a Anthropic: regras curtas + persona vs princípios longos justificados.
- **Exemplos reais:** `OpenAI/4o-2025-09-03-new-personality.md`, `OpenAI/gpt-5.1-quirky.md`, `OpenAI/gpt-5.1-candid.md`, `OpenAI/gpt-5.5-instant.md`, `OpenAI/gpt-5.5-api.md`, `OpenAI/gpt-5.5-pro-api.md`.
- **Atividade:** diff entre duas personalidades GPT — o que muda, o que permanece.
- **Entregável:** mapa do que é "base" vs "persona" num par de variantes.

---

## Trilha 3 — Filosofias Comparadas & Especializaçêo *(visêo comparada)*

> Objetivo da trilha: o mesmo problema tem soluções diferentes por fornecedor e por tipo de produto. Aprender a **comparar** é aprender a escolher.

### Módulo 3.1 — Quatro filosofias de design
- **Objetivo:** caracterizar a "assinatura" de cada fornecedor.
- **Conteúdo detalhado:**
  - **Anthropic** — princípios longos com porquê; consolidaçêo; segurança por padrêo.
  - **OpenAI** — regras curtas + persona modular; variantes por canal.
  - **Google / Microsoft** — estrutura + procedimento; schema e passo-a-passo (regra por exemplo forte).
  - **xAI** — concisêo opinativa; personas; XML estrutural.
- **Exemplos reais:** `Anthropic/claude-fable-5.md`, `OpenAI/gpt-5.5-instant.md`, `Google/gemini-3.1-pro.md`, `Microsoft/vscode-copilot-agent.md`, `xAI/grok-4.3-beta.md` + `xAI/grok-personas.md`.
- **Atividade:** classificar um trecho "cego" (sem nome) por filosofia.
- **Entregável:** quadro das 4 assinaturas com 1 evidência cada.

### Módulo 3.2 — Especializaçêo por tipo de produto
- **Objetivo:** ver como o mesmo padrêo muda de chatbot para agente, buscador, office, voice e CLI.
- **Conteúdo detalhado:**
  - **Chatbot** (tom, recusa) vs **agente de código** (autonomia, contrato de ferramenta) vs **buscador** (preservaçêo de fonte, citaçêo) vs **office** (formato estruturado) vs **voice** (concisêo extrema, sem markdown) vs **CLI** (orçamento de saída).
  - O que cada contexto *adiciona* e o que *remove* do núcleo.
- **Exemplos reais:** `Perplexity/comet-browser-assistant.md` (buscador), `Anthropic/claude-for-excel.md` / `claude-for-word.md` (office), `Perplexity/voice-assistant.md` (voice), `Microsoft/copilot-cli.md` (CLI).
- **Atividade:** mesma tarefa, comparar a regra de formato em voice vs office.
- **Entregável:** tabela "o que muda por produto" para 3 padrões.

### Módulo 3.3 — Matriz comparativa: um problema, quatro respostas
- **Objetivo:** consolidar a trilha numa matriz que vira ferramenta de consulta.
- **Conteúdo detalhado:** pegar 3 problemas universais (ex.: "quando recusar", "como citar fonte", "como decidir agir sem perguntar") e mapear a soluçêo de 4 fornecedores lado a lado — expondo trade-offs.
- **Exemplos reais:** trechos das 4 filosofias do módulo 3.1.
- **Atividade:** preencher uma célula nova da matriz com um quinto fornecedor.
- **Entregável:** matriz comparativa 3×4 publicável.

---

## Trilha 4 — Construindo o Seu: Robusto e Simples *(laboratório)*

> Objetivo da trilha: aplicar tudo. Método central — **prompt mínimo viável → evoluçêo por diff → consolidaçêo periódica**, versionado em git. O histórico do aluno vira o seu próprio "repo de evoluçêo".

### Módulo 4.1 — O prompt mínimo viável
- **Objetivo:** escrever o menor prompt que funciona — só identidade + 1 contrato.
- **Conteúdo detalhado:** resistir ao impulso de antecipar regras; começar pelo núcleo; definir critério de "funciona" (um teste concreto).
- **Atividade:** escrever o MVP e rodar o primeiro teste.
- **Entregável:** `prompt-v0` + 1 teste.

### Módulo 4.2 — Evoluçêo por diff e rodadas de consolidaçêo
- **Objetivo:** crescer por necessidade real, nêo por antecipaçêo — e consolidar antes de inchar.
- **Conteúdo detalhado:** ciclo: testar → achar falha real → corrigir com **um** padrêo do catálogo (nunca "mais uma regra solta") → a cada 3 adições, **1 rodada de consolidaçêo** (imitando 4.8→Fable 5).
- **Atividade:** 3 ciclos de adiçêo + 1 consolidaçêo documentada.
- **Entregável:** changelog com motivaçêo por mudança.

### Módulo 4.3 — Testes e o "porquê documentado" (regra de ouro)
- **Objetivo:** instalar a disciplina que espelha a direçêo dos fornecedores.
- **Conteúdo detalhado:** a **regra de ouro da cultura** — *toda regra adicionada precisa de um porquê documentado e de um teste que falharia sem ela*. Sem teste, a regra nêo entra; sem porquê, nêo generaliza.
- **Atividade:** escrever o teste-que-falharia para cada regra do próprio prompt.
- **Entregável:** suíte mínima de testes vinculada ao changelog.

### Módulo 4.4 — Projeto final: system prompt versionado
- **Objetivo:** entregar um prompt de produçêo pequeno, robusto e justificado.
- **Conteúdo detalhado:** consolidar o repo do aluno — prompt + changelog (cada mudança rotulada pelo padrêo) + testes. Critério de qualidade: comportamento mantido com **menos** linhas que o rascunho intermediário.
- **Atividade:** rodada final de consolidaçêo medindo por testes, nêo por opiniêo.
- **Entregável final:** repo-modelo (prompt mínimo + testes + changelog justificado por padrêo).

---

## 4. Cultura: rituais e práticas contínuas

A trilha ensina; a **cultura** sustenta. Práticas leves e recorrentes:

1. **Diff da Semana** — a cada versêo nova (ex.: Fable 5), análise curta: o que entrou, o que saiu, qual padrêo explica. Insumo pronto: "Recently Updated" + links de diff no `README.md`.
2. **Clube de Dissecaçêo** — sessêo mensal: um prompt, leitura coletiva, mapear padrões ao vivo.
3. **Glossário vivo** — os 12 padrões + 5 antipadrões abertos a contribuições (já em `educacao/glossario.md`).
4. **Desafio de Consolidaçêo** — reduzir um prompt inchado mantendo o comportamento (medido por testes).
5. **Regra de ouro:** *toda regra adicionada precisa de um porquê documentado e de um teste que falharia sem ela* — espelhando a direçêo que os fornecedores tomaram.

---

## 5. Estado atual (o que já existe)

| Artefato | Local | Status |
|----------|-------|--------|
| Glossário (12 padrões + 5 antipadrões) | `educacao/glossario.md` | ✅ feito |
| 12 fichas de padrêo | `educacao/fichas/01..12` | ✅ feito |
| Diff anotado 4.8→Fable 5 (14 mudanças + 5 lições) | `educacao/diff-anotado-opus-4.8-fable-5.md` | ✅ feito |
| Trilha 1 (3 páginas: anatomia, catálogo, diffs) | `educacao/curso/trilha1/` | ⚠️ feito na estrutura antiga — **rever** |
| Redirect raiz → curso | `index.html` | ✅ no ar (GitHub Pages via Actions) |

> **Nota de migraçêo:** a `trilha1/` atual junta Anatomia + Catálogo + Diffs numa só trilha. Na nova estrutura, **Diffs vira a Trilha 2** e o Catálogo se desdobra em 2 módulos (estruturais/comportamentais) + 1 de antipadrões. As 3 páginas atuais viram a base — nêo se joga nada fora, redistribui-se.

---

## 6. Roadmap revisado

- **Fase 1 — ✅ concluída:** glossário + 12 fichas + diff anotado.
- **Fase 2 — Trilha 1 completa (4 módulos):** reaproveitar as páginas atuais, dividir o catálogo em 2 + acrescentar o módulo de antipadrões. Formato INEMA.CLUB (skill `formato-curso`).
- **Fase 3 — Trilha 2 (5 módulos):** o coraçêo novo do curso; partir do diff anotado já pronto e expandir para a série 4.6→Fable 5, segurança, Claude Code e OpenAI.
- **Fase 4 — Trilhas 3 e 4:** filosofias/especializaçêo + laboratório com template de repo.
- **Fase 5 — Vídeos e rituais:** 1 vídeo por módulo (`videos-cursos-inema`) + primeiro "Diff da Semana" + abertura do glossário a contribuições.

---

## 7. Princípio norteador (resumo de 1 parágrafo)

O acervo prova que os melhores system prompts de 2026 nêo sêo os mais longos — sêo os mais **consolidados, justificados e em camadas**. A educaçêo deve espelhar isso: ensinar por padrões nomeados (vocabulário comum, Trilha 1), por diffs (evoluçêo real, nêo teoria, Trilha 2), por comparaçêo (filosofias e produtos, Trilha 3) e por laboratório iterativo (adicionar pouco, consolidar sempre, Trilha 4). Quem aprende assim constrói sistemas robustos *porque* sêo simples, nêo apesar disso.
