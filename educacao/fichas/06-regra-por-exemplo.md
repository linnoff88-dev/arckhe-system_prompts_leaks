# Ficha 6 — Regra por Exemplo

> Regra definida via exemplo embutido: schema, formato de chamada, resposta-modelo.

## Problema
Regras de formato descritas em prosa são ambíguas. "Use a sintaxe correta de database" admite N interpretações; o modelo escolhe uma errada.

## Solução
Mostrar, não (só) descrever. Um exemplo concreto do formato esperado — schema inline, chamada-modelo, par bom/ruim — elimina a ambiguidade de uma vez.

## Exemplos reais

**Notion — `Notion/notion-ai.md` (~linhas 121–125):**
> Example: `<database url="URL" inline>Title</database>`
> Example: `<database url="URL" locked>Title</database>`

Duas linhas de exemplo substituem um parágrafo de especificação de atributos.

**Google — `Google/gemini-2.5-pro-api.md` (~linhas 38–44):**
> ```tool_code
> concise_search(query="your search query")
> ```
> ```tool_code
> print(browse(urls=["url1", "url2"]))
> ```
> When you are asked to browse multiple urls, you can browse multiple urls in a single call.

O exemplo carrega a regra: o segundo trecho *mostra* o batching de URLs antes de a prosa mencioná-lo.

## Variante avançada
Pares de contraste (`<example_good>` / `<example_bad>`) e exemplos com contexto (`<memory_application_examples>` nos prompts da Anthropic) — o exemplo demonstra também o *julgamento*, não só o formato.

## Antipadrão correspondente
Regra abstrata ambígua ("formate citações adequadamente"). No extremo oposto: **overfit ao exemplo** — o modelo copia o exemplo literalmente (busca por "your search query") em vez de generalizar. Exemplos devem ser obviamente placeholder ou variados.

## Quando NÃO usar
Para princípios de comportamento e julgamento, exemplos demais engessam — o modelo trata a lista como exaustiva. Exemplo é para *formato e mecânica*; princípio é para *julgamento* (Ficha 3).

## Visto em
Notion, Google, Microsoft (schemas YAML/JSON inline), Anthropic (blocos `<example>` em memória e preferências).

## Relacionadas
[[08-contrato-de-ferramenta]] · [[03-regra-com-porque]]
