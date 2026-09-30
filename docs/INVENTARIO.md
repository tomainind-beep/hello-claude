# Inventário do que já existe (30/09/2026)

Tudo foi feito no Cowork (computador do Leonardo). Legenda: **visto** = aparece nos conectores desta central; **local** = só no Cowork, ainda não visível.

| Frente | Estado | Onde está | Prioridade de migração |
|---|---|---|---|
| Gerador de propostas | Funcionando, atende | **visto**: Cloud Run `tomain-gerador`, Airtable `Tomain Comercial`, Drive `Tomain — Gerador` | Não mexer (ver `GERADOR-EM-PARALELO.md`) |
| Gerador de contratos | Funcionando | **visto** (Drive `Tomain — Agentes`) | Alta |
| Agente jurídico (plugin Claude) | Criado | **visto** (Drive) | Alta: base do agente Jurídico |
| Integração das áreas / Financeiro | Tentativas, bastante alimentado | **local** (painel `Painel de Gestão - Tomain.html`) | Média |
| Buscador de empresas (lista da Receita) | Scripts no Drive; a base da Receita não subiu | **visto** (scripts) | Média: agente de Prospecção |
| Marketing | Materiais de design (lâminas, manual da marca v1–v3) | **visto**: Drive (pastas do designer) | Baixa: já é insumo |
| Retomada de propostas de 2025 | Lista pronta | **visto**: planilha no Drive | Média: caso de uso imediato p/ Comercial |

## Como trazer o que é local
Para cada item local, o Leonardo exporta (ou aponta) para o Drive compartilhado da Tomain, numa pasta `Tomain — Agentes/<área>`:
1. Código/scripts do gerador de contratos e do buscador.
2. O prompt/arquivos do agente jurídico (o `CLAUDE.md` ou instruções que usou).
3. O que o Financeiro já leva de dados (só estrutura, sem valores, se preferir).

Depois cada item entra como agente em `agentes/`, rodando **em paralelo** ao original, que continua funcionando no Cowork até ficar equivalente.

---

# Atualização — material recebido no Drive (`Tomain — Agentes`, 30/09/2026)

## Jurídico (`juridico-e-contratos`)
- Estrutura de trabalho do agente jurídico: `01 - Contratos` (Em análise / Vigentes / Encerrados), `02 - Modelos`, `03 - Notificações e Cartas`, `04 - Pareceres`, `05 - Pesquisas Jurídicas`, `99 - Plugin e Config`.
- O agente é um plugin do Claude (`assistente-juridico.plugin`, arquivo zip). Ainda não abri o conteúdo do plugin.
- Aviso já embutido no material: informação jurídica geral e minutas; casos de valor alto ou litígio passam por advogado.

## Gerador de contratos (`Gerador de Contratos`)
- Gera "Contrato de Compra e Venda de Equipamentos com Reserva de Domínio" a partir de uma proposta aprovada, em Word e PDF, com timbrado.
- Motor: `gerar-contrato.js` (Node, biblioteca `docx`). Dois modelos: `enxuto` (~4 páginas, equipamento avulso) e `completo` (18 cláusulas, alto valor). Na dúvida, pergunta.
- Fixo: dados da Tomain, cláusulas, timbrado. Variável: comprador, fiador (opcional), valor, entrada, parcelas, prazo, garantia, FOB, diárias, foro (padrão Uberaba/MG).
- Regras: nº do contrato = nº da proposta; pasta `Contratos/Proposta <nº>/`; conferir valores e CNPJ; sem campos `<<...>>` pendentes; revisão jurídica final antes de assinar.
- O repositório Git dele foi copiado para o Drive (`.git`). O original está no GitHub privado `tomainind-beep/gerador-de-contratos`.

## Prospecção (`prospeccao-buscador-empresas/Captação Clientes`)
Pipeline em 4 etapas: (1) baixar a base pública de CNPJ da Receita; (2) `02_filtrar_cnae.py` filtra por setor (cosméticos, lubrificantes, saneantes, agro, química, alimentos/bebidas, farmacêutico) e estado (MG, GO, SP); (3) `03_enriquecer_linkedin.py` gera mensagem personalizada com Claude por empresa; (4) `04_disparar_whatsapp.py` dispara via Z-API. A lista da Receita não foi enviada (pesada demais).
- **Riscos a decidir antes de automatizar** — ver `agentes/prospeccao/AGENTE.md`.
- O enriquecimento por LinkedIn ainda não existe (roadmap do próprio pipeline).

## Integração Tomain (`Integração Tomain`) — o plano que o Leonardo já tinha
Contém `Decisões.md`, `Roteiro de Fases.md`, `Prontuário` e `_rascunhos`. Pontos que esta central **herda**:
- **Regra nº 1:** gerador de propostas congelado (`compor.py`, `triagem.py`, `registro.py`).
- **Um dado, um dono; congela ao fechar; mudou = revisão.** Chave única = número da proposta (ex.: 950A).
- Nuvem gerenciada, sem servidor próprio nem TI dedicada.
- Airtable é o eixo comercial (superou o AppSheet em 17/09).
- **Decisão de 13/08:** sistema em conta única (só o Leonardo), no máximo quatro acessos no futuro. **Isto conflita com o pedido dos terminais para funcionários** — precisa de decisão nova (ver `docs/TERMINAIS-FUNCIONARIOS.md`).
- Já planejados: agente de Relatório de Instalação/Start-up (piloto Trouw, proposta 814), descritivo de produção, contrato lendo o prontuário, financeiro (parcelas, NF, baixa), handoffs automáticos.
- Backups no GitHub privado: `gerador-de-propostas`, `gerador-de-contratos`, `integracao-tomain`.

## Financeiro (`financeiro-e-integracao`)
Contém extratos (Sicoob, BB), contratos de empréstimo, diagnóstico de contas a pagar e modelo financeiro. **Dado sensível: só o agente Financeiro lê, e só sob pedido.** Não foi aberto na revisão inicial.
