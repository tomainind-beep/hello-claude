# Roadmap

## Fase 0 — Fundação (agora)
- [x] Repositório central, regras e níveis de acesso definidos
- [ ] Criar sessões dos agentes com tags `agente:<nome>` (ver `agentes/`)
- [ ] Mapear onde ficam hoje os dados de cada área (comercial, jurídico, marketing, assistência)

## Fase 1 — Tudo sob pedido
- [ ] Propostas: pedir ao agente que cadastre o pedido e acompanhe até a proposta chegar no e-mail interno
- [ ] Orquestrador: painel diário (sessões, pendências de aprovação, falhas)
- [ ] Comercial, Jurídico, Marketing, Assistência: um caso de uso real por agente, sempre com rascunho + aprovação

## Fase 2 — Automatização seletiva
Critério para promover uma tarefa: 5 execuções seguidas aprovadas sem correção. Cada promoção é registrada aqui, com data e regra escrita.

## Perguntas abertas
- Hoje o gerador de propostas roda a partir do Power (fluxo do Leonardo) ou do Cloud Run `tomain-gerador`? A documentação descreve o Cloud Run com Airtable; confirmar se o Power é a porta de entrada dele.
- Onde estão os dados de assistência técnica, jurídico e marketing (Drive, Airtable, e-mail)?
