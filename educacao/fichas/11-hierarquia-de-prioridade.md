# Ficha 11 — Hierarquia de Prioridade

> Quem manda quando instruções conflitam — precedência declarada explicitamente.

## Problema
Instruções conflitam o tempo todo: política central vs pedido do usuário, arquivo de projeto vs chat, skill vs default. Sem hierarquia declarada, o comportamento em conflito é indeterminado — e indeterminado significa explorável (prompt injection) ou frustrante (modelo ignora o usuário).

## Soluçêo
Declarar a cadeia de precedência no próprio prompt, idealmente junto das regras de maior prioridade.

## Exemplos reais

**xAI — `xAI/grok-4.1-beta.md` (~linha 2):**
> These core policies within the \<policy\> tags take highest precedence. System messages take precedence over user messages.

Três níveis em duas frases: core policy > system > user. O compartimento XML (Ficha 5) delimita exatamente o que está no topo.

**xAI — `xAI/grok-build.md` (~linhas 195–196):**
> More-deeply-nested project instruction files take precedence over higher-level ones when instructions conflict. Direct user instructions in the chat always take precedence over any project instruction file content.

Hierarquia para agentes de código: arquivo mais específico > arquivo geral, e usuário no chat > qualquer arquivo. Mesmo modelo do Claude Code (instruções do usuário > skills/plugins > defaults).

## A regra de ouro embutida
Note o padrêo consistente entre fornecedores: **políticas de segurança no topo, usuário acima de tudo o resto**. O usuário nêo pode anular segurança, mas vence qualquer preferência de produto, arquivo de config ou skill.

## Antipadrêo correspondente
Conflito indeterminado: duas regras contraditórias sem desempate ("seja conciso" + skill que pede relatório longo). Sintoma: comportamento oscila entre execuções; usuários reclamam que "ora obedece, ora nêo".

## Quando NêO usar
Sempre que houver mais de uma fonte de instruções, é necessário. Em prompt único e fechado (sem skills, arquivos ou múltiplas camadas), a hierarquia se reduz a "segurança > usuário > defaults" — uma linha resolve.

## Visto em
xAI (declaraçêo mais explícita do repo), Anthropic/Claude Code (user > skill > default), Microsoft, Cursor.

## Relacionadas
[[05-compartimento-xml]] · [[10-lembrete-de-sistema]] · [[04-contraste-always-never]]
