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

## Análise do YCloud, plano Growth (03/10/2026)
Pedido do Leonardo: o plano Growth do YCloud cobre os dois números? Resultado, a partir da documentação pública do YCloud (o site não abre neste ambiente; vi só resultados de busca com trechos dele):

| Necessidade | YCloud | Atende? |
|---|---|---|
| 2 números | Growth: **3 canais** (Free: 2 canais) | Sim |
| Manter o app WhatsApp Business em uso | Coexistência documentada: app versão 2.24.17 ou superior, ligação por QR code | Sim |
| Histórico das conversas | Até **6 meses**, entregue por webhook próprio, se o dono autorizar na ligação; o app deve ficar aberto durante a sincronização | Sim |
| Mensagens enviadas pela equipe (para medir tempo de resposta) | Evento de eco (`smb.message.echoes`) entrega as enviadas pelo app | Sim |
| **Anúncio de origem** | O webhook de mensagem recebida traz o objeto `referral` (id do anúncio, título e `ctwa_clid`) em conversas de anúncio clique-para-WhatsApp | Sim |
| Preço sem margem sobre a Meta | Repasse da tarifa da Meta, sem acréscimo | Sim |
| Receptor próprio (nosso) | Webhook para o nosso endereço | Sim |

**Preço: atenção.** O Growth custa **US$ 39 por mês, em dólar, e não R$ 39**. A página lista também "US$ 468 por ano", o que sugere cobrança anual; **confirmar se há plano mensal**. Inclui 2 usuários da caixa de entrada deles, que não vamos usar, porque lemos pelo webhook. Canais extras: US$ 5 cada.

**O plano Free também tem 2 canais e API de mensagens ilimitada.** Pode bastar para começar. **Perguntar ao YCloud** se coexistência, histórico e webhook funcionam no Free; se sim, testamos o número 1 sem custo e subimos para o Growth depois, se precisar.

**Cuidados que não mudam com o plano**
- O YCloud guarda o histórico por 6 meses; o nosso receptor precisa guardar o resto.
- **Correção de 03/10:** as duas linhas são da Tomain (Leonardo e Taynara), não dos vendedores. Os vendedores externos ficam fora do CRM automático, então **não há autorização de terceiros a obter**.
- **Uma conta Free comporta as duas linhas (2 canais).** Não é preciso criar duas contas. Plano de teste: começar com **uma linha** na conta Free, rodar por semanas e só então ligar a segunda.
- Regra dos 13 dias (abrir o app) e limitações da coexistência (grupos, listas de transmissão) continuam valendo.
- Exigir contrato de tratamento de dados (LGPD) do YCloud.

## Links para cotar (páginas oficiais de preço)
| Provedor | Página de preços / contato | O que a busca de 03/10 indicou (confirmar na página) |
|---|---|---|
| 360dialog | https://360dialog.com/pricing | Plano Regular ~€ 49 por número por mês (2 números ~€ 98/mês), sem repasse sobre as taxas da Meta; Premium ~€ 99 por número. Tem documentação de coexistência |
| YCloud | https://www.ycloud.com/pricing | Plano grátis (2 canais) e Growth ~US$ 39/mês (3 canais); sem margem sobre a Meta. Tem documentação de coexistência |
| Twilio | https://www.twilio.com/en-us/whatsapp/pricing | ~US$ 0,005 por mensagem enviada ou recebida, além da Meta. Cobrar por mensagem recebida pesa em volume alto. Coexistência: confirmar |
| Zenvia | https://zenvia.com/en/prices/ (e https://zenvia.com) | Planos a partir de ~R$ 100/mês, mais taxa de ativação; botão "Fale com Vendas" na página. Coexistência: confirmar |

Ordem sugerida para cotar: **360dialog e YCloud primeiro** (ambos publicam coexistência), depois Zenvia (suporte em português e em reais) e Twilio como referência. Valores vêm de resultados de busca e blogs; **o que vale é o que aparece na página e no orçamento recebido**.

**Mensagem pronta (colar no formulário ou e-mail de cada um):**
> Somos uma fabricante de máquinas industriais no Brasil e recebemos leads de anúncios clique-para-WhatsApp em 2 números do WhatsApp Business (aplicativo). Queremos ligar os 2 números à API oficial em modo de coexistência, mantendo o aplicativo em uso, e receber por webhook todas as mensagens (recebidas e enviadas pela equipe) com os dados de origem do anúncio, apenas para leitura e análise. Não vamos enviar mensagens em massa. Por favor, enviem: preço para 2 números, taxas por mensagem, histórico de até 6 meses na ligação, prazo de implantação, requisitos e contrato de tratamento de dados (LGPD).

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
