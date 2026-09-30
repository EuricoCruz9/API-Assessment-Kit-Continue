---

# `.continue/prompts/analyze-business.md`

```markdown
---
name: Analyze Business
invokable: true
description: Traduz o comportamento de uma aplicação para uma visão funcional e de negócio, identificando objetivos, fluxos, regras e conceitos observáveis.
---

# Análise Funcional e de Negócio da Aplicação

Utilize `.continue/agents/business-analyst.md` como referência principal para esta análise.

Também considere, quando disponíveis:

- `.continue/rules/evidence-policy.md`
- `.continue/rules/evidence-chain.md`
- `.continue/rules/documentation-style.md`

Esses arquivos devem ser tratados como instruções complementares para evidência, rastreabilidade e documentação.

## Objetivo

Produzir uma visão funcional da aplicação que possa ser compreendida por uma pessoa com pouco ou nenhum conhecimento técnico.

A pergunta central é:

> O que esta aplicação faz e quais comportamentos de negócio podem ser observados a partir dos artefatos disponíveis?

O foco deve estar no **objetivo e no comportamento da aplicação**, e não na tecnologia utilizada para implementá-la.

---

# Regras fundamentais

1. Não invente regras de negócio.
2. Não assuma o significado de entidades apenas pelo nome.
3. Não transforme hipóteses em fatos.
4. Diferencie CONFIRMADO, INFERIDO, HIPÓTESE e SEM EVIDÊNCIA SUFICIENTE.
5. Toda afirmação relevante deve possuir evidência rastreável.
6. Quando o código não permitir determinar o significado de negócio, declare a limitação.
7. Não altere código.
8. Não execute análises de arquitetura, performance, segurança, resiliência ou observabilidade.
9. Não dependa de relatórios anteriores para conseguir executar a análise.
10. Relatórios anteriores podem ser utilizados como contexto complementar, quando existirem.

---

# Processo

## 1. Entender a aplicação

Investigue os artefatos disponíveis e procure determinar:

- objetivo aparente da aplicação;
- principais capacidades funcionais;
- principais conceitos de negócio;
- entradas;
- saídas;
- atores e sistemas participantes.

Comece pela visão funcional e utilize os detalhes técnicos como evidência.

---

## 2. Mapear os principais fluxos

Identifique os fluxos funcionais observáveis.

Para cada fluxo, explique:

- objetivo;
- início;
- participante que inicia;
- informações recebidas;
- principais decisões;
- validações;
- processamento;
- integrações;
- resultado;
- condições de encerramento ou falha.

Descreva cada fluxo primeiro em linguagem funcional.

---

## 3. Identificar regras de negócio

Procure regras implementadas ou documentadas.

Para cada regra identificada:

- descreva a regra em linguagem simples;
- indique sua evidência;
- classifique seu nível de certeza.

Não atribua significado de negócio a uma condição técnica quando esse significado não estiver comprovado.

---

## 4. Identificar conceitos e estados

Mapeie conceitos relevantes e, quando aplicável:

- estados;
- transições;
- condições de mudança;
- operações permitidas em cada estado.

Utilize os nomes reais encontrados na aplicação quando o significado não estiver claro.

---

## 5. Traduzir para linguagem não técnica

Revise toda a descrição procurando substituir explicações excessivamente técnicas por explicações funcionais.

Por exemplo:

Evitar:

> O controller recebe uma requisição HTTP e chama o service.

Preferir:

> O sistema recebe uma solicitação e inicia o processamento correspondente.

A informação técnica pode permanecer na evidência.

---

# Relatório

Crie:

`docs/assessment/05-business-understanding.md`

O relatório deve conter:

## 1. Resumo executivo

Explique em linguagem simples:

- o que a aplicação faz;
- qual objetivo funcional foi identificado;
- quais são suas principais capacidades.

Se o objetivo não puder ser determinado com segurança, deixe isso explícito.

---

## 2. O que a aplicação faz

Descreva as principais capacidades funcionais observadas.

---

## 3. Principais fluxos

Para cada fluxo:

### Nome do fluxo

**Objetivo**

**Como começa**

**Passos principais**

**Decisões e regras**

**Resultado**

**Participantes**

**Nível de evidência**

---

## 4. Regras de negócio identificadas

Tabela:

| Regra | Descrição funcional | Evidência | Classificação |
|---|---|---|---|

---

## 5. Conceitos de negócio

| Conceito | Significado observado | Evidência | Classificação |
|---|---|---|---|

---

## 6. Estados e transições

Quando aplicável:

```text
Estado A
   ↓ condição
Estado B
   ↓ condição
Estado C