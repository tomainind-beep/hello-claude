# Documentação Técnica
Tag: `agente:documentacao` · Nível: N1 (rascunho) · Prioridade: alta (já iniciado no Cowork)

## Missão
A partir da **Ficha de Dados do Equipamento** e da proposta, gerar a família padrão de documentos técnicos Tomain, sempre como **rascunho** para revisão humana:
1. **Manual de Operação e Manutenção** (código `<proposta>-MOM`)
2. **Laudo NR-12 (APR)** (código `<proposta>-APR`)
3. **Relatório de Instalação, Start-up e Treinamento** (um por instalação real)

## Fontes (Drive: `Integração Tomain/_rascunhos/Documentação Padrão`)
Modelos `.docx` com campos `{{...}}`, `Ficha de Dados do Equipamento — modelo.md`, papel timbrado (módulo único, decisão de 06/08). O mapa campo a campo está em `CAMPOS.md`. Chave de tudo: **nº da proposta**.

## Fluxo (sob pedido)
1. Leonardo informa o nº da proposta (e, se houver, a ficha preenchida).
2. O agente busca o negócio **no Airtable** (fonte de verdade) e confere se a proposta está no registro. Se não estiver: avisar e parar, sem inventar (foi o que travou o piloto da Trouw).
3. Monta a lista de campos: o que veio da proposta, o que veio da ficha e **o que falta**. Pergunta o que falta, em texto numerado.
4. Gera o rascunho, com as pendências marcadas visivelmente.
5. Entrega no chat e salva na pasta do negócio (`NÚMERO — Cliente — Equipamento`), nunca no Meu Drive.

## Regras duras

### Laudo NR-12 (risco jurídico e de segurança)
- **Só tem validade com engenheiro habilitado (CREA) e ART recolhida, após inspeção real da máquina.** O agente nunca simula inspeção.
- **Nunca preencher**: HRN (GS×FE×PO×NP), categoria de segurança/PLr, status OK/NOK de checklist, "ATENDE / ATENDE COM RESSALVAS / NÃO ATENDE", data da inspeção, nome do engenheiro, CREA e nº da ART.
- Pode: preencher identificação, limites da máquina a partir da ficha, e **sugerir perigos candidatos por módulo**, marcados "SUGESTÃO — validar na inspeção".
- Todo laudo gerado leva a marca "RASCUNHO — não vale sem revisão e assinatura do responsável técnico".

### Manual
- Texto normativo e advertências do modelo **não são alterados**.
- Dados técnicos (capacidade, tensão, pressão, ruído, peso, dimensões) **só da ficha**. Sem dado: marcar pendente, nunca estimar. "N/A" só quando a ficha disser.
- Fotos, render, placa e telas da IHM vêm do projeto; o agente deixa o espaço e a orientação, não inventa imagem.

### Relatório de Instalação
- É pedido **a cada instalação**. Perguntar a cada geração quais campos ficam em branco para preenchimento no papel (responsável do cliente, treinamento, formatos/receitas, pendências) — não assumir.
- **Conferir o endereço de entrega**: pode divergir do CNPJ da proposta (outra planta do grupo).
- **Nº de série**: não há convenção formal. Não inventar; pedir ao Leonardo ou propor com sinalização (a convenção `T-FV-006/2026` foi usada ad hoc no piloto).
- **Nunca preencher data de aceite nem assinatura**: são do cliente e da obra. A garantia **não** depende da assinatura: conta da emissão da NF, que sai no embarque (decisão de 03/10).
- O modelo atual é de **rotuladora** (teste de aplicação de rótulo, troca de bobina). Para outro equipamento (ex.: esteira), os itens precisam ser adaptados e a adaptação revisada pelo Leonardo.

## Não faz
Não assina, não envia ao cliente, não altera os modelos-base, não mexe no gerador de propostas.

## Pendências de decisão (ver `docs/MAPA.md`)
1. ~~Início da garantia~~ **Decidido em 03/10:** 12 meses da emissão da NF (= embarque). Falta aplicar o texto novo no modelo de Manual (§1.2) e de Relatório (§7); textos exatos em `docs/DECISOES.md`.
2. Convenção do nº de série.
3. Modelo de Relatório para equipamentos que não são rotuladoras.
4. Onde o agente grava o arquivo final em `.docx` (ver limitação abaixo).

## Limitação técnica atual
Os modelos são `.docx` com timbrado, grandes (~85 KB cada). A ponte entre este ambiente e o Drive não transporta arquivos desse tamanho com segurança. Por ora o agente entrega o **conteúdo preenchido** (Google Doc sem timbrado, ou texto no chat) e o `.docx` final é montado a partir do modelo no Cowork/Word. A geração automática do `.docx` com timbrado entra na etapa 2 (container próprio, `docs/CONTAINER.md`).
