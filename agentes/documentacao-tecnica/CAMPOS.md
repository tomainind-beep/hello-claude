# Mapa de campos — Documentação Técnica

Origem: **Prop** = proposta/Airtable · **Ficha** = Ficha de Dados do Equipamento · **Eng** = engenheiro responsável · **Obra** = técnico na instalação · **Leo** = decisão do Leonardo · **Fixo** = texto do modelo, não muda.

## Manual de Operação e Manutenção
| Campo | Origem | Observação |
|---|---|---|
| Nome do equipamento, modelo | Ficha | |
| Cliente, nº do negócio | Prop | Código do manual = `<proposta>-MOM` |
| Revisão / data | Sistema | Mudou depois de entregue = nova revisão |
| Nº de série, ano de fabricação | Ficha | Convenção do série em aberto |
| Mês/ano de expedição (garantia §1) | Prop/Leo | Ver contradição de garantia |
| Período de garantia | Prop | Padrão 12 meses; **confirmar com a proposta** |
| Dados técnicos §2 (capacidade, VAC, Hz, kW, bar, L/min, C×L×A, kg, dB, acabamento) | Ficha | Sem dado = pendente |
| Uso previsto e proibido §3.1 | Ficha | |
| Botões de emergência, seccionadoras, válvula pneumática §3.3 | Ficha (seção 5) | |
| Espaço livre mínimo, rede de ar §3.4 | Ficha | Padrão do modelo: 800 mm; confirmar |
| Processo e operação §4.1–4.2 | Ficha + projeto | Passos reais dependem da máquina |
| Telas da IHM §4.3 | Projeto | Remover seção se não houver IHM |
| Módulos §4.4 | Ficha (seção 4) | Um bloco por módulo |
| Plano de manutenção, itens específicos §5.2–5.3 | Ficha (seção 6) | Padrão mínimo Tomain + específicos |
| Contato de assistência (telefone, e-mail, horário) §6 | Leo | Valores do modelo são exemplo |
| Responsável Tomain e do cliente §7 | Obra | |
| Normas, avisos, limitações de garantia, limpeza | Fixo | Não alterar |

## Laudo NR-12 (APR)
| Campo | Origem | Observação |
|---|---|---|
| Equipamento, cliente, CNPJ, endereço, nº do negócio | Prop/Ficha | Código `<proposta>-APR` |
| Responsável técnico, CREA, ART, atribuições | **Eng** | **Nunca o agente** |
| Solicitante (nome/função), IE | Prop | |
| Referências normativas §1.2 | Eng | O modelo traz a lista-base; manter só as aplicáveis |
| Limites da máquina §2.1 | Ficha | |
| Tabela HRN e faixas §3.1 | Eng | Ajustar à tabela adotada |
| Checklist §4.1 (OK/NOK/N.A.) | **Eng** | Exige inspeção real |
| Avaliação por módulo §4.2 (foto, perigos, HRN, categoria/PLr, residual, ação) | **Eng** | Agente só sugere perigos candidatos |
| Conclusão §5 (atende / com ressalvas / não atende) | **Eng** | **Nunca o agente** |
| Local, data, assinatura | **Eng** | |

## Relatório de Instalação, Start-up e Treinamento
| Campo | Origem | Observação |
|---|---|---|
| Equipamento, série, nº do negócio, cliente, CNPJ | Prop/Ficha | |
| Local da instalação | **Confirmar** | Pode divergir do CNPJ da proposta |
| Datas, técnicos Tomain | Obra | |
| Responsável do cliente | Obra | Perguntar se fica em branco |
| Checklists das seções 2, 3 e 5 (OK / N.A.) | Obra | Agente não marca |
| Tolerância e capacidade-padrão (§3) | Ficha | Pendente se não houver |
| Receitas/formatos configurados | Obra | Perguntar |
| Treinamento (data, duração, instrutor, participantes) | Obra | Perguntar |
| Pendências (§6) | Obra | "Sem pendências" só se o técnico confirmar |
| Termo de aceite (§7): cidade, data, assinaturas | Cliente/Obra | **Agente nunca preenche**; assinatura dispara a garantia |

## Itens do modelo de Relatório específicos de rotuladora (adaptar para outros equipamentos)
Teste com produto: aplicação de rótulo · aferição de precisão de aplicação · teste dos sensores de produto/rótulo e anti-falha · conteúdo do treinamento: troca de bobina e setup de rótulo, ajuste de formatos.
