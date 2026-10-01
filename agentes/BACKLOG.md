# Agentes em espera

Ordem herdada de `Áreas futuras de integração.md`: **nenhum entra antes do núcleo rodar** (comercial → projeto → produção → compras → financeiro → fiscal).

| Agente | O que faz | Elo | Prioridade |
|---|---|---|---|
| **Documentação Técnica** | Gera, a partir da Ficha de Dados do Equipamento: Manual de Operação e Manutenção, Laudo NR-12 (APR) e Relatório de Instalação/Start-up/Treinamento. Engenheiro revisa e assina o laudo (ART obrigatória); assinatura do cliente no start dispara a garantia | Em andamento no Cowork (modelos v1, piloto Trouw, proposta 814) | **Alta** (já iniciado) |
| **Projeto** | Descritivo de Projeto (com contato do cliente, sem valores); desenhos e BOM preliminar | estado 3 e 3b | Média |
| **Produção** | Descritivo de Produção (sem preço, sem dados do cliente), OP, status de fabricação | estados 3b e 4 | Média |
| **Compras** | Lista de faltas, cotações a 2–3 fornecedores, comparativo preço × prazo | estados 4 e 5 | Média |
| **Fiscal/Contábil** | NF, baixa de recebimentos, relatório mensal para a contabilidade | estados 7–9 | Média (já "meio dentro") |
| **Estoque** | Inventário com mínimos; BOM baixa estoque; mínimo dispara cotação | Compras | Baixa |
| **Pós-venda / Assistência** | Registro por nº de série ↔ nº do negócio, preventiva, garantia | Já previsto em `agentes/assistencia-tecnica/` | Baixa |
| **Qualidade de produto** | Checklist de inspeção final, não conformidades | (distinto do agente Qualidade, que testa os agentes) | Baixa |
| **Expedição** | Frete CIF, agenda de embarque, comprovante libera parcela | Financeiro | Baixa |
| **RH** | Férias, documentos, treinamentos, vencimento de EPIs/NRs | — | Baixa |
| **Indicadores** | Margem por negócio, prazo real × prometido, inadimplência | Prontuário | Coroamento |

Questões abertas herdadas: convenção de **nº de série** (hoje ad hoc: `T-FV-006/2026`); índice confiável de propostas fechadas recentes; endereço de entrega que pode divergir do CNPJ da proposta.
