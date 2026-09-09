# PROMPT — Discover API

## Objetivo

Realizar a descoberta inicial de uma API existente e determinar quais informações e arquivos precisam ser analisados para construir um mapa arquitetural confiável.

Esta etapa é de descoberta.

Não realizar ainda um assessment completo de performance, segurança, escalabilidade ou product readiness.

---

## Especialista

Utilize as responsabilidades e limitações definidas para o **API Architect**.

Respeite integralmente todas as regras do projeto, especialmente a Política de Evidências.

---

## Contexto inicial

Utilize o contexto disponível do repositório:

@repository-map

Antes de iniciar, determine exatamente quais informações estão disponíveis no contexto.

Não presuma que o repository map contém o conteúdo dos arquivos.

O repository map deve ser utilizado principalmente para:

* compreender a estrutura do projeto;
* localizar arquivos potencialmente relevantes;
* identificar módulos;
* identificar packages;
* planejar quais arquivos devem ser analisados.

A existência de um arquivo ou diretório não comprova seu comportamento.

---

# Etapa 1 — Identificar o projeto

A partir das evidências disponíveis, tente identificar:

* linguagem;
* framework;
* sistema de build;
* módulos;
* estrutura principal;
* arquivos de configuração;
* documentação existente.

Classifique cada conclusão segundo a Política de Evidências.

Se apenas o nome de um arquivo indicar determinada tecnologia, trate isso adequadamente como evidência limitada.

---

# Etapa 2 — Mapear a estrutura

Identifique arquivos ou diretórios potencialmente relacionados a:

* controllers;
* endpoints;
* services;
* use cases;
* domain;
* repositories;
* persistence;
* clients;
* gateways;
* adapters;
* producers;
* consumers;
* schedulers;
* configuration;
* security;
* observability;
* documentação;
* testes.

Não assumir comportamento interno com base apenas nos nomes.

---

# Etapa 3 — Identificar pontos de entrada

Procure evidências estruturais de possíveis pontos de entrada da aplicação, como:

* controllers;
* handlers;
* consumers;
* listeners;
* schedulers;
* jobs.

Neste estágio, identifique-os como candidatos à análise.

Não documente seu comportamento sem analisar seu conteúdo.

---

# Etapa 4 — Selecionar contexto adicional

Determine quais arquivos precisam ser analisados para compreender a API.

Não solicite todo o repositório indiscriminadamente.

Priorize arquivos que forneçam maior quantidade de informação arquitetural.

Classifique-os como:

## PRIORIDADE ALTA

Necessários para compreender os principais fluxos e contratos.

## PRIORIDADE MÉDIA

Necessários para aprofundar partes específicas.

## PRIORIDADE BAIXA

Úteis posteriormente, mas não necessários para iniciar o assessment.

---

# Etapa 5 — Justificar cada solicitação

Para cada arquivo solicitado, informe:

**Arquivo:** caminho ou nome identificado.

**Prioridade:** Alta | Média | Baixa.

**Motivo:** por que esse arquivo é necessário.

**O que pretende validar:** qual hipótese ou informação poderá ser confirmada.

Exemplo:

**Arquivo:** `ClaimController.java`

**Prioridade:** Alta

**Motivo:** possível ponto de entrada HTTP identificado no repository map.

**O que pretende validar:** endpoints expostos, contratos HTTP e serviços chamados.

---

# Etapa 6 — Identificar contexto externo necessário

Determine se existem informações importantes que provavelmente não podem ser obtidas apenas pelo código.

Exemplos:

* arquitetura de infraestrutura;
* API Gateway;
* balanceador;
* quantidade de instâncias;
* autoscaling;
* métricas de produção;
* SLA;
* volumes;
* dependências gerenciadas externamente.

Não peça essas informações apenas porque poderiam ser interessantes.

Solicite-as somente quando forem necessárias para alguma etapa posterior do assessment.

---

# Etapa 7 — Perguntas ao usuário

Faça perguntas apenas quando:

1. houver ambiguidade relevante;
2. não for possível escolher quais arquivos analisar;
3. uma informação ausente mudar significativamente o caminho da análise.

Caso contrário, registre a informação como pendente e continue.

Agrupe as perguntas.

---

# Saída esperada

Produza:

## 1. Contexto disponível

Descreva brevemente o que foi efetivamente analisado.

## 2. Características iniciais identificadas

| Característica | Evidência | Status |
| -------------- | --------- | ------ |

Status permitidos:

* CONFIRMADO
* INFERIDO
* HIPÓTESE
* SEM EVIDÊNCIA SUFICIENTE

## 3. Estrutura relevante encontrada

Apresente os principais diretórios, módulos ou arquivos candidatos à análise.

## 4. Contexto necessário — Prioridade Alta

Liste os arquivos necessários para iniciar a análise arquitetural.

## 5. Contexto necessário — Prioridade Média

Liste apenas quando aplicável.

## 6. Contexto necessário — Prioridade Baixa

Liste apenas quando aplicável.

## 7. Informações externas potencialmente necessárias

