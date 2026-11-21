# Ficha 9 — Preservação de Fonte

> Citações e textos externos intocados, com mecanismo formal de citação.

## Problema
Dois riscos opostos com material de terceiros: (a) o modelo *altera* o que cita — parafraseia citações, corrompe rastreabilidade; (b) o modelo *copia demais* — reproduz texto protegido por direitos autorais.

## Solução
Dupla regra: citações passam por um mecanismo formal que preserva a origem exatamente; reprodução de conteúdo protegido tem limites duros — e a paráfrase detalhada conta como reprodução.

## Exemplos reais

**xAI — `xAI/grok-4.3-beta.md` (~linha 617):**
> Do not cite sources any other way; always use this component to render citation. You should only render citation from web search, browse page, X search, or document search results, not other sources.

Citação só via componente estruturado, e só de fontes verificáveis da própria sessão — rastreabilidade garantida por arquitetura, não por boa vontade.

**Anthropic — `Anthropic/claude-fable-5.md` (~linha 1360):**
> When users request that you reproduce [...] passages from articles or books: Decline and explain you cannot reproduce substantial portions. Do not attempt to reconstruct the passage through detailed paraphrasing with specific facts/statistics from the original—this still violates copyright even without verbatim quotes.

O lado copyright: fecha inclusive a brecha da "paráfrase detalhada" — preservar a fonte também significa não reconstruí-la.

## Antipadrão correspondente
Citação livre em prosa ("according to the article...") sem mecanismo — impossível auditar; e a **regra-mecânica** invertida: permitir qualquer paráfrase como se contornasse o direito autoral.

## Quando NÃO usar
Conversas sem material externo não precisam do aparato. O mecanismo formal de citação só se justifica em produtos de busca/síntese (Perplexity, Grok, Copilot) — num chatbot puro, vira cerimônia.

## Visto em
Perplexity (regra "preserve response_text com zero modificações"), xAI, Microsoft, Anthropic (limites de copyright em todo prompt).

## Relacionadas
[[08-contrato-de-ferramenta]] · [[12-principio-consolidado]] (a evolução do bloco de copyright é o caso de estudo)
