# Captura automática de conversas do WhatsApp → CRM

Decisão do Leonardo em 03/10/2026: **a exportação manual não serve**. O objetivo é automático: a conversa é lida continuamente, analisada e **condensada no CRM** (resumo, etapa, próxima ação, origem do anúncio), sem alguém exportar nada.

## Como funciona (arquitetura)
```
Anúncio Meta (clique para WhatsApp)
        │
WhatsApp Business (app no celular/computador — continua sendo usado pelo time)
        │  conexão oficial da Meta (API do WhatsApp Business, modo "coexistência")
        ▼
Webhook (receptor) ──► Airtable: tabela Mensagens (bruto, uma linha por mensagem)
                                │
                  Agente Analista (Claude), 1x por dia ou a cada conversa encerrada
                                │
                                ▼
                 Airtable: Leads / Negócios / Interações (condensado)
                 etapa · resumo · objeções · próxima ação · origem do anúncio · tempo de resposta
```
- **Atribuição automática**: quando o lead chega de um anúncio "clique para WhatsApp", a API entrega junto da mensagem os dados do anúncio de origem (id do anúncio, título). O custo por conversa e por venda por criativo passa a sair sozinho, sem código na mensagem.
- **O time continua usando o aplicativo normalmente.** A API só espelha as mensagens.
- **Somente leitura nesta fase**: o sistema recebe e analisa; **não envia nada**. Nenhuma resposta automática a lead.

## O que o Analista condensa por lead
Etapa do funil · resumo de 3–5 linhas · o que o lead pediu (produto, volume, prazo) · objeções · temperatura · próxima ação sugerida e data · tempo até a 1ª resposta e tempo entre respostas · anúncio/campanha de origem · quem atendeu · alerta de "lead sem resposta há X horas". Tudo como **rascunho** que alimenta a planilha/CRM; a decisão e o contato continuam com as pessoas.

## Caminhos de implantação
| | A. Direto na API da Meta | B. Provedor oficial (BSP) | C. CRM pronto com WhatsApp |
|---|---|---|---|
| O que é | Nós ligamos o número à API e recebemos o webhook | Um provedor oficial faz a ligação e entrega o webhook | Ferramenta completa de atendimento/CRM |
| Custo | Menor (hospedagem + análise) | Mensalidade do provedor | Mensalidade por usuário |
| Esforço | Maior (conta Meta, verificação, webhook) | Médio (onboarding guiado) | Baixo, mas **cria um segundo CRM** |
| Controle | Total | Bom | Menor; fere "um dado, um dono" |
| Recomendação | Se houver um desenvolvedor | **Provável melhor ponto de partida** | Só se aceitar trocar o eixo do CRM |

Recomendo **B**: um provedor oficial resolve o onboarding dos dois números e entrega as mensagens por webhook; o resto (receptor, análise, CRM) é nosso, no Airtable.

## O que precisa ser confirmado antes de contratar
1. **Coexistência** (manter o app WhatsApp Business e a API no mesmo número): disponibilidade no Brasil, requisitos e limites (por exemplo, o que não sincroniza), e se traz o **histórico** recente de conversas na ligação. Perguntar ao provedor.
2. **Custos atuais** da Meta e do provedor. Receber mensagem de lead normalmente não gera cobrança, mas a tabela muda: conferir antes.
3. **Verificação do negócio** na Meta (Business Manager) e quem é o administrador.
4. **Os dois números**: o segundo pertence a uma conta Meta de outra pessoa (os vendedores)? A ligação exige autorização do dono de cada conta.

## Etapas e quem faz
| # | Etapa | Quem | Depende de |
|---|---|---|---|
| 1 | Escolher provedor e confirmar coexistência/custos | Leonardo (+ eu preparo as perguntas e a comparação) | — |
| 2 | Business Manager verificado; ligar o **número 1** (Tomain) | Leonardo, com o celular do número em mãos | 1 |
| 3 | Tabelas `Mensagens`, `Leads`, `Interações`, `Origens` no Airtable | Eu, **após sua aprovação do esquema** (C1) | aprovação |
| 4 | Receptor do webhook (Cloud Run, projeto separado do gerador) | Eu escrevo; Leonardo cria o projeto/credenciais | 1, 2 |
| 5 | Agente Analista (prompt, regras, testes) | Eu | 3, 4 |
| 6 | Ligar o **número 2** (vendedores) | Leonardo + vendedores | autorização deles |
| 7 | Painel: leads por anúncio, tempo de resposta, funil | Eu | 5 |

O que **posso fazer já**, sem esperar: o esquema do Airtable, o desenho do receptor e do Analista, e os critérios de análise. Para calibrar o resumo, bastam **3 a 5 conversas de teste** exportadas uma única vez (só calibração; não é o processo).

## Segurança, LGPD e regras
- Credenciais do provedor e da Meta ficam **só** no gerenciador de segredos do ambiente. Nunca no repositório.
- As conversas ficam em Airtable/Drive da Tomain, **nunca no GitHub**.
- É preciso **aviso de privacidade** (as pessoas escrevem para a empresa) e finalidade registrada (atendimento e melhoria comercial). Equipe ciente de que as conversas são registradas e analisadas.
- Nada de resposta automática nem disparo em massa. Fase atual: **só leitura e análise**.
- Acesso aos resumos por perfil: vendedor vê os seus; conversas brutas só administrador.
