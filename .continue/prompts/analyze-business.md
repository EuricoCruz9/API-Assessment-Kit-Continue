---
name: Analyze Business
invokable: true
description: Traduz o comportamento de uma aplicação para uma visão funcional, explicando seu objetivo, processos, regras de negócio, dados e integrações em linguagem não técnica.
---

# Análise Funcional da Aplicação

Utilize `.continue/agents/business-analyst.md` como referência principal para esta análise.

Também considere, quando disponíveis:

- `.continue/rules/evidence-policy.md`
- `.continue/rules/evidence-chain.md`
- `.continue/rules/documentation-style.md`

---

# Objetivo

Descobrir e explicar **o que a aplicação faz**, qual é sua responsabilidade funcional e quais processos de negócio ela suporta.

A análise deve transformar o comportamento observado no código, configuração e documentação em uma explicação que possa ser entendida por:

- Product Managers;
- Product Owners;
- gestores;
- analistas de negócio;
- arquitetos;
- stakeholders;
- profissionais técnicos que não conhecem a aplicação.

A análise NÃO deve ser uma documentação técnica do código.

---

# Regra principal

## Investigue tecnicamente. Explique funcionalmente.

Você pode analisar profundamente:

- classes;
- métodos;
- queries;
- configurações;
- endpoints;
- integrações;
- componentes;
- dependências;
- banco de dados;
- mensagens;
- arquivos de configuração.

Porém, o resultado final deve abstrair esses detalhes sempre que possível.

Pergunte continuamente:

> "O que este detalhe técnico significa do ponto de vista funcional?"

Se um detalhe técnico não acrescentar entendimento sobre o funcionamento da aplicação, não o apresente no relatório.

---

# Exemplo obrigatório de nível de abstração

Se a investigação encontrar algo equivalente a:

```text
Controller
    ↓
Service
    ↓
Validator
    ↓
Repository
    ↓
DataSource
    ↓
SQL Server
    ↓
CERTIFICATE