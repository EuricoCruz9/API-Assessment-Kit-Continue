# RULE — Escopo da Avaliação de APIs

## Objetivo

Toda análise deve considerar a API sob a perspectiva de engenharia de software, arquitetura e Technical Product Management.

O objetivo não é apenas identificar problemas técnicos, mas avaliar a capacidade da API de evoluir, escalar e atender novos consumidores.

---

## Dimensões obrigatórias da análise

Sempre que possível, avaliar:

### Arquitetura

* responsabilidades dos componentes;
* organização em camadas;
* dependências internas;
* dependências externas;
* acoplamento.

### Contrato da API

* endpoints;
* métodos HTTP;
* payloads;
* códigos de retorno;
* versionamento.

### Escalabilidade

* processamento síncrono;
* concorrência;
* estado compartilhado;
* cache;
* filas;
* persistência;
* integrações externas.

### Resiliência

* timeout;
* retry;
* circuit breaker;
* fallback;
* tratamento de erros.

### Observabilidade

* logs;
* métricas;
* tracing;
* correlation IDs;
* health checks.

### Segurança

* autenticação;
* autorização;
* validações;
* dados sensíveis;
* segredos.

### Camada de Dados

* queries;
* paginação;
* índices;
* transações;
* consistência.

### Reusabilidade

* regras específicas de cliente;
* configurações hardcoded;
* parametrização;
* multitenancy;
* extensibilidade.

### Produto de API

* onboarding de consumidores;
* documentação;
* compatibilidade;
* governança;
* possibilidade de reutilização.

---

## Classificação dos achados

Todo achado deve possuir:

* Severidade.
* Impacto técnico.
* Impacto de negócio.
* Evidência.
* Recomendação.
* Esforço estimado (Baixo, Médio, Alto).
