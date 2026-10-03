# Decisões desta central

Uma linha por decisão: data · decisão · motivo. Herda as decisões de `Integração Tomain/Decisões.md`.

- **30/09/2026 · Tudo sob pedido.** Nenhum agente age sozinho; ação externa exige aprovação do Leonardo. Motivo: validar antes de automatizar.
- **30/09/2026 · Gerador de propostas fica intocado; a central o observa em paralelo.** Motivo: já atende e não pode ser estragado (Regra nº 1).
- **30/09/2026 · Só o Leonardo lança dados até o sistema estar validado por inteiro.** Terminais para funcionários são uma fase futura, ainda certa, mas só depois da validação. Isso confirma a decisão de 13/08 (conta única) por ora. Motivo: não colocar mais gente antes de o sistema estar pronto para dar seguimento.
- **30/09/2026 · Disparo automático de WhatsApp fica desligado.** A Prospecção entrega lista e rascunho. Motivo: risco de LGPD e de banimento do número.
- **01/10/2026 · A central segue o plano "Integração Tomain" (22/07), não cria um paralelo.** Fluxo de estados, prontuário por seções, papéis e a regra "dinheiro e fiscal: agente prepara, pessoa aprova" valem aqui. Motivo: o plano já existia e já tinha decisões do Leonardo.
- **22/07/2026 (herdada) · Contas dos funcionários só quando o sistema estiver desenvolvido, integrado e rodando.** Coerente com a decisão de 30/09.
- **02/10/2026 · Prioridade máxima: Etapa 1 — Comercial** (CRM, captação e leads, marketing/criativos, follow-up, fechamento, passagem à produção). Regra: seguir a ordem; se um passo travar, trabalhar no que destrava. As outras frentes (Jurídico, Documentação Técnica etc.) ficam atrás desta. Detalhe em `docs/ETAPA-1-COMERCIAL.md`.
- **02/10/2026 · O CRM nasce em tabelas novas, sem alterar as 3 tabelas do gerador.** Ligação pelo nº da proposta. Motivo: o gerador não pode correr risco (Regra nº 1).
- **03/10/2026 · Follow-up é feito por pessoas** (vendedores Prymaxx/Fenox e a Taynara); os agentes só priorizam e redigem rascunho. Leads entram por Meta → WhatsApp.
- **03/10/2026 · Planilha de follow-up no Drive é o CRM provisório** até o C1 ser aprovado e criado. Nenhum dado de cliente fica no GitHub.
- **03/10/2026 · Leitura de WhatsApp e Meta Ads: somente leitura, começando por exportação manual.** Sem API não oficial no número de vendas (risco de banimento). Integração contínua só com aprovação e decisão de LGPD.
- **03/10/2026 · Exportação manual de conversas descartada.** A captura das conversas do WhatsApp tem de ser automática e condensada no CRM. Direção: API oficial do WhatsApp Business (coexistência com o app), via provedor oficial, só leitura e análise nesta fase. Detalhe em `docs/CAPTURA-WHATSAPP.md`.
- **03/10/2026 · Esquema do CRM aprovado e criado no Airtable** (Origens, Negocios, Leads, Interacoes), sem alterar as tabelas do gerador. Mensagens brutas do WhatsApp não vão para o Airtable.
- **03/10/2026 · Garantia conta do embarque do equipamento (Leonardo).** Conflito aberto: Termos da proposta e Contratos dizem emissão da NF/faturamento; Manual diz expedição; Relatório diz assinatura do aceite. Pendente: confirmar se a NF sai no dia do embarque e, então, alinhar os textos (alterar Termos da proposta ou contrato exige autorização por serem fontes congeladas).
- **03/10/2026 · Garantia: 12 meses a partir da emissão da Nota Fiscal, que sai no dia do embarque (Leonardo).** Termos da proposta e Contratos já dizem isso e **não mudam**. Ficam a corrigir só os modelos de Documentação Técnica:
  - Manual §1.2: trocar "a partir da data de expedição, comprovada pelos documentos de expedição" por "a partir da data de emissão da Nota Fiscal, que coincide com o embarque do equipamento".
  - Relatório de Instalação §7: trocar "A partir da data de assinatura deste termo inicia-se a contagem do período de garantia, nos termos das condições de garantia entregues." por "O período de garantia é contado a partir da data de emissão da Nota Fiscal, que coincide com o embarque do equipamento, nos termos do Termo de Garantia entregue."
  - A frase "a assinatura dispara a garantia" em `Áreas futuras de integração.md` (Drive) também deixa de valer.
- **03/10/2026 · Provedor de WhatsApp pré-escolhido: YCloud (plano Growth, US$ 39/mês, ou Free para testar).** Atende os 7 requisitos técnicos pelas fontes públicas; falta confirmar com o YCloud: coexistência/histórico/webhook no Free, cobrança mensal ou anual, contrato LGPD. Preço é em dólar. Número 2 depende de autorização dos vendedores.
- **03/10/2026 · CRM automático só da Tomain; as duas linhas são Leonardo e Taynara.** Vendedores externos ficam fora (têm campanhas e números próprios). Começar com uma linha por tempo suficiente para validar, depois ligar a segunda. Uma conta Free do YCloud (2 canais) basta.
- **03/10/2026 · Primeiro acesso ao cliente é do vendedor externo.** Nenhum agente contata, lê conversa ou redige follow-up desse cliente até o vendedor repassar o follow-up à Tomain. Regra em `CLAUDE.md` e campos novos em `Negocios`.
