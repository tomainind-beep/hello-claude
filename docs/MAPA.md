# Mapa do projeto — onde estamos

**Atualizado em 01/10/2026 (2ª leitura do Drive).** Leia este arquivo primeiro ao retomar. Legenda: ✅ feito · 🟡 em andamento · ⬜ não começou · ⛔ bloqueado/decisão pendente

## Em uma frase
Estrutura e regras da central estão prontas e o inventário está feito; **nenhum agente está rodando ainda**. O Jurídico/Contratos foi analisado e o gerador de contratos roda aqui com dados fictícios. Próximo passo: você escolher um caso real para o teste comparativo e soltar o conteúdo do plugin jurídico.

## Importante (descoberto na 2ª leitura)
O plano "Integração Tomain" que você já tinha no Cowork **já define a lógica dos agentes**: cada mudança de status de um negócio dispara um agente, que escreve só na sua seção do prontuário. A central segue esse plano (`docs/FLUXO-DE-ESTADOS.md`), não um paralelo.

## Princípios fixos
1. Tudo sob pedido; ação externa só com aprovação do Leonardo.
2. Gerador de propostas não é tocado; a central só o observa em paralelo.
3. Só o Leonardo lança dados até o sistema estar validado.
4. Nada de segredos no repositório; dados de cliente ficam no Drive/Airtable, nunca no GitHub.

## Fundação
| Item | Estado | Onde |
|---|---|---|
| Regras para todos os agentes | ✅ | `CLAUDE.md` |
| Níveis de acesso e matriz por agente | ✅ | `docs/ACESSOS.md` |
| Arquitetura (orquestrador + agentes) | ✅ | `docs/ARQUITETURA.md` |
| Inventário do que já existe | ✅ | `docs/INVENTARIO.md` |
| Decisões registradas | ✅ | `docs/DECISOES.md` |
| Material do Cowork no Drive | 🟡 jurídico, contratos, prospecção e integração subidos; **falta** base da Receita (pesada, dispensada por ora) | Drive → `Tomain — Agentes` |
| Repositório próprio `tomain-agentes` | ⛔ aguardando sua decisão | — |
| Sessões dos agentes criadas (tags `agente:<nome>`) | ⬜ | — |
| Container próprio (Google Cloud separado) | ⬜ só na etapa 2 | `docs/CONTAINER.md` |

## Agentes
| Agente | Definido | Material existente | Rodando | O que falta |
|---|---|---|---|---|
| **Orquestrador** | ✅ | — | ⬜ | Criar a sessão; painel diário de status e pendências |
| **Propostas** | ✅ (só observa) | ✅ Cloud Run + Airtable, em produção | ⬜ | Sessão de leitura; depois réplica de teste e, só com sua autorização, criar pedidos |
| **Jurídico** | ✅ (atualizado 01/10) | ✅ plugin + pastas (Drive) | ⬜ | Soltar o conteúdo do plugin (zip não abre daqui); testar com um caso real |
| **Contratos** (parte do Jurídico) | ✅ | ✅ `gerar-contrato.js` (Drive) | 🟡 testado com dados fictícios | Comparar com um contrato real (ex.: proposta 957); PDF fora do Cowork ainda não funciona; depois ler o prontuário |
| **Prospecção** | ✅ (lista + rascunho) | 🟡 scripts 02–04 no Drive; base da Receita fora | ⬜ | Definir filtros e redes sociais; decidir base legal; conferir chaves nos scripts |
| **Comercial** | ✅ | ✅ Airtable, lista de retomada de 2025 | ⬜ | Primeiro caso: retomar propostas de 2025 sem desfecho |
| **Financeiro** | ✅ (só leitura) | ✅ painel, extratos, contas a pagar (dado sensível) | ⬜ | Só sob pedido; substituir/complementar a rotina do dia 25 |
| **Marketing** | ✅ | 🟡 manual da marca v1–v3, lâminas | ⬜ | Escolher o primeiro caso de uso |
| **Assistência Técnica** | ✅ | ⬜ nada localizado | ⬜ | ⛔ onde ficam os dados hoje? Piloto já previsto: Relatório de Instalação (Trouw, proposta 814) |
| **Melhoria de Sistema** | ✅ | — | ⬜ | Só faz sentido depois de 2 ou 3 agentes rodando |
| **Qualidade** | ✅ | — | ⬜ | Escrever a bateria inicial em `testes/` (5 casos já listados) |

## Pendências que dependem só de você
1. Criar o repositório `tomain-agentes` ou manter neste?
2. Conferir se os scripts de prospecção têm chave de API ou token real dentro; se tiver, trocar as chaves.
3. Onde estão os dados de assistência técnica, jurídico e marketing (além do que já subiu)?
4. Definir filtros da Prospecção (CNAE, porte, estado) e se quer redes sociais.
5. Escolher o caso real do teste comparativo de contrato (sugestão: proposta 957) e dizer se posso gerar uma cópia para você comparar com a original.
6. Descompactar o `assistente-juridico.plugin` (é um zip) e colocar os arquivos soltos em `juridico-e-contratos/99 - Plugin e Config/conteudo`.

## Agentes em espera (não definidos ainda)
Projeto, Produção, Compras, Fiscal/Contábil, **Documentação Técnica** (já iniciada no Cowork), Estoque, Expedição, RH, Indicadores. Ver `agentes/BACKLOG.md`.

## Trilha (ordem recomendada)
1. ✅ Fundação e inventário
2. ▶ **Jurídico + Contratos** em paralelo ao Cowork (análise feita; falta teste comparativo)
3. Orquestrador com painel de status
4. Propostas em modo observação; réplica de teste do gerador
5. Qualidade com bateria de testes
6. Comercial (retomada de 2025) e Prospecção (lista + rascunho)
7. Financeiro, Marketing, Assistência (Relatório de Instalação)
8. Melhoria de Sistema
9. Validação geral → terminais para funcionários (no máximo 4 acessos)
10. Automação seletiva (5 execuções aprovadas sem correção)

## Como retomar
Abra uma sessão neste repositório (branch `claude/ambiente-cowork-integration-9x6dhp`), diga "retomar o projeto" e peça para ler `docs/MAPA.md`. Atualize as tabelas acima a cada avanço.
