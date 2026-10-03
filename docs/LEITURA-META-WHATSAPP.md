# Leitura de Meta Ads e WhatsApp (somente leitura)

> **Atualização 03/10:** o Leonardo rejeitou a exportação manual como solução (não é automática). A direção passou a ser a **captura contínua pela API oficial**, descrita em `docs/CAPTURA-WHATSAPP.md`. O caminho 1 abaixo fica apenas como **calibração** (3 a 5 conversas de teste).

Pedido do Leonardo em 03/10/2026: ler os leads que chegam pelo WhatsApp a partir dos anúncios do Meta e analisar as duas contas (Meta Ads e WhatsApp), **sem enviar nada**.

## Situação nesta central
- **WhatsApp**: não há conector de WhatsApp disponível. Nenhuma ferramenta daqui lê conversas.
- **Meta Ads**: não há conector oficial instalado. Existem conectores de terceiros de leitura de métricas de anúncios (ex.: Windsor.ai, Supermetrics) que o Leonardo teria de conectar pelas configurações de conectores; envolvem OAuth com a conta de anúncios, possível custo e envio de dados de campanha a um terceiro. Um deles (Adspirer) também cria e altera campanhas: **descartado**, por permitir escrita.
- Gmail, Drive, Agenda e Airtable já estão conectados.

## Como o time usa o WhatsApp (informado em 03/10)
- **WhatsApp Business (aplicativo)**, no celular e no computador (dispositivos conectados). **Dois números** recebem os leads vindos dos links dos anúncios.
- Consequências:
  - **Exportar conversa só funciona pelo celular**; o WhatsApp no computador não exporta.
  - Como é o aplicativo (e não a API), o caminho 1 serve já; o caminho 3 exigiria tratar **cada um dos dois números** (e a coexistência aplicativo + API, ainda a confirmar).
  - **Atribuição por número**: se cada anúncio/conjunto aponta para um número específico, o número já diz a origem em nível de campanha; o código por criativo na mensagem pré-preenchida refina para o nível do anúncio.
  - Várias pessoas podem atender o mesmo número por dispositivos conectados; isso dificulta saber quem respondeu e quando, sem registro no CRM.

## Etiquetas do WhatsApp Business (ganho imediato, sem integração)
O aplicativo permite **etiquetas** nas conversas. Sugestão alinhada ao funil do CRM, para o time usar já: `Lead novo` · `Qualificado` · `Proposta solicitada` · `Proposta enviada` · `Em negociação` · `Fechado` · `Perdido` · `Sem retorno`. As etiquetas não saem na exportação do chat, então a legenda de cada conversa exportada deve dizer a etapa.

## Caminhos, do mais seguro ao mais completo
| # | Caminho | Esforço | Risco | O que entrega |
|---|---|---|---|---|
| 1 | **Exportação manual** (CSV do Meta + conversas do WhatsApp em .txt, para uma pasta do Drive) | Baixo, uma vez | Nenhum | Análise de anúncios, tempo de resposta, objeções, perfil do lead bom |
| 2 | **Conector de leitura de métricas do Meta** (Windsor/Supermetrics) | Médio | Baixo (dados de campanha com terceiro) | Custo por conversa por anúncio, sempre atualizado |
| 3 | **WhatsApp Business Platform (API oficial da Meta)** com captura das mensagens recebidas no Airtable (Leads/Interações) | Alto (projeto) | Médio (LGPD, custo por conversa, migração do número) | Lead entra no CRM sozinho, com o anúncio de origem |
| ✗ | **API não oficial** (ex.: Z-API) no número principal | — | **Alto: risco de banimento do número de vendas** e violação dos termos do WhatsApp | Não recomendado |

Observação sobre o caminho 3: a Meta oferece um modo que permite manter o aplicativo WhatsApp Business e a API no mesmo número ("coexistência"). **A confirmar** disponibilidade no Brasil, custos e requisitos antes de decidir.

## Começar agora: caminho 1
Instruções para a equipe estão no Drive: `Tomain — Agentes/comercial-crm/entrada-meta-whatsapp/COMO EXPORTAR`. O que o agente de Leads/Marketing entrega a partir daí:
- Quais anúncios geram conversas e a que custo.
- Tempo até a primeira resposta da equipe.
- Em que ponto as conversas morrem e quais objeções aparecem.
- Perfil dos leads bons e sugestões de criativo e de roteiro de atendimento (rascunho para aprovação).

## Regras
- Só leitura; nada é enviado a lead nem cliente.
- Conversas têm dado pessoal: ficam **só no Drive**, nunca no GitHub; excluir trechos sensíveis (documento, senha, dado bancário); usar só para análise comercial.
- Qualquer integração contínua (caminhos 2 e 3) precisa de aprovação do Leonardo e de decisão sobre LGPD.
