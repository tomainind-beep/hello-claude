# Roadmap

## Fase 0 — Fundação (agora)
- [x] Repositório central, regras e níveis de acesso definidos
- [ ] Criar sessões dos agentes com tags `agente:<nome>` (ver `agentes/`)
- [x] Inventário do que existe (`docs/INVENTARIO.md`)
- [ ] Exportar para o Drive o que está só no Cowork (gerador de contratos, agente jurídico, buscador de empresas, financeiro)

## Fase 1 — Etapa 1: Comercial (prioridade máxima, 02/10)
Ver `docs/ETAPA-1-COMERCIAL.md`.
- [x] C2 Planilha de follow-up das propostas em aberto (03/10); falta o time preencher
- [ ] C2b Lista de retomada de 2025 (49 propostas): Leonardo/Taynara decidem GANHOU / PERDEU / RETOMAR antes de qualquer contato
- [ ] C3/C4: captura automática das conversas do WhatsApp (`docs/CAPTURA-WHATSAPP.md`): escolher provedor, confirmar coexistência e custos, ligar o número 1, receptor + Analista. Calibração com 3–5 conversas de teste.
- [x] C1a Tabelas do CRM criadas no Airtable (03/10)
- [ ] C1b Importar o histórico 2021–2025 e agrupar propostas em Negócios
- [x] Provedor pré-escolhido: YCloud (03/10). Falta confirmar plano (Free × Growth), cobrança e LGPD com o YCloud
- [ ] (Proposta) Obter um **número comercial novo** (WhatsApp Business), apontar os anúncios do Meta para ele; criar conta Free no YCloud, Business Manager verificado, ligar **esse número** por QR code e testar por semanas. Números atuais ficam fora
- [ ] Combinar com Prymaxx e Fenox como avisam que repassaram o follow-up de um cliente
- [ ] C3 Leads · C4 Marketing/criativos · C5 Prospecção · C6 Fechamento → produção

## Fase 1b — Demais agentes, sob pedido
- [ ] Propostas (Fase A): só observar o gerador; fluxo atual intocado (`docs/GERADOR-EM-PARALELO.md`)
- [ ] Orquestrador: painel diário (sessões, pendências de aprovação, falhas)
- [x] Jurídico/Contratos: material lido e gerador testado com dados fictícios (01/10); falta teste comparativo com contrato real
- [ ] Comercial, Marketing, Assistência: um caso de uso real por agente, sempre com rascunho + aprovação
- [ ] Melhoria de Sistema e Qualidade: escrever a bateria de testes inicial (`testes/`)

## Fase 1.5 — Gerador em ensaio isolado e integração (Fase B e C do gerador)
- [ ] Réplica de teste do gerador; comparar saída com a produção
- [ ] Autorização do Leonardo para o agente criar pedidos

## Fase 3 — Terminais para funcionários (só depois da validação)
Pré-requisito: o Leonardo declara o sistema validado. Até lá, ele é o único a lançar dados.
- [ ] Formulários Airtable por papel, com no máximo 4 acessos (decisão de 13/08)
- [ ] Registrar a nova decisão em `docs/DECISOES.md`

## Fase 2 — Automatização seletiva
Critério para promover uma tarefa: 5 execuções seguidas aprovadas sem correção. Cada promoção é registrada aqui, com data e regra escrita.

## Perguntas abertas
- "Power" foi tratado como erro de transcrição: o gerador é o do Cloud Run + Airtable descrito na skill. Corrigir se for outro sistema.
- Mover este projeto para um repositório próprio (`tomain-agentes`)?
- Onde estão os dados de assistência técnica, jurídico e marketing (Drive, Airtable, e-mail)?
