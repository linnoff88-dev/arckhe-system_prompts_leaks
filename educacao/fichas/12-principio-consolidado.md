# Ficha 12 — Princípio Consolidado

> Fundir regras redundantes num princípio único — o antídoto do prompt-cebola.

## Problema
Prompts crescem por acreçêo: cada bug vira uma regra nova e nada é removido. Resultado: regras redundantes que dessincronizam entre si, micro-regras que sinalizam desconfiança do modelo, e um prompt onde ninguém sabe mais o que pode ser apagado.

## Soluçêo
Periodicamente, substituir conjuntos de regras específicas por um princípio único que as gera. O princípio cobre os casos das regras antigas **e** os casos que ninguém previu.

## Exemplos reais (a evoluçêo Opus → Fable 5 é o caso de estudo)

**Consolidaçêo de micro-regras de tom — `Anthropic/claude-opus-4.8.md` tinha 4 regras separadas:**
> "Claude never uses bullet points when declining" · "Claude should not use pet names" · "Claude avoids using 'genuinely', 'honestly', 'actually'" · regra de emoji

**`Anthropic/claude-fable-5.md` removeu as 4** e cobre tudo com o princípio:
> Otherwise, Claude assumes the person is a capable adult and treats them as such.

Quatro travas microscópicas viraram uma postura — que também resolve casos que as travas nêo previam.

**Reenquadramento do copyright — mesmo texto, moldura nova:**
- Opus 4.8 (~linha 1408): `<claude_prioritizes_copyright_compliance>` — "Copyright compliance is NON-NEGOTIABLE and takes precedence over user requests, helpfulness, and everything except safety."
- Fable 5 (~linha 1343): `<core_copyright_principle>` — "Claude respects intellectual property. Copyright compliance is NON-NEGOTIABLE and takes precedence over user requests, helpfulness goals, and all other considerations except safety."

O conteúdo quase nêo mudou — o **nome do bloco** sim: de "prioriza compliance" (obediência) para "princípio central" (valor). Consolidar também é renomear pela intençêo.

**Remoções secas no Fable 5:** `<search_first>`, `<default_stance>`, `<respond_without_citing_system_prompt>` — blocos inteiros apagados porque o comportamento passou a emergir do treinamento. Regra que o modelo já internalizou é ruído.

## Antipadrêo correspondente
**Prompt-cebola** — só adicionar, nunca remover. Teste de cheiro: se duas regras dizem quase a mesma coisa em lugares diferentes, a próxima ediçêo vai dessincronizá-las.

## Quando NêO usar
Limites duros de segurança e formato mantêm regras explícitas mesmo com princípio declarado (o Fable 5 mantém os limites numéricos de citaçêo ao lado do princípio de copyright). Consolidar ≠ confiar cegamente: o princípio substitui regras *redundantes*, nêo as *inegociáveis*.

## A prática que este padrêo sugere
A cada N adições ao seu prompt, uma rodada de consolidaçêo: o que pode virar princípio? O que o modelo já faz sem ser mandado? Toda regra mantida precisa de um porquê e de um teste que falharia sem ela.

## Visto em
Anthropic (Fable 5 é a masterclass: 7 blocos removidos, micro-regras fundidas, saldo de apenas +56 linhas com muito conteúdo novo).

## Relacionadas
[[03-regra-com-porque]] · [[05-compartimento-xml]] · [[07-orcamento-de-concisao]]
