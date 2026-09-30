# Gerador de propostas: em paralelo, sem risco

O gerador atual atende o Leonardo e **não pode ser estragado**. Regra desta central:

## Fase A — Só observar (agora)
- O fluxo de hoje (formulário/pedido → gerador → e-mail interno) continua exatamente como está.
- O agente Propostas é **somente leitura** sobre Pedidos, Propostas e Drive: acompanha, confere, resume, alerta. **Não cria pedido, não altera registro, não faz deploy.**
- Nenhum número de proposta é consumido pela central.

## Fase B — Ensaio isolado
- Réplica de teste do gerador (cópia da árvore, sem tocar produção, sem consumir número, sem e-mail real), como a skill já recomenda.
- O agente Propostas gera propostas de teste na réplica e o agente Qualidade compara com a saída de produção do mesmo pedido. Só passa se **idêntico**.

## Fase C — Integração
- Somente quando a réplica igualar a produção em uma bateria de casos e o Leonardo autorizar por escrito no `ROADMAP.md`.
- Primeiro passo: o agente Propostas passa a **criar o pedido** (com aprovação por pedido). O motor segue intocado.
- Rollback: desligar o agente; o fluxo atual continua funcionando sem ele.

## Regras fixas (da skill `gerador-propostas-tomain`)
Congelados: `compor.py`, `triagem.py`, `registro.py`; `render.py` só com autorização explícita.
