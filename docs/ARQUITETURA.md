# Arquitetura

```
                        Leonardo
                           │  (um comando)
                     ┌─────▼──────┐
                     │ Orquestrador│  vê todas as sessões, revisa, distribui
                     └─────┬──────┘
   ┌────────┬──────────┬───┴──────┬───────────┬───────────┬──────────┐
Propostas Comercial  Jurídico  Marketing  Assist. Técnica Financeiro
   │          │          │         │            │            │
   └──────────┴────── Dados compartilhados ─────┴────────────┘
        Airtable (registros) · Drive (documentos) · Gmail · Agenda
```

## Peças
- **Agentes**: sessões Claude Code Remote, uma por função, cada uma com o prompt de `agentes/<nome>/AGENTE.md`. Tag da sessão: `agente:<nome>`.
- **Orquestrador**: usa `list_sessions`/`get_session` para ver estado, `list_events` para ler o que foi feito, `SendMessage` para repassar comandos, `interrupt_session` para parar, `create_trigger` para revisões agendadas.
- **Fonte única de dados**: Airtable (base `appuP3V321joRG9jw` já tem Clientes, Propostas, Pedidos; novas tabelas entram na mesma base ou em uma base irmã) e Drive compartilhado. O repositório guarda só definições e documentação, nunca dados de cliente.
- **Gerador de propostas**: serviço existente no Cloud Run (`tomain-gerador`). Continua sendo o motor; o agente Propostas só o alimenta e acompanha (ver `agentes/propostas/AGENTE.md`).

## Fluxo de um comando
1. Leonardo escreve o pedido ao Orquestrador.
2. Orquestrador identifica o(s) agente(s) responsável(is) e repassa a tarefa, com o escopo recortado.
3. Cada agente executa até o limite do seu nível de acesso; ação externa pára em "aguardando aprovação".
4. Orquestrador consolida: o que foi feito, o que espera aprovação, o que falhou.

## Limites conhecidos
- O Orquestrador só enxerga sessões cloud da conta. O Cowork local no computador não aparece como sessão endereçável; integra-se via dados compartilhados (Drive/Airtable).
- Conectores e permissões vêm da conta; o nível de acesso por agente é aplicado por instrução (prompt) e pela lista de conectores da rotina/sessão, não por um controle de identidade separado.
