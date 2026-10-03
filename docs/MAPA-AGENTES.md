# Mapa de agentes e conexões

Versão visual (privada, só o Leonardo abre): https://claude.ai/artifact/QvCQMHtaQpipM4uM7MNZEr

Estado em 03/10/2026. **No ar:** CRM no Airtable e Gerador de Propostas. **Em andamento:** Comercial (planilha de follow-up). **Definidos:** Orquestrador, Analista de Leads, Marketing, Prospecção, Contratos e Jurídico, Propostas, Documentação Técnica, Financeiro, Qualidade, Melhoria. **Em espera:** Projeto e Produção, Compras.

```mermaid
flowchart TD
  L[Leonardo<br/>aprova toda ação externa] -->|comando| O[Orquestrador]
  M[Meta Ads] -->|clique| W[WhatsApp Business<br/>2 números]
  W -->|via API oficial, só leitura| A[Analista de Leads]
  A -->|resumo + origem| C[(CRM no Airtable<br/>Origens · Leads · Negócios · Interações)]
  R[Base da Receita] --> P[Prospecção<br/>lista + rascunho]
  P -->|leads| C
  C <-->|etapa e prazo| CO[Comercial<br/>funil e follow-up]
  M -.->|relatório de anúncios| MK[Marketing]
  MK -->|criativos e roteiro| CO
  CO -->|pede proposta| G[Gerador de Propostas<br/>Cloud Run · congelado]
  G -.->|leitura| PR[Propostas agente<br/>só observa]
  C -->|proposta fechada| CJ[Contratos e Jurídico]
  CJ -->|contrato assinado| PP[Projeto e Produção<br/>em espera]
  PP -->|faltas| CP[Compras<br/>em espera]
  CP -->|pedidos| F[Financeiro<br/>só leitura]
  PP -->|ficha do equipamento| DT[Documentação Técnica]
  Q[Qualidade] -.->|testa e audita| O
  ME[Melhoria de Sistema] -.->|propõe por PR| O
```

Regras de todas as ligações: tudo sob pedido; nenhum agente envia mensagem, e-mail ou proposta ao cliente sozinho; dinheiro e fiscal, o agente prepara e uma pessoa aprova; dados de cliente ficam no Airtable e no Drive, nunca no GitHub.
