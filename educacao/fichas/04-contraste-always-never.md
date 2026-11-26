# Ficha 4 — Contraste ALWAYS/NEVER

> Ênfase em caps (NEVER, ALWAYS, MUST) reservada aos comportamentos críticos.

## Problema
Em prompts longos, regras críticas se diluem no meio de dezenas de orientações. O modelo trata tudo com o mesmo peso e viola exatamente a regra que nêo podia.

## Soluçêo
Marcar com caps **apenas** o que é inegociável, idealmente em pares de contraste: o que NUNCA fazer + o que fazer EM VEZ disso. O contraste positivo/negativo elimina a ambiguidade de "ok, nêo faço X... e faço o quê?".

## Exemplos reais

**Cursor — `Cursor/cursor.md` (~linhas 117–133):**
> RULE SUMMARY (ALWAYS Follow):
> - NEVER mix formats.
> - NEVER add language tags to CODE REFERENCES.
> - NEVER indent triple backticks.
> - ALWAYS include at least 1 line of code in any reference block.

Lista de contraste pura: três NEVER + um ALWAYS, sobre o assunto onde o produto nêo tolera erro (renderizaçêo de código no editor).

**Microsoft — `Microsoft/github-copilot.md` (~linhas 7–8):**
> You MUST NOT generate any text before or between tool calls. Do not explain what you're about to do, do not narrate your reasoning. Simply execute the tool calls silently. Only provide text output AFTER all tool calls are complete...

Proibiçêo (MUST NOT) imediatamente seguida do comportamento positivo esperado ("simply execute... only provide text AFTER") — o par completo.

## Antipadrêo correspondente
**Inflaçêo de ênfase**: quando tudo é CRITICAL, IMPORTANT e NEVER, nada é. O prompt grita o tempo todo e o modelo perde a escala de prioridade. A evoluçêo Opus → Fable 5 reduziu caps, reservando-os a copyright e segurança.

## Quando NêO usar
Para preferências de estilo e comportamentos com nuance — aí entra a Regra com Porquê (Ficha 3). Regra prática: se você consegue imaginar uma exceçêo legítima, nêo merece NEVER.

## Visto em
Cursor e Microsoft (uso intenso), OpenAI, Anthropic (uso cada vez mais raro e cirúrgico). Mais comum em agentes de código, onde erros de formato quebram o produto.

## Relacionadas
[[03-regra-com-porque]] (o complemento para tudo que tem nuance) · [[11-hierarquia-de-prioridade]]
