# Ficha 10 — Lembrete de Sistema

> Camada dinâmica injetada pelo harness em tempo de execução, separada do comportamento estável.

## Problema
Nem tudo que o modelo precisa saber é estável: data atual, avisos contextuais, estado de ferramentas, degradação de aderência em conversas longas. Colocar isso no prompt estável obriga a reeditar (e re-testar) o prompt inteiro a cada ajuste.

## Solução
Arquitetura em duas camadas: o system prompt define o comportamento **estável**; o harness injeta `<system-reminder>` dinâmicos nas mensagens quando necessário. O prompt estável ensina o modelo a *interpretar* essa camada.

## Exemplos reais

**xAI — `xAI/grok-build.md` (~linha 36):**
> Tool results and user messages may include \<system-reminder\> tags. \<system-reminder\> tags contain useful information and reminders. They are automatically added by the system, and bear no direct relation to the specific tool results or user messages in which they appear.

O contrato da camada: o modelo aprende que esses avisos vêm da plataforma, não do usuário nem da ferramenta.

**Anthropic — `Anthropic/claude-fable-5.md` (bloco `<anthropic_reminders>`):**
O Fable 5 lista um *conjunto nomeado* de reminders (image_reminder, cyber_warning, system_warning, ethics_reminder, ip_reminder, long_conversation_reminder) — o último, novo no Fable 5, refresca as instruções em conversas longas:
> The long_conversation_reminder, appended to the person's message by Anthropic, helps Claude keep its instructions over long conversations.

## Por que é o padrão arquiteturalmente mais importante
É a separação config estável × estado dinâmico da engenharia de software aplicada a prompts. Permite: ajustar comportamento sem redeploy do prompt, A/B de avisos, e resposta a problemas emergentes (ex.: degradação em conversa longa) sem inchar o prompt base.

## Antipadrão correspondente
**Tudo-no-prompt**: data, avisos e estado misturados ao comportamento estável. Sintoma: o prompt precisa de edição a cada mudança de contexto, e o diff entre versões vira ruído.

## Quando NÃO usar
Exige controle do harness — quem só escreve o prompt (sem controlar a plataforma) não tem como injetar a camada. Nesse caso, manter ao menos a *disciplina mental*: separar no texto o que é estável do que é contextual.

## Visto em
Anthropic (caso canônico e mais evoluído), xAI (adotou o mesmo formato — note a convergência entre fornecedores).

## Relacionadas
[[05-compartimento-xml]] · [[11-hierarquia-de-prioridade]]
