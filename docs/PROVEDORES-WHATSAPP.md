# Provedores para a captura de conversas do WhatsApp

Objetivo: ligar os **dois números** do WhatsApp Business (que o time continua usando no celular e no computador) à API oficial, para receber as mensagens, ler e condensar no CRM. **Só leitura** nesta fase. Contexto: `docs/CAPTURA-WHATSAPP.md`.

> Pesquisa de 03/10/2026 em fontes públicas (blogs e documentações de provedores). **Preços e regras mudam e vêm de terceiros: confirmar com a Meta e com o provedor antes de decidir.** Alguns sites de documentação estavam bloqueados neste ambiente.

## O que a pesquisa confirmou
| Ponto | O que as fontes dizem | Confiança |
|---|---|---|
| **Coexistência** (app WhatsApp Business e API no mesmo número) | Existe e é suportada em vários países, **incluindo o Brasil** | Boa (várias fontes) |
| **Histórico** | Na ligação, sincroniza até **6 meses** de conversas | Boa |
| **Mensagens enviadas pelo app** | Aparecem também na API (o sistema vê os dois lados da conversa) | Boa |
| **Regra dos 13 dias** | O aplicativo precisa ser aberto pelo menos a cada 13 dias | Boa |
| **Limitações** | Listas de transmissão ficam desativadas; mensagens temporárias em chats 1:1 e "ver uma vez" não funcionam; **grupos não sincronizam com a API** | Boa |
| **Origem do anúncio** | Em conversa que vem de anúncio "clique para WhatsApp", a primeira mensagem traz no webhook os dados do anúncio (id do anúncio e um **ctwa_clid**) | Boa |
| **Custo de receber** | Mensagens de serviço (resposta ao cliente) custam pouco ou nada; há janela gratuita de **72 horas** para conversas abertas por anúncio. Relatos citam ~R$ 0,035 por mensagem de serviço/utilidade e ~R$ 0,32 por mensagem de marketing no Brasil | Média: confirmar |

Como a fase atual **não envia nada**, o custo da Meta tende a ser perto de zero. O custo real é a **mensalidade do provedor**, a hospedagem do receptor e a análise com Claude.

## Candidatos para cotar
| Tipo | Exemplos | Bom para | Cuidado |
|---|---|---|---|
| **Provedor oficial (BSP) só de conexão** | 360dialog, YCloud, Twilio | Ligar o número e entregar mensagens por webhook, a custo previsível; nós construímos o resto no Airtable | Perguntar coexistência e histórico (ver lista abaixo) |
| **Provedor oficial brasileiro** | Zenvia | Suporte e cobrança em reais, atendimento em português | Pode empurrar plataforma própria de atendimento |
| **Plataforma de atendimento/CRM** | Respond.io, Wati | Caixa de entrada compartilhada, bots, relatórios prontos | Cria um **segundo CRM** (conflita com "um dado, um dono"); mensalidade por usuário |
| **Provedor com API não oficial** | Z-API (o produto usado nos scripts de prospecção) | Rápido e barato | **Risco de banimento do número de vendas e violação dos termos do WhatsApp. Não usar nos números dos leads.** (A Z-API também fala de coexistência oficial em seu blog; tratar como produto à parte e confirmar.) |

**Recomendação:** começar cotando **BSP de conexão** (360dialog, YCloud, Twilio e Zenvia) e comparar com uma plataforma (Respond.io ou Wati) apenas como referência de preço.

## Perguntas para cada provedor (copiar e enviar)
1. Vocês suportam **WhatsApp Business App Coexistence** para números brasileiros? Em quais condições?
2. Na ligação, o **histórico de até 6 meses** é entregue ao webhook, ou só fica no aplicativo? Em que formato?
3. As mensagens **enviadas pelo aplicativo** (pela equipe) chegam ao webhook, com horário e remetente? (Preciso medir o tempo até a primeira resposta.)
4. O webhook inclui o objeto de **origem do anúncio** (referral, ad id, ctwa_clid) nas conversas vindas de "clique para WhatsApp"?
5. Vocês cobram por **mensagem recebida**, por conversa, por número, por usuário ou mensalidade fixa? Qual o valor para **2 números** e **somente receber**?
6. Posso usar **só a API/webhook**, sem a caixa de entrada de vocês? Existe taxa mínima?
7. Onde os dados ficam armazenados, por quanto tempo, e há **contrato de tratamento de dados (LGPD)**?
8. Posso **exportar** todo o histórico e **trocar de provedor** sem perder os números?
9. Como funciona a ligação dos **dois números** quando pertencem a **contas Meta diferentes** (Tomain e vendedores)?
10. Qual o prazo de implantação, o que preciso preparar (Business Manager verificado, documentos) e quanto custa a implantação?
11. Há limite de mensagens por segundo ou de mensagens por mês no plano?
12. O que acontece com o aplicativo no celular durante e depois da ligação (perde alguma função que usamos hoje)?

## Antes de ligar qualquer número
- **Business Manager verificado** na Meta e quem é o administrador de **cada** número.
- O **segundo número** pertence aos vendedores: precisa da **autorização deles** e, provavelmente, da ligação feita por quem administra a conta.
- **Aviso de privacidade** para quem escreve à empresa; equipe ciente de que as conversas são registradas e analisadas.
- Decidir **quem acessa** as conversas brutas (só administrador) e os resumos (vendedor vê os seus).

## Fontes consultadas
Resultados de busca de 03/10/2026: documentação e blogs de [360dialog](https://docs.360dialog.com/docs/waba-management/the-360-client-hub/embedded-signup/whatsapp-coexistence), [YCloud](https://www.ycloud.com/blog/whatsapp-business-app-coexistence-meta-update), [Respond.io](https://respond.io/help/whatsapp/whatsapp-coexistence), [Wati](https://support.wati.io/en/articles/11822402-introducing-whatsapp-coexistence), [Zenvia (preços 2026)](https://zenvia.com/en/new-whatsapp-business-pricing-rules-for-2026/), [Twilio (ctwa_clid)](https://www.twilio.com/en-us/changelog/new--click-id--callback-parameter-for-inbound-whatsapp-messages-), [Z-API (coexistência)](https://z-api.io/blog/en/whatsapp-coexistence-how-to-use-the-app-and-api-with-the-same-number/). São fontes de terceiros; não substituem a documentação da Meta.
