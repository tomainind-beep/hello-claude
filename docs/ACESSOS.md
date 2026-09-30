# Níveis de acesso

| Nível | Pode | Não pode |
|---|---|---|
| **N0 – Leitura** | consultar dados e documentos | escrever qualquer coisa |
| **N1 – Rascunho** | criar rascunhos (e-mail, minuta, peça, planilha) e arquivos novos em pasta de trabalho | enviar, alterar registros existentes |
| **N2 – Execução com aprovação** | executar ação externa depois de aprovação explícita do Leonardo | agir sem aprovação |
| **N3 – Autônomo** | agir sozinho dentro de regra escrita | (reservado; ninguém está aqui ainda) |

## Matriz inicial (tudo começa sob pedido)

| Agente | Airtable | Drive | Gmail | Agenda | Nível |
|---|---|---|---|---|---|
| Orquestrador | leitura | leitura | — | leitura | N0 + comandar agentes |
| Propostas | Clientes/Propostas/Pedidos: escrita de pedido | Motor/Fontes: leitura; Propostas: escrita | rascunho | — | N2 |
| Comercial | Clientes/Propostas: leitura | Orçamentos: leitura | rascunho | leitura | N1 |
| Jurídico | leitura de Clientes/Pedidos | Contratos: leitura/escrita em pasta própria | rascunho | leitura | N1 |
| Marketing | leitura de Clientes (sem dados sensíveis) | pasta própria | rascunho | — | N1 |
| Assistência Técnica | Pedidos: leitura | pasta própria | rascunho | leitura/agenda de visitas | N1 |
| Financeiro | leitura | `Financeiro Tomain Eng`: leitura (só este agente) | — | leitura | N0 |

Revisão do nível: só o Leonardo promove um agente de nível, registrando no `docs/ROADMAP.md`.
