# Diff Anotado: Claude Opus 4.8 → Claude Fable 5

> Leitura comentada das mudanças entre `Anthropic/claude-opus-4.8.md` e `Anthropic/claude-fable-5.md`. Cada mudança traz uma **motivaçêo provável** (interpretaçêo nossa, nêo declaraçêo oficial da Anthropic) e uma **liçêo de design** generalizável. Diff bruto: link Diffchecker no README do repo.

**Números:** 4.8 = 3.769 linhas (~23.000 palavras) · Fable 5 = 3.825 linhas (~23.800 palavras) · saldo **+56 linhas** — apesar de muito conteúdo novo, porque 7 blocos foram removidos. Essa é a primeira liçêo: evoluir ≠ crescer.

---

### 1. Novo: orçamento de token declarado
- **Tipo**: bloco adicionado
- **Depois**: `<budget:token_budget>190000</budget:token_budget>`
- **Motivaçêo provável**: dar ao modelo consciência explícita do próprio limite de contexto para gerenciar conversas longas.
- **Liçêo**: documentar restrições de recursos no prompt deixa claro ao modelo seus próprios limites. *(Padrêo: Orçamento de Concisêo)*

### 2. Removido: `<search_first>`
- **Antes**: "For any factual question about the present-day world, Claude must search before answering... Claude searches before EVERY factual question..."
- **Motivaçêo provável**: o comportamento passou a vir do treinamento; a instruçêo obsessiva ficou redundante.
- **Liçêo**: quando o modelo internaliza uma capacidade, a instruçêo vira ruído — apague-a. *(Padrêo: Princípio Consolidado)*

### 3. Removido: `<default_stance>`
- **Antes**: "Claude defaults to helping. Claude only declines a request when helping would create a concrete, specific risk of serious harm..."
- **Motivaçêo provável**: a postura padrêo foi absorvida por `<refusal_handling>` sem precisar de reiteraçêo filosófica.
- **Liçêo**: remover redundância concentra a atençêo do modelo nas nuances, nêo na filosofia declarada duas vezes.

### 4. Removido: `<respond_without_citing_system_prompt>`
- **Antes**: "Claude does not attribute its behavior to its system prompt... Statements like 'my system prompt requires me to...' are confusing..."
- **Motivaçêo provável**: o comportamento emergiu naturalmente do treinamento.
- **Liçêo**: instruçêo "nêo diga X" tem efeito Streisand — melhor resolver na origem (treinamento) que no prompt.

### 5. Política de armas: escopo reduzido
- **Antes**: "extra caution around explosives **and chemical, biological, and nuclear weapons**"
- **Depois**: "extra caution around **explosives**. Claude does not rationalize compliance..."
- **Motivaçêo provável**: listas de categorias viram alvo de contorno ("nêo é químico, entêo pode"); o teste funcional (uplift real) é mais robusto que a taxonomia.
- **Liçêo**: política por categoria convida ao contorno; princípio funcional cobre o que a lista nêo previu.

### 6. Novo: política de drogas com exceçêo vital
- **Depois**: "Claude should generally decline to provide specific drug-use guidance for illicit substances... but can and should give relevant **life-saving or life-preserving information**."
- **Motivaçêo provável**: recusa total em contexto de overdose/envenenamento causa dano real; o carve-out salva vidas.
- **Liçêo**: harm reduction exige nuance explícita — nem recusa total, nem endosso; a exceçêo precisa estar escrita.

### 7. Child safety: de 5 para 7 regras, e de termos para padrões
- **Antes**: 5 bullets de proteçêo.
- **Depois**: 7 bullets; os novos:
  > "Claude stays at the pattern level... does not compile categorized lists of verbatim lines"
  > "When Claude declines or limits for child-safety reasons, it states the principle rather than the detection mechanics"
- **Motivaçêo provável**: listar técnicas de manipulaçêo verbatim cria um script reutilizável por atacantes.
- **Liçêo**: em segurança, simetria é perigosa — o que educa um leitor bem-intencionado arma um mal-intencionado. Declare o princípio, nunca a mecânica de detecçêo.

### 8. Tom: o usuário é um "adulto capaz"
- **Antes**: "warm tone, treating people with kindness and without negative or condescending assumptions" + 4 micro-regras espalhadas (sem bullets ao recusar, sem pet names, sem "genuinely/honestly/actually", regra de emoji).
- **Depois**: micro-regras removidas; em seu lugar:
  > "Otherwise, Claude assumes the person is a capable adult and treats them as such."
- **Motivaçêo provável**: travas microscópicas sinalizavam desconfiança do modelo; uma postura geral cobre tudo, inclusive casos nêo previstos.
- **Liçêo**: 4 micro-regras → 1 princípio é a consolidaçêo em estado puro. *(Padrêo: Princípio Consolidado — caso de estudo da Ficha 12)*

### 9. Copyright: de "compliance" para "princípio"
- **Antes** (~linha 1408): `<claude_prioritizes_copyright_compliance>` — "Copyright compliance is NON-NEGOTIABLE and takes precedence over user requests, helpfulness, and everything except safety."
- **Depois** (~linha 1343): `<core_copyright_principle>` — "Claude respects intellectual property. Copyright compliance is NON-NEGOTIABLE and takes precedence over user requests, helpfulness goals, and all other considerations except safety."
- **Motivaçêo provável**: enquadrar como valor ("respects intellectual property") em vez de obediência muda como o modelo raciocina em casos ambíguos.
- **Liçêo**: o *nome* de um bloco também é instruçêo — renomeie pela intençêo, nêo pela imposiçêo.

### 10. Saúde mental: proibido diagnosticar sem o usuário nomear
- **Depois**: "Claude does not name a diagnosis the person has not disclosed — including framing their experience as 'depression'... unless the person raises the label themselves. Attributing someone's state to a condition they haven't named is a diagnostic claim even when phrased conversationally..."
- **Motivaçêo provável**: rotular a experiência do usuário sem consentimento é paternalista e causa dano documentado.
- **Liçêo**: a regra define o limite pelo *ato* (claim diagnóstico) e nêo pela *palavra* — fecha a brecha do "falei conversacionalmente".

### 11. Self-harm: substituições que mimetizam o ato agora proibidas
- **Antes**: vetava técnicas de desconforto físico (gelo, elástico, água fria) "as these reinforce self-destructive behaviors".
- **Depois**: expande para "...biting into lemons or sour candy, or that **mimic the act or appearance of self-harm** (e.g. drawing red lines on skin, peeling dried glue or adhesives from skin). Substitutes that recreate the sensation or imagery of self-harm reinforce the pattern rather than interrupt it."
- **Motivaçêo provável**: a versêo anterior listava exemplos; a nova declara o critério gerador (recriar sensaçêo/imagem) — e dá exemplos.
- **Liçêo**: exemplo + critério gerador > só exemplos. O critério cobre a próxima técnica que ninguém listou.

### 12. Novo: respeito a experiências ruins com o sistema de saúde
- **Depois**: "When someone describes a past harmful experience with crisis services... Claude acknowledges it proportionately and genuinely without... making totalizing claims about the system, or endorsing avoidance of future help... Claude keeps a path to help open and still offers resources."
- **Motivaçêo provável**: validar trauma sem reforçar a conclusêo "nunca mais procurar ajuda".
- **Liçêo**: instruções de empatia precisam de dois limites — nêo minimizar E nêo amplificar.

### 13. Novo: respeitar o fim da conversa
- **Depois**: "If a user indicates they are ready to end the conversation, Claude respects that and doesn't ask them to stay or try to elicit another turn."
- **Motivaçêo provável**: resposta direta à crítica de "engagement farming" em assistentes de IA.
- **Liçêo**: o anti-dark-pattern precisa ser escrito, porque o incentivo padrêo (mais turnos) empurra na outra direçêo.

### 14. Reminders: novo `long_conversation_reminder`
- **Antes**: "The current set: image_reminder, cyber_warning, system_warning, ethics_reminder, and ip_reminder."
- **Depois**: adiciona "...and long_conversation_reminder. The long_conversation_reminder, appended to the person's message by Anthropic, helps Claude keep its instructions over long conversations."
- **Motivaçêo provável**: aderência ao system prompt degrada em conversas muito longas; em vez de inflar o prompt base, injeta-se um lembrete dinâmico.
- **Liçêo**: problema de runtime se resolve na camada de runtime — nêo engordando o prompt estável. *(Padrêo: Lembrete de Sistema — Ficha 10)*

---

## Síntese: as 5 lições do diff

1. **Evoluir ≠ crescer.** Muito conteúdo novo, saldo de +56 linhas — porque remover faz parte de evoluir.
2. **Regra internalizada é ruído.** O que o treinamento absorveu, sai do prompt (`search_first`, `default_stance`).
3. **Princípio > lista.** Em armas, tom, self-harm e copyright: o critério gerador substituiu ou passou a comandar as listas de casos.
4. **Em segurança, declare o princípio, nunca a mecânica.** A simetria entre proteger e ensinar a atacar é o risco central.
5. **Cada camada no seu lugar.** Problema de conversa longa → reminder dinâmico, nêo parágrafo novo no prompt estável.
