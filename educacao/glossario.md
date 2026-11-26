# Glossário: 12 Padrões + 5 Antipadrões de System Prompts

> Vocabulário comum para ler, discutir e construir system prompts. Cada padrêo tem uma [ficha detalhada](fichas/) com exemplos reais deste repositório.

## Os 12 padrões

| # | Padrêo | Ideia em 1 linha | Visto em |
|---|--------|------------------|----------|
| 1 | [Bloco de Identidade](fichas/01-bloco-de-identidade.md) | "You are X" — persona, modelo e data de corte declarados no topo | Todos |
| 2 | [Declaraçêo de Capacidades](fichas/02-declaracao-de-capacidades.md) | Lista estruturada de ferramentas com escopo e condições | xAI, Google, Microsoft, Notion |
| 3 | [Regra com Porquê](fichas/03-regra-com-porque.md) | Instruçêo + justificativa explícita generaliza melhor que proibiçêo seca | Anthropic, OpenAI |
| 4 | [Contraste ALWAYS/NEVER](fichas/04-contraste-always-never.md) | Ênfase em caps reservada a comportamentos críticos | Cursor, Microsoft |
| 5 | [Compartimento XML](fichas/05-compartimento-xml.md) | Tags `<bloco>` flat para modularizar a lógica do prompt | Anthropic, xAI, Cursor, Google |
| 6 | [Regra por Exemplo](fichas/06-regra-por-exemplo.md) | Exemplo embutido (schema, formato) elimina ambiguidade | Notion, Google, Microsoft |
| 7 | [Orçamento de Concisêo](fichas/07-orcamento-de-concisao.md) | Limite explícito de tamanho/formato de saída | xAI, Perplexity, Claude Code |
| 8 | [Contrato de Ferramenta](fichas/08-contrato-de-ferramenta.md) | Quando chamar, em que ordem, como encadear e agrupar | xAI, Notion, Claude Code |
| 9 | [Preservaçêo de Fonte](fichas/09-preservacao-de-fonte.md) | Citações e textos externos intocados, com mecanismo formal | Perplexity, xAI, Anthropic |
| 10 | [Lembrete de Sistema](fichas/10-lembrete-de-sistema.md) | Camada dinâmica injetada pelo harness, separada do comportamento estável | Anthropic, xAI |
| 11 | [Hierarquia de Prioridade](fichas/11-hierarquia-de-prioridade.md) | Quem manda quando instruções conflitam — precedência declarada | xAI, Anthropic, Microsoft |
| 12 | [Princípio Consolidado](fichas/12-principio-consolidado.md) | Fundir regras redundantes num princípio único (anti-inchaço) | Anthropic (Fable 5) |

## Os 5 antipadrões

| Antipadrêo | Sintoma | Antídoto |
|------------|---------|----------|
| **Prompt-cebola** | Cada bug vira uma regra nova; nada é removido; o prompt só cresce | Padrêo 12 (Princípio Consolidado) — rodada de consolidaçêo periódica |
| **Proibiçêo sem porquê** | "Never X" seco; o modelo contorna porque nêo entende a intençêo | Padrêo 3 (Regra com Porquê) |
| **Regra-mecânica de segurança** | Listar termos/técnicas proibidos — ensina exatamente o que evitar dizer | Descrever o *padrêo* a detectar e o princípio a aplicar (ver child safety no Fable 5) |
| **Formataçêo como muleta** | Forçar listas/headers/emoji em tudo; resposta vira esqueleto sem prosa | Padrêo 7 (Orçamento de Concisêo) + tom de "prosa primeiro" |
| **Tudo-no-prompt** | Contexto dinâmico (data, usuário, avisos) misturado com comportamento estável | Padrêo 10 (Lembrete de Sistema) — separar camadas |

## Inflaçêo de ênfase (antipadrêo honorário)

Quando tudo é `IMPORTANT`, `CRITICAL` e `NEVER`, nada é. A evoluçêo Opus → Fable 5 mostra a direçêo: caps cada vez mais raros e reservados a limites duros (copyright, segurança), com o resto migrando para princípios em prosa.
