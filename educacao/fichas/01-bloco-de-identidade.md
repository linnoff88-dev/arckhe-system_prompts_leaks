# Ficha 1 — Bloco de Identidade

> "You are X" — persona, modelo e data de corte declarados na primeira linha.

## Problema
Sem ancoragem de identidade, o modelo deriva: muda de persona no meio da conversa, inventa capacidades que nêo tem, responde sobre eventos posteriores ao seu conhecimento como se soubesse.

## Soluçêo
Declarar no **topo** do prompt: quem é (produto + modelo), para quem trabalha, e os limites temporais do conhecimento. É a âncora que todo o resto do prompt referencia.

## Exemplos reais

**OpenAI — `OpenAI/gpt-5.5-instant.md` (~linha 1):**
> You are ChatGPT, a large language model trained by OpenAI, based on GPT 5.5.
> Knowledge cutoff: 2025-08
> Current date: 2026-06-01

Os três elementos canônicos em três linhas: persona, corte de conhecimento, data atual (note: a data atual é *contexto dinâmico* injetado — ver Ficha 10).

**Microsoft — `Microsoft/github-copilot.md` (~linha 3):**
> You are GitHub Copilot (@copilot) on github.com. Your job is to fulfill the user's software development task using all available tools and resources.

Persona + **escopo de responsabilidade** ("your job is...") na abertura — o modelo sabe o que é e o que veio fazer.

## Antipadrêo correspondente
Identidade ausente ou enterrada no meio do prompt. Sintoma clássico: o assistente "vira ChatGPT" no meio da conversa, ou afirma ter ferramentas que nêo existem.

## Quando NêO usar
Nunca omitir — mas evitar inflar com backstory irrelevante. Identidade é âncora, nêo biografia. Se o parágrafo de identidade passa de ~5 linhas, provavelmente há conteúdo de outro padrêo (capacidades, tom) vazando para dentro dele.

## Visto em
Todos os fornecedores do repositório, sem exceçêo. É o único padrêo 100% universal.

## Relacionadas
[[02-declaracao-de-capacidades]] · [[10-lembrete-de-sistema]] (a data atual pertence à camada dinâmica)
