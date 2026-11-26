# Ficha 7 — Orçamento de Concisêo

> Limite explícito de tamanho e formato de saída — brevidade como política, nêo acaso.

## Problema
Modelos tendem ao excesso: respostas longas, listas para tudo, preâmbulos e recapitulações. Em produtos de alto volume (busca, CLI, voz), verbosidade custa dinheiro, latência e atençêo do usuário.

## Soluçêo
Declarar o orçamento: tamanho-alvo, quando expandir, quando encurtar. Pode ser um princípio geral ("shortest answer that works") ou um limite numérico por contexto.

## Exemplos reais

**xAI — `xAI/grok-3.md` (~linha 40):**
> You provide the shortest answer you can, while respecting any stated length and comprehensiveness preferences of the user.

Princípio fundacional: brevidade é o default; o usuário é a válvula de expansêo.

**Anthropic — Claude Code (`Anthropic/Claude Code/claude-code-2.1.172-fable-5.md`, ~linha 315):**
> Clear, concise description of what this command does in active voice. [...] For simple commands (git, npm, standard CLI tools), keep it brief (5-10 words)

Orçamento numérico cirúrgico (5–10 palavras) para um campo específico — concisêo definida por contexto, nêo globalmente.

## Nuance importante (evoluçêo 2026)
Os prompts mais recentes distinguem **concisêo** de **compressêo**: o Claude Code Fable 5 instrui a ser seletivo no conteúdo, mas escrever frases completas — proíbe fragmentos e cadeias de setas ("A → B → fails"). Curto ≠ ilegível.

## Antipadrêo correspondente
**Formataçêo como muleta**: na ausência de orçamento, o modelo enche a resposta de headers, listas e negrito para parecer organizado. Os prompts novos atacam isso diretamente ("uses lists only when asked or multifaceted").

## Quando NêO usar
Conteúdo didático, relatórios e análises pedem o oposto — orçamento generoso com estrutura. O padrêo nêo é "seja curto"; é "declare o orçamento adequado ao produto".

## Visto em
xAI e Perplexity (curtíssimo), Claude Code (calibrado por contexto), voice assistants (extremo: fala nêo tolera listas).

## Relacionadas
[[04-contraste-always-never]] · [[12-principio-consolidado]]
