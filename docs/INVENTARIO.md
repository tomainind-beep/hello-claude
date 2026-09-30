# Inventário do que já existe (30/09/2026)

Tudo foi feito no Cowork (computador do Leonardo). Legenda: **visto** = aparece nos conectores desta central; **local** = só no Cowork, ainda não visível.

| Frente | Estado | Onde está | Prioridade de migração |
|---|---|---|---|
| Gerador de propostas | Funcionando, atende | **visto**: Cloud Run `tomain-gerador`, Airtable `Tomain Comercial`, Drive `Tomain — Gerador` | Não mexer (ver `GERADOR-EM-PARALELO.md`) |
| Gerador de contratos | Funcionando | **local** | Alta: pedir export |
| Agente jurídico (Claude Code) | Criado | **local** | Alta: vira base do agente Jurídico |
| Integração das áreas / Financeiro | Tentativas, bastante alimentado | **local** (painel `Painel de Gestão - Tomain.html`) | Média |
| Buscador de empresas (lista da Receita) | Existe; faltam filtros e redes sociais | **local** | Média: base do agente Comercial/Prospecção |
| Marketing | Materiais de design (lâminas, manual da marca v1–v3) | **visto**: Drive (pastas do designer) | Baixa: já é insumo |
| Retomada de propostas de 2025 | Lista pronta | **visto**: planilha no Drive | Média: caso de uso imediato p/ Comercial |

## Como trazer o que é local
Para cada item local, o Leonardo exporta (ou aponta) para o Drive compartilhado da Tomain, numa pasta `Tomain — Agentes/<área>`:
1. Código/scripts do gerador de contratos e do buscador.
2. O prompt/arquivos do agente jurídico (o `CLAUDE.md` ou instruções que usou).
3. O que o Financeiro já leva de dados (só estrutura, sem valores, se preferir).

Depois cada item entra como agente em `agentes/`, rodando **em paralelo** ao original, que continua funcionando no Cowork até ficar equivalente.
