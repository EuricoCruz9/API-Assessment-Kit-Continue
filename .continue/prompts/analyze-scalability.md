# PROMPT — Analyze Scalability

## Objetivo

Avaliar riscos, limitações e evidências relacionadas à performance e escalabilidade da API.

Utilize as responsabilidades do **Performance Engineer** e todas as regras definidas no projeto.

---

# Contexto inicial

Utilize como ponto de partida:

`docs/assessment/01-discovery.md`

Se outros documentos anteriores do assessment estiverem disponíveis, utilize-os apenas quando forem relevantes.

Documentos anteriores são evidência derivada.

Sempre que uma conclusão importante depender de comportamento específico do código, consulte a evidência primária correspondente quando ela estiver disponível.

---

# Etapa 1 — Ler o discovery

Identifique:

* stack;
* endpoints;
* fluxos;
* bancos;
* integrações;
* processamento assíncrono;
* componentes relevantes;
* arquivos citados como evidência.

Crie mentalmente uma lista dos pontos que merecem investigação de performance.

Não produza conclusões ainda.

---

# Etapa 2 — Determinar contexto necessário

Antes de solicitar arquivos adicionais, utilize todo contexto já disponível.

Quando necessário, solicite somente arquivos que possam confirmar ou rejeitar hipóteses relevantes.

Priorize:

1. services associados aos principais fluxos;
2. repositories;
3. clients externos;
4. configurações de conexão;
5. consumers/producers;
6. configurações de threads ou pools;
7. código relacionado a processamento de arquivos ou grandes payloads.

Não solicite todo o repositório indiscriminadamente.

---

# Etapa 3 — Analisar escalabilidade

Avalie:

## Processamento

* síncrono;
* assíncrono;
* sequencial;
* paralelo;
* operações potencialmente demoradas.

## Persistência

* consultas;
* paginação;
* operações repetidas;
* transações;
* volume potencial de retorno.

## Dependências externas

* número de chamadas;
* sequência das chamadas;
* timeout;
* retry;
* tratamento de erro.

## Estado

* estado local;
* sessão;
* cache;
* armazenamento temporário.

## Concorrência

* locks;
* pools;
* threads;
* processamento compartilhado.

## Escalabilidade horizontal

Investigue impedimentos observáveis para múltiplas instâncias.

---

# Etapa 4 — Diferenciar três conceitos

Não misture:

## Escalabilidade arquitetural

Capacidade estrutural de crescer.

## Performance atual

Comportamento observado em produção.

## Capacidade máxima

Limite real da aplicação.

Código pode fornecer evidências sobre escalabilidade arquitetural.

Performance atual e capacidade máxima normalmente exigem métricas ou testes.

Nunca afirmar performance atual ou capacidade máxima apenas pelo código.

---

# Etapa 5 — Gerar findings

Utilize o padrão:

`PERF-001`, `PERF-002`, `PERF-003`...

Para cada finding registre:

* status;
* impacto potencial;
* confiança;
* evidência;
* observação;
* risco;
* cenário;
* informação necessária;
* recomendação;
* esforço.

---

# Etapa 6 — Identificar informações necessárias de produção

Ao final, registre separadamente informações necessárias para confirmar capacidade real.

Exemplos:

* RPS;
* P95;
* P99;
* taxa de erro;
* CPU;
* memória;
* número de réplicas;
* política de autoscaling;
* conexão com banco;
* tempo médio de queries;
* volume de dados.

Não solicite métricas que não tenham relação com os riscos encontrados.

---

# Persistência do resultado

O resultado deve ser persistido em:

`docs/assessment/03-scalability.md`

Se o arquivo ainda não existir, crie-o.

Se o ambiente não permitir criar arquivos, gere o Markdown completo no chat.

Se o arquivo existir, atualize-o preservando findings ainda válidos.

---

# Estrutura do documento

# Scalability Assessment

## Status

Utilize:

* EM ANÁLISE
* ANÁLISE CONCLUÍDA
* AGUARDANDO EVIDÊNCIAS

---

## Contexto analisado

Liste os documentos e evidências primárias realmente utilizados.

---

## Resumo executivo

Explique brevemente:

* o que foi possível avaliar;
* principais riscos;
* principais limitações da análise.

Não declarar a API como "escalável" ou "não escalável" quando não houver evidência suficiente.

---

## Características favoráveis à escalabilidade

Registrar somente características observadas.

---

## Riscos identificados

Adicionar os findings `PERF-XXX`.

---

## Escalabilidade horizontal

Descrever o que foi possível determinar.

---

## Dependências externas

Descrever riscos relacionados a dependências.

---

## Persistência

Descrever os pontos relevantes encontrados.

---

## Processamento e concorrência

Registrar os achados correspondentes.

---

## Informações de produção necessárias

Liste métricas ou informações necessárias para validar hipóteses.

---

## Perguntas para o usuário

Agrupe somente perguntas relevantes.

---

## Conclusão

Classifique a avaliação como:

### SEM BLOQUEIOS ESTRUTURAIS EVIDENTES

Não foram encontrados bloqueios estruturais relevantes no escopo analisado.

Isso não significa capacidade comprovada.

### RISCOS DE ESCALABILIDADE IDENTIFICADOS

Foram encontradas evidências de riscos que precisam ser tratados ou validados.

### INFORMAÇÃO INSUFICIENTE

Não existe contexto suficiente para uma conclusão significativa.

Não utilizar simplesmente:

> A API é escalável.

sem informar claramente qual aspecto está sendo avaliado.

---

## Próximos passos

Recomendar ações de investigação, métricas ou análises adicionais.

---

# Regra final

Performance potencial não é performance comprovada.

Escalabilidade arquitetural não é capacidade comprovada.

Ausência de problema visível no código não comprova capacidade de produção.
