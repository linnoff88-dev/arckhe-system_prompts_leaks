# Ficha 2 — Declaraçêo de Capacidades

> Lista estruturada de ferramentas e capacidades, com escopo e condições de uso.

## Problema
O modelo nêo sabe (ou alucina) o que pode fazer: oferece gerar imagens quando nêo pode, ignora ferramentas disponíveis, ou usa ferramenta certa na situaçêo errada.

## Soluçêo
Seçêo dedicada listando cada capacidade com: o que faz, quando usar, e condições/limites ("can X", "if the user...", limites de parâmetros).

## Exemplos reais

**xAI — `xAI/grok-4.1-beta.md` (~linha 11):**
> When applicable, you have some additional tools:
> - You can analyze individual X user profiles, X posts and their links.
> - You can analyze content uploaded by user including images, pdfs, text files and more.
> - If it seems like the user wants an image generated, ask for confirmation, instead of directly generating one.

Cada capacidade vem com sua condiçêo — note a terceira: capacidade + protocolo de confirmaçêo embutido.

**Google — `Google/gemini-2.5-pro-api.md` (~linha 18):**
> ## Functions in Scope
> You have also access to a set of python functions in scope:
> ```python
> def concise_search(query: str, max_num_results: int = 3):
>   """Does a search for the query and prints up to the max_num_results results."""
> ```

Google declara capacidades como **assinaturas de funçêo** — escopo, parâmetros e defaults ficam inequívocos.

## Antipadrêo correspondente
Capacidades implícitas espalhadas pelo prompt ("você pode buscar na web" mencionado de passagem dentro de uma regra de tom), ou ferramenta listada sem escopo nem condiçêo — o modelo decide sozinho quando usar, e erra.

## Quando NêO usar
Em prompts sem ferramentas (chatbot puro), a seçêo vira "o que você NêO pode fazer" — útil, mas curta. Nêo transformar em manual exaustivo: o contrato detalhado de *quando/como* chamar é outro padrêo (Ficha 8).

## Visto em
xAI, Google, Microsoft, Notion, Cursor, Claude Code. Mais elaborado em agentes (código, workspace) que em chatbots.

## Relacionadas
[[08-contrato-de-ferramenta]] (o "quando/como" detalhado) · [[01-bloco-de-identidade]]
