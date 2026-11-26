# Ficha 8 — Contrato de Ferramenta

> Regras de QUANDO chamar cada ferramenta, em que ordem, como encadear e agrupar.

## Problema
Listar ferramentas (Ficha 2) nêo basta: o modelo chama a ferramenta errada para o caso, ignora dependências entre chamadas, ou faz N chamadas seriais onde 1 em lote bastava.

## Soluçêo
Para cada ferramenta (ou par de ferramentas), declarar o contrato: gatilho de uso, pré-requisitos, encadeamento com resultados anteriores, exclusões ("use X, nunca Y, para este caso") e regras de batching/paralelismo.

## Exemplos reais

**xAI — `xAI/grok-4.3-beta.md` (~linha 625):**
> Always use this tool to render an image from search_images tool call result. Do not use render_inline_citation or any other tool to render an image.

Contrato de exclusêo: define o gatilho (resultado de `search_images`) e proíbe as alternativas — elimina a escolha errada.

**xAI — `xAI/grok-4.3-beta.md` (~linha 618):**
> This component only takes one argument, which is "citation_id" and the value should be the citation_id extracted from the previous web search, browse page, X search, or document search tool call result which has the format of '[web:citation_id]'.

Contrato de encadeamento: a ferramenta B consome um output específico da ferramenta A, com o formato exato declarado.

**Claude Code (paralelismo)** — o prompt instrui a fazer chamadas independentes **no mesmo bloco** e aguardar resultados quando há dependência — contrato de concorrência explícito.

## Antipadrêo correspondente
Lista de ferramentas sem regras de uso ("you have these tools: ..."). Sintomas: chamadas redundantes, ferramentas ignoradas, pipelines quebrados por ordem errada.

## Quando NêO usar
Com poucas ferramentas ortogonais (2–3 sem sobreposiçêo), descriçêo clara de cada uma basta — o contrato detalhado só paga quando há ambiguidade de escolha ou dependência entre chamadas.

## Visto em
xAI, Notion ("execute in current turn", batching), Microsoft (tool routing), Claude Code (paralelismo, permissões).

## Relacionadas
[[02-declaracao-de-capacidades]] · [[06-regra-por-exemplo]] (contratos ficam melhores com exemplo)