Liste informações que poderão precisar ser fornecidas pelo usuário posteriormente.

Não trate essas informações como inexistentes.

## 8. Perguntas

Faça somente perguntas necessárias para prosseguir.

## 9. Próxima ação

Informe objetivamente qual contexto deve ser fornecido na próxima interação.

---

# Restrições

Nesta etapa:

NÃO:

* avaliar se a API é escalável;
* declarar gargalos de performance;
* declarar vulnerabilidades;
* avaliar product readiness;
* recomendar refatorações;
* alterar código;
* criar componentes inexistentes;
* completar fluxos por suposição;
* assumir infraestrutura externa;
* assumir comportamento com base apenas no nome de arquivos.

O objetivo é descobrir **o que existe e o que precisa ser investigado**.

---

# Verificação final

Antes de responder, verifique:

1. Fiz alguma afirmação sobre código que não analisei?
2. Transformei nome de arquivo em comportamento?
3. Presumi alguma infraestrutura?
4. Solicitei arquivos sem explicar por quê?
5. Solicitei mais contexto do que realmente preciso?
6. Transformei ausência de evidência em ausência de funcionalidade?

Se sim, corrija a resposta antes de apresentá-la.

# Persistência da descoberta

O resultado desta análise deve ser persistido em:

`docs/assessment/01-discovery.md`

Este documento representa o estado atual da descoberta da API e será utilizado como contexto por análises posteriores.

## Criação

Se o arquivo ainda não existir, crie-o.

Se o ambiente atual não permitir criação de arquivos, gere no chat o conteúdo Markdown completo destinado ao arquivo e informe explicitamente ao usuário que ele deve ser salvo como:

`docs/assessment/01-discovery.md`

## Atualização

Se `docs/assessment/01-discovery.md` já existir:

1. leia o conteúdo existente;
2. preserve informações ainda válidas;
3. incorpore somente novas informações suportadas pelas evidências analisadas;
4. corrija informações anteriores quando uma evidência primária demonstrar que estavam incorretas;
5. registre conflitos que não possam ser resolvidos;
6. não duplique informações.

Não remova informações pendentes apenas porque não foram encontradas na análise atual.

## Estrutura obrigatória

O documento deve utilizar:

# API Discovery

## Status

Utilize:

* EM DESCOBERTA
* DESCOBERTA CONCLUÍDA

Utilize `EM DESCOBERTA` enquanto ainda faltarem informações relevantes para compreender os principais componentes e fluxos da API.

---

## Contexto analisado

Liste somente o contexto efetivamente analisado.

Exemplo:

* repository map;
* `pom.xml`;
* `application.yml`;
* `ClaimController.java`.

Não liste arquivos cujo conteúdo não tenha sido analisado como se tivessem sido.

---

## Stack identificada

Registre tecnologias identificadas e a evidência correspondente.

---

## Estrutura da aplicação

Registre módulos, packages e componentes relevantes encontrados.

---

## Endpoints identificados

Registre apenas endpoints confirmados por evidência suficiente.

---

## Dependências externas identificadas

Registre integrações encontradas.

Não inferir infraestrutura externa.

---

## Persistência identificada

Registre mecanismos de persistência efetivamente identificados.

---

## Configurações relevantes

Registre configurações relevantes encontradas durante a descoberta.

Não registrar segredos, tokens, senhas, certificados privados ou valores sensíveis no documento.

---

## Principais fluxos identificados

Documente somente fluxos que possam ser sustentados pelas evidências analisadas.

---

## Hipóteses e inferências

Registre separadamente qualquer informação classificada como INFERIDO ou HIPÓTESE.

Nunca misture essas informações com fatos confirmados.

---

## Informações não disponíveis

Liste informações relevantes que não puderam ser determinadas.

---

## Contexto adicional necessário

Liste arquivos ou informações adicionais necessários para continuar a descoberta.

Para cada item, explique o motivo.

---

## Perguntas para o usuário

Registre perguntas cuja resposta seja necessária para resolver ambiguidades relevantes.

---

## Próximos passos

Informe objetivamente qual deve ser a próxima ação do assessment.

# Regra de portabilidade de contexto

O documento deve ser compreensível por outro agente ou por uma nova sessão de chat sem depender do histórico da conversa atual.

Não utilize referências como:

* "conforme discutido anteriormente";
* "como você informou acima";
* "como vimos no chat";
* "no arquivo que você acabou de enviar".

Registre o contexto necessário explicitamente no documento.

Ao mesmo tempo, não copie grandes trechos de código para o documento.

Prefira registrar a localização da evidência:

**Evidência:** `src/.../ClaimController.java` — método `createClaim()`.

# Finalização

Ao terminar a execução:

1. atualize `docs/assessment/01-discovery.md`;
2. informe ao usuário se o status permanece `EM DESCOBERTA` ou passou para `DESCOBERTA CONCLUÍDA`;
3. se permanecer em descoberta, informe qual contexto deve ser fornecido na próxima interação;
4. não inicie automaticamente outra etapa do assessment.
