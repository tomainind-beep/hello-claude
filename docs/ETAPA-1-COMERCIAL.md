# Etapa 1 — Comercial (prioridade máxima)

Definida pelo Leonardo em 02/10/2026. Escopo: do marketing e da captação de leads até o fechamento e a passagem para a produção. **Regra de condução:** seguir a ordem abaixo; se um passo travar por causa de outro, trabalhar no que destrava e voltar.

## O que já existe
- **Gerador de propostas** em produção (Cloud Run + Airtable). Intocado.
- Airtable `Tomain Comercial` com 3 tabelas: `Clientes` (~700), `Propostas` (Status só "Em aberto" / "Fechada"; vendedor), `Pedidos` (fila do gerador).
- **Não existe**: tabela de leads, de oportunidades/funil, de interações (follow-up), de origem/campanha.
- Histórico 2021–2025 pronto para importar: `CRM Tomain — base.xlsx` (430 propostas, 66 clientes, desfechos revisados), mais a lista de retomada de 2025 sem desfecho.

## Ordem e dependências

| # | Passo | Depende de | Pode começar já? |
|---|---|---|---|
| **C1** | **CRM mínimo**: tabelas Negócios (funil), Leads, Interações, Origens; importar o histórico | Aprovação do esquema pelo Leonardo | Sim (esquema) |
| **C2** | **Follow-up das propostas em aberto** (inclui a lista de retomada de 2025) | Só dos dados que já existem; usa o CRM quando ele nascer | **Sim — destrava valor sem esperar o CRM** |
| **C3** | **Leads**: entrada, qualificação, rascunho de resposta, ligação lead → proposta | C1 (onde o lead mora) e saber de onde os leads chegam | Parcial |
| **C4** | **Marketing e criativos**: qual anúncio/campanha gera lead que vira **venda** (não só lead barato) | C1 + C3 + exportação dos dados de anúncio | Não |
| **C5** | **Prospecção ativa** (base da Receita, filtros, redes sociais) | C1; decisão sobre WhatsApp e LGPD; base da Receita no ar | Não |
| **C6** | **Fechamento → produção**: ficha de fechamento, contrato, aviso à produção e ao financeiro | C1 (status Fechada) + Contratos (já testado) | Parcial |

## Como o CRM é desenhado (proposta para aprovação)
- **Não alterar as 3 tabelas do gerador.** Elas não são tocadas: criamos tabelas novas na mesma base, ligadas pelo **nº da proposta** (a chave que já vale em toda a casa). Assim o gerador não corre risco.
- **Negócios** (uma linha por oportunidade/proposta): número, cliente, vendedor, valor, **etapa do funil**, data do último contato, próxima ação e data, motivo de perda, origem.
- **Etapas do funil** (alinhadas ao `docs/FLUXO-DE-ESTADOS.md`): Lead novo → Qualificado → Proposta solicitada → Proposta enviada → Em negociação → **Fechada** | Perdida | Sem retorno.
- **Leads**: nome/empresa, contato, origem (campanha, anúncio, formulário), data, qualificação, quem atende, virou negócio? (ligação com Negócios).
- **Interações**: negócio, data, canal (WhatsApp, e-mail, telefone, visita), resumo, próxima ação.
- **Origens/Campanhas**: plataforma, campanha, criativo, período, custo (quando houver) → permite medir **custo por venda**.

## Agentes desta etapa (todos sob pedido, rascunho + aprovação)
| Agente | Faz | Passo |
|---|---|---|
| Comercial | Mantém o funil, aponta propostas paradas, sugere o próximo contato, redige a mensagem (não envia) | C1, C2 |
| Captação / Leads (novo) | Qualifica lead, responde rascunho, liga lead → negócio | C3 |
| Marketing | Cruza campanha e criativo com resultado em venda; sugere criativos | C4 |
| Prospecção | Lista qualificada e rascunho (não dispara) | C5 |
| Propostas | Continua só observando o gerador; passa a ler Negócios | C1 |
| Contratos/Jurídico | Contrato a partir da proposta fechada | C6 |

## Bloqueios conhecidos
- **Origem dos leads de tráfego pago**: não sei por onde chegam (WhatsApp, formulário, Meta Lead Ads, site). Sem isso C3 e C4 ficam só no esquema. Não há conector de anúncios nesta central; dados entram por exportação (CSV) ou colagem.
- **Base da Receita**: não foi enviada; C5 só depois.
- **Disparo em massa por WhatsApp**: desligado por decisão de 30/09.
- **Numeração duplicada no histórico**: 6 propostas com número herdado de cópia precisam de conferência humana antes da importação.
- **Vendedores**: o gerador lista vendedores de empresas parceiras (Prymaxx, Fenox). Preciso saber quem de fato faz follow-up e quem aprova o contato com o cliente.

## Primeiros passos propostos
1. **C2 agora** (não depende de nada): levantar as propostas "Em aberto" e a lista de retomada de 2025, ordenar por valor e tempo parado, e entregar a lista de follow-up com mensagem sugerida para você aprovar.
2. **C1 em paralelo**: você aprova o esquema acima e eu crio as tabelas (só depois da sua aprovação, por mexer no Airtable de produção).
