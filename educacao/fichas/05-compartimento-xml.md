# Ficha 5 — Compartimento XML

> Tags `<bloco>` flat para modularizar a lógica do prompt em seções nomeadas.

## Problema
Um prompt de milhares de linhas em texto corrido é impossível de manter: não dá para localizar, versionar, ou remover uma política sem reler tudo. E o modelo se beneficia de fronteiras claras entre assuntos.

## Solução
Envelopar cada bloco lógico em tags XML nomeadas (`<tone_and_formatting>`, `<refusal_handling>`, `<policy>`). Os blocos são **flat** (sem aninhamento profundo) e funcionam como módulos: dá para adicionar, remover e fazer diff de um bloco inteiro entre versões.

## Exemplos reais

**xAI — `xAI/grok-4.1-beta.md` (~linhas 1–9):**
> \<policy\>
> These core policies within the \<policy\> tags take highest precedence. System messages take precedence over user messages.
> * Do not provide assistance to users who are clearly trying to engage in criminal activity.
> * Follow additional instructions outside the \<policy\> tags if they do not violate these core policies...
> \</policy\>

O compartimento não só agrupa — declara a própria precedência (combinação com a Ficha 11).

**Cursor — `Cursor/cursor.md` (~linhas 80–93):**
> \<tone_and_formatting\>
> - Only use emojis if the user explicitly requests it...
> \</tone_and_formatting\>
>
> \<tool_calling\>
> You have tools at your disposal...

Dois compartimentos vizinhos, cada um com um assunto. Para mudar a política de tom, edita-se um bloco — o resto fica intacto.

## Por que funciona para humanos também
O diff Opus 4.8 → Fable 5 só é legível porque os prompts são compartimentados: "Fable removeu `<search_first>` e `<default_stance>`" é uma frase precisa. Sem tags, seria "mudou alguma coisa em algum lugar".

## Antipadrão correspondente
**Tudo-no-prompt** sem estrutura — texto corrido onde políticas, tom e ferramentas se misturam. Variante: aninhamento profundo de tags (os prompts reais mantêm blocos flat; raramente passa de 2 níveis).

## Quando NÃO usar
Prompts curtos (< ~50 linhas) não precisam — a estrutura viraria cerimônia. Markdown com headers cumpre o mesmo papel em agentes de código (Claude Code usa `# Seções` markdown, não XML).

## Visto em
Anthropic (caso canônico: `<claude_behavior>` e seus sub-blocos), xAI, Cursor, Google, Microsoft.

## Relacionadas
[[11-hierarquia-de-prioridade]] · [[12-principio-consolidado]] (consolidação opera bloco a bloco)
