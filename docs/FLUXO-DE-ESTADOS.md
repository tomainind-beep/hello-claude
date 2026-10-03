# Fluxo de estados — como os agentes se encaixam

Fonte: `Integração Tomain/Fluxo de estados — visão do agente.md` (rascunho v0.1 do Leonardo, 22/07/2026). Aqui está a versão adaptada à central.

**Ideia:** cada negócio (chave = nº da proposta, ex. 950A) anda por estados. Quando um status muda, **um agente age**, escreve **só na seção da área dona** do prontuário e avisa a área seguinte. Ninguém redigita.

**Regras permanentes:** um dado, um dono · congela ao fechar (mudou = revisão: 950A → 950B) · **dinheiro e fiscal: o agente prepara, a pessoa aprova**.

| # | Gatilho | Agente responsável | Escreve em | Aprovação |
|---|---|---|---|---|
| 1 | Proposta solicitada | Propostas (insumos; o gerador segue congelado) | comercial | Vendedor confere |
| 2 | Enviada | Comercial (registra envio, agenda follow-up) | comercial | — |
| 3 | **Fechada** (piloto) | Contratos/Jurídico + Documentação (descritivos de projeto e produção); congela cliente+comercial | contrato, projeto, produção | Projeto e produção validam |
| 3b | Desenhos liberados | Produção (descritivo definitivo + BOM) | produção | Produção confirma |
| 4 | Em preparação | Compras/Estoque (lista de faltas) | produção, compras | Produção confirma |
| 5 | A comprar | Compras (cotações) + Financeiro (agenda pagamentos) | compras, financeiro | **Compras e financeiro aprovam** |
| 6 | Fechada (paralelo) | Financeiro (parcelas a receber, cobranças) | financeiro | **Financeiro aprova** |
| 7 | Produção concluída | Financeiro/Fiscal (prepara NF; libera parcela "no embarque") | financeiro, fiscal | **NF conferida** |
| 8 | Faturado | Financeiro (baixa, lembretes de atraso) | financeiro | Cobrança aprovada |
| 9 | Fechamento do mês | Fiscal/Contábil (relatório para a contabilidade) | fiscal | **Sempre** |
| 10 | Alteração após Fechada | Orquestrador abre revisão e re-notifica | negócio | Dono confirma |

## O que isso muda na central
- O **Orquestrador** passa a ser, além do "comando único", o **disparador por mudança de status**. Enquanto o painel central não existir, os gatilhos são **comandos do Leonardo**, no modo "tudo sob pedido".
- Surgem agentes que eu não tinha: **Projeto, Produção, Compras, Fiscal/Contábil, Documentação Técnica**. Estão em `agentes/BACKLOG.md`, na ordem que você já definiu ("nenhuma entra antes do núcleo rodar").
- O piloto da linha 3 (950A) vira o caso de teste do agente Qualidade.
