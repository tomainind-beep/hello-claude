# Terminais para os funcionários

Objetivo: outras pessoas lançarem dados sem depender do Leonardo.

## Princípios
- Cada pessoa tem **login individual** e um **papel** (Comercial, Assistência, Jurídico, Marketing, Financeiro, Admin). O papel define o que vê e o que pode lançar.
- Funcionário **lança dados e faz pedidos**; não fala com agente com poder de execução. O pedido entra numa fila e o agente responsável processa, com aprovação do Leonardo enquanto estivermos no modo sob pedido.
- Todo lançamento registra quem, quando e de onde (auditoria).

## Caminho em duas etapas
1. **Curto prazo, sem código novo:** formulários e interfaces do Airtable por papel (a Taynara já usa um formulário). Cada área ganha um formulário e uma visão só do que lhe cabe.
2. **Depois:** um pequeno app web no container da central, com login, um formulário por papel e um chat com o agente da área, gravando nas mesmas tabelas.

## Dados sensíveis
Financeiro e jurídico ficam fora dos terminais gerais. Acesso a esses papéis só para quem o Leonardo indicar.
