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
| **C3** | **Leads**: captura automática das conversas do WhatsApp, qualificação, resumo no CRM, ligação lead → proposta | C1 (onde o lead mora) e saber de onde os leads chegam | Parcial |
| **C4** | **Marketing e criativos**: qual anúncio/campanha gera lead que vira **venda** (não só lead barato) | C1 + C3 + exportação dos dados de anúncio | Não |
| **C5** | **Prospecção ativa** (base da Receita, filtros, redes sociais) | C1; decisão sobre WhatsApp e LGPD; base da Receita no ar | Não |
| **C6** | **Fechamento → produção**: ficha de fechamento, contrato, aviso à produção e ao financeiro | C1 (status Fechada) + Contratos (já testado) | Parcial |

## Como o CRM é desenhado (APROVADO em 03/10 e CRIADO no Airtable)
Tabelas criadas na base `Tomain Comercial`: `Origens`, `Negocios`, `Leads`, `Interacoes`. As 3 tabelas do gerador não foram tocadas.
- **Não alterar as 3 tabelas do gerador.** Elas não são tocadas: criamos tabelas novas na mesma base, ligadas pelo **nº da proposta** (a chave que já vale em toda a casa). Assim o gerador não corre risco.
- **Negócios** (uma linha por oportunidade; um negócio agrupa uma ou mais propostas): número, cliente, vendedor, valor, **etapa do funil**, data do último contato, próxima ação e data, motivo de perda, origem.
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

## Como o comercial funciona hoje (informado pelo Leonardo em 03/10)
- **Leads**: a campanha roda no **Meta (Facebook/Instagram)** e o **primeiro contato é pelo WhatsApp Business** (aplicativo no celular e no computador), em **dois números** ligados aos links dos anúncios.
- **Follow-up**: feito pelos próprios **vendedores (Prymaxx e Fenox)** e pela **Taynara (apoio comercial)**. Os agentes preparam lista, prioridade e rascunho; **quem envia a mensagem é uma pessoa**.
- O lead nasce numa conversa de WhatsApp, que esta central **não consegue ler**. Por isso a entrada do lead no CRM depende de registro (Taynara/vendedor, ou importação) e da atribuição à campanha, descrita abaixo.

### Atribuição campanha → lead → venda (para o C3/C4)
Em anúncio "clique para WhatsApp", a conversa abre com uma mensagem pré-preenchida. **Sugestão simples e sem custo**: incluir nessa mensagem um **código por criativo** (ex.: `Olá, vi o anúncio [T5K-VID2]`). Assim a primeira mensagem do lead já diz de qual anúncio veio, e o registro do lead leva o código. Sem isso, o custo por venda por criativo não é mensurável. Integração automática (API oficial do WhatsApp e dos anúncios) fica para depois e exige decisão sobre LGPD e custo.

Captura automática das conversas do WhatsApp (C3/C4): ver `docs/CAPTURA-WHATSAPP.md` (a exportação manual foi descartada pelo Leonardo em 03/10). Opções de leitura: `docs/LEITURA-META-WHATSAPP.md`.

## Resultado do C2 (03/10/2026)
Planilha de follow-up criada no Drive: `Tomain — Agentes/comercial-crm/Follow-up — propostas em aberto (03-10-2026)`.
- **99 propostas "Em aberto"**, todas entre 04/07 e 02/10/2026, somando R$ 18,3 mi **nominais** (não é pipeline: ver achados).
- **52 paradas há mais de 21 dias**, 35 entre 8 e 21 dias, 12 recentes (até 7 dias).
- **26 de alto valor** (≥ R$ 150 mil), somando R$ 13,1 mi nominais; 68 médias; 4 de peça/serviço.
- Colunas para o time preencher: quem faz o follow-up, último contato, próxima ação, data, situação, motivo de perda.
- Regra de temperatura (transparente): recente ≤ 7 dias; atenção 8–21; parada > 21. Ação sugerida por faixa; **não** foi escrita mensagem para nenhum cliente.

### Achados do Airtable (a conferir com o Leonardo)
1. **O status do funil não está sendo mantido.** Só existem "Em aberto" e "Fechada", e há negócios que provavelmente já fecharam (houve contrato gerado para pelo menos duas dessas propostas) ainda como "Em aberto".
2. **Há um registro de teste do gerador** na lista (proposta 1001, "TESTE MIGRACAO"); deve ser excluído do funil.
3. **Um cliente costuma ter várias propostas** (variantes/opções do mesmo negócio). O CRM precisa tratar **Negócio (1) → Propostas (N)**, senão o funil conta o mesmo cliente várias vezes.
4. **Um valor parece fora do padrão** (rotuladora T-ROT 2000-C a R$ 220 mil, contra R$ 55 mil de tabela): conferir se é erro de lançamento ou quantidade.
5. Muitas propostas estão no nome do **Leonardo** como vendedor; para o follow-up isso precisa de um responsável efetivo (a coluna "Quem faz o follow-up").

## Bloqueios conhecidos
- **Leads (resolvido em parte)**: chegam pelo WhatsApp a partir do Meta. Falta definir como o lead é registrado e como se identifica o anúncio de origem (ver atribuição acima). Não há conector de anúncios nem de WhatsApp nesta central; os dados entram por exportação (CSV) ou colagem.
- **Base da Receita**: não foi enviada; C5 só depois.
- **Disparo em massa por WhatsApp**: desligado por decisão de 30/09.
- **Numeração duplicada no histórico**: 6 propostas com número herdado de cópia precisam de conferência humana antes da importação.
- **Vendedores (resolvido)**: o follow-up é feito pelos vendedores Prymaxx e Fenox e pela Taynara. Em aberto: quem aprova a mensagem antes de ir ao cliente, e como os vendedores externos acessam a planilha (hoje só o Leonardo tem acesso).

## Primeiros passos propostos
1. **C2 agora** (não depende de nada): levantar as propostas "Em aberto" e a lista de retomada de 2025, ordenar por valor e tempo parado, e entregar a lista de follow-up com mensagem sugerida para você aprovar.
2. **C1 em paralelo**: você aprova o esquema acima e eu crio as tabelas (só depois da sua aprovação, por mexer no Airtable de produção).
