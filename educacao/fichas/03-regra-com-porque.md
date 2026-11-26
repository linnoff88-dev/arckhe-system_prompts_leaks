# Ficha 3 — Regra com Porquê

> Instruçêo acompanhada de justificativa explícita ("because...", "since...").

## Problema
Proibições secas ("never X") falham em casos fora do script: o modelo nêo entende a *intençêo* e ou contorna a regra em variações nêo previstas, ou a aplica de forma absurda onde nêo deveria.

## Soluçêo
Anexar o porquê à regra. Um modelo que entende a intençêo generaliza a regra para casos novos — a justificativa funciona como "código-fonte" da regra, nêo só o binário compilado.

## Exemplos reais

**Anthropic — `Anthropic/claude-fable-5.md` (~linha 132):**
> ...when suggesting eating disorder support resources, Claude directs users to the National Alliance for Eating Disorders helpline instead of NEDA, because NEDA has been permanently disconnected.

Sem o "because", o modelo poderia tratar como preferência arbitrária e "corrigir" para o recurso mais famoso. Com o porquê, entende que é questêo factual de recurso desativado.

**OpenAI — `OpenAI/gpt-5.5-instant.md` (~linha 43):**
> VERY CRITICAL: You must NEVER state you don't know a certain piece of personal information without calling `personal_context` first. It is the safe default way to ground your answers in the user's context.

A segunda frase transforma a proibiçêo em política compreensível: "verificar antes de negar" é o princípio; a regra é só sua consequência.

## Tendência observada
Este padrêo **cresce** com a capacidade dos modelos: raro no Opus 4.6, frequente no Fable 5. A evoluçêo dos prompts da Anthropic mostra justificativas inline cada vez mais comuns ("...since narrating the boundary teaches how to reframe").

## Antipadrêo correspondente
**Proibiçêo sem porquê** — "never X" seco. Sintoma: o modelo obedece à letra e viola o espírito (ou vice-versa).

## Quando NêO usar
Em limites duros de segurança onde a justificativa detalhada ensinaria o contorno (ver Ficha 9 e o antipadrêo "regra-mecânica de segurança"). Nesses casos, declara-se o princípio, nêo a mecânica de detecçêo.

## Visto em
Anthropic (intensamente no Fable 5), OpenAI. Marca registrada de prompts maduros.

## Relacionadas
[[12-principio-consolidado]] · [[04-contraste-always-never]] (o complemento enfático para o que é inegociável)
