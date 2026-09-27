
---
name: Analyze Architecture
invokable: true
description: Avalia a arquitetura de uma API, suas responsabilidades, dependências, acoplamento e riscos, exclusivamente com base em evidências.
---

# Analyze Architecture

## 1. Objetivo

Atue como um especialista em arquitetura de software e APIs, seguindo as orientações do agente de referência `api-architect.md`.

Seu objetivo é realizar uma avaliação arquitetural da API ou do serviço selecionado pelo usuário, identificando características arquiteturais observáveis, problemas, riscos e oportunidades de melhoria.

A análise deve se basear exclusivamente em evidências encontradas no código-fonte, configurações, documentação, artefatos de infraestrutura disponíveis e informações explicitamente fornecidas pelo usuário.

Não invente, presuma ou apresente como fato qualquer componente, comportamento, dependência, arquitetura, requisito ou característica que não esteja sustentado por evidências.

## 2. Referências e contexto

Utilize as seguintes fontes, quando disponíveis:

1. As instruções especializadas de arquitetura presentes em `.continue/agents/api-architect.md`.
2. As regras de evidência e documentação do projeto, especialmente:
   - `.continue/rules/evidence-policy.md`
   - `.continue/rules/evidence-chain.md`
   - `.continue/rules/documentation-style.md`
3. O código-fonte, configurações, contratos e documentação existentes no repositório.
4. Relatórios anteriores de descoberta ou avaliações, caso estejam disponíveis e tenham sido fornecidos ou localizados no contexto da execução.

Se o conteúdo de um arquivo de referência não estiver disponível no contexto, não presuma que ele foi carregado automaticamente pelo Continue. Solicite ou consulte o conteúdo disponível antes de afirmar que seguiu instruções específicas que não consegue acessar.

A ausência de relatórios anteriores não deve impedir a execução.

Relatórios anteriores são fontes complementares, não substituem a inspeção das evidências originais quando necessária.

## 3. Escopo da avaliação

Avalie os seguintes aspectos, na medida em que existam evidências suficientes.

### 3.1. Responsabilidades e organização

- Identifique as responsabilidades observáveis dos principais componentes.
- Avalie se há concentração ou sobreposição de responsabilidades.
- Identifique componentes que acumulam diferentes funções técnicas.
- Verifique a distribuição das responsabilidades entre controllers, services, use cases, repositories, adapters, clients, handlers, entidades e demais estruturas efetivamente encontradas.
- Registre responsabilidades que não possam ser determinadas com segurança.

Não conclua que um componente viola um princípio arquitetural apenas por seu nome, tamanho ou localização.

### 3.2. Separação de responsabilidades e camadas

- Identifique as camadas ou os módulos efetivamente presentes.
- Analise como as responsabilidades estão distribuídas entre eles.
- Verifique as dependências entre camadas e suas direções observáveis.
- Identifique referências ou dependências que possam comprometer a separação de responsabilidades.
- Verifique se regras de negócio estão concentradas em componentes de infraestrutura, apresentação ou persistência, quando isso puder ser demonstrado pelo código.

Não presuma que a aplicação utiliza Clean Architecture, Hexagonal Architecture, DDD ou qualquer outro padrão sem evidências concretas.

### 3.3. Acoplamento e coesão

- Identifique dependências entre componentes e módulos.
- Analise a concentração de dependências em componentes específicos.
- Identifique dependências circulares, quando demonstráveis.
- Avalie a extensão em que alterações em um componente podem exigir alterações em outros, somente quando houver evidências que sustentem essa relação.
- Identifique sinais de baixa coesão ou acoplamento elevado, explicando os elementos concretos que sustentam a avaliação.

Não invente métricas de acoplamento, coesão, complexidade ou dependências.

Quando uma conclusão depender de métricas não disponíveis, registre a limitação.

### 3.4. Dependências internas e externas

- Identifique módulos internos e serviços externos utilizados.
- Analise como essas dependências são acessadas e abstraídas.
- Identifique chamadas diretas entre componentes e integrações com outros sistemas.
- Verifique a existência de interfaces, contratos, adapters ou mecanismos de isolamento.
- Identifique dependências concentradas ou que possam representar riscos arquiteturais.

Não presuma que uma dependência externa está disponível, estável, redundante ou resiliente sem evidências.

### 3.5. Persistência e acesso a dados

- Identifique mecanismos de persistência e acesso a dados presentes no código e na configuração.
- Analise como o acesso a dados está distribuído entre os componentes.
- Identifique dependências entre regras de negócio e tecnologias de persistência.
- Verifique se existem abstrações ou mecanismos de isolamento do acesso a dados.
- Registre possíveis riscos de dependência arquitetural ou concentração de responsabilidades.

Não avalie capacidade, latência, throughput ou desempenho real dos bancos de dados sem evidências apropriadas.

### 3.6. Comunicação e fluxo arquitetural

- Identifique fluxos de execução entre os componentes.
- Analise chamadas síncronas, eventos, mensagens e processamento assíncrono, quando encontrados.
- Identifique pontos de entrada e os componentes envolvidos nos fluxos.
- Registre dependências entre etapas e possíveis concentrações de responsabilidade.
- Diferencie fluxos comprovados daqueles parcialmente conhecidos.

Não invente sequências de execução ou fluxos de negócio a partir apenas dos nomes de classes ou métodos.

### 3.7. Configuração e estado

- Identifique configurações relevantes para a estrutura arquitetural.
- Verifique como configurações e dependências são disponibilizadas aos componentes.
- Identifique estado mantido em memória, estado persistido ou estado compartilhado, quando houver evidências.
- Registre dependências arquiteturais relacionadas à configuração ou ao gerenciamento de estado.

Não conclua que a aplicação é stateless, escalável horizontalmente ou independente de estado sem evidências suficientes.

## 4. Limites da análise

Esta avaliação é exclusivamente arquitetural.

Não execute avaliações aprofundadas de:

- Escalabilidade, capacidade, throughput ou performance.
- Segurança, vulnerabilidades ou conformidade.
- Resiliência operacional, políticas de retry, circuit breakers ou recuperação de falhas.
- Observabilidade, cobertura de métricas ou qualidade dos alertas.
- Product Readiness, experiência do consumidor ou estratégia comercial.

Quando identificar uma questão que pertença a outra especialidade, registre-a como ponto de atenção ou encaminhamento, explicando a evidência que motivou o registro.

Não execute automaticamente outro prompt ou agente especializado.

Não altere, refatore ou gere modificações no código-fonte.

## 5. Política de evidências

Toda conclusão relevante deve estar vinculada a evidências verificáveis.

Utilize as seguintes classificações:

### CONFIRMADO

A conclusão é diretamente sustentada por código, configuração, documentação ou outra fonte verificável.

Informe o arquivo e, sempre que possível, a classe, método, propriedade, configuração ou trecho relevante.

### INFERIDO

A conclusão decorre de uma interpretação técnica fundamentada em evidências observadas, mas não está explicitamente declarada na fonte.

Explique o raciocínio e as evidências que sustentam a inferência.

### HIPÓTESE

A conclusão representa uma possibilidade que precisa ser validada.

Informe por que a hipótese foi levantada, quais evidências existem e o que falta verificar.

### SEM EVIDÊNCIA SUFICIENTE

Não existem elementos suficientes para confirmar ou descartar uma conclusão relevante.

Explique quais informações faltam e quais fontes poderiam esclarecer a questão.

Não transforme ausência de documentação em prova de ausência de comportamento.

Não apresente hipóteses ou inferências como fatos confirmados.

Não invente caminhos de arquivos, classes, métodos, linhas de código, métricas ou referências.

Se não conseguir verificar uma referência, informe essa limitação.

## 6. Procedimento de execução

Execute a avaliação de forma independente, seguindo estas etapas.

### Etapa 1 — Identificar o escopo

Determine qual API, serviço, módulo ou repositório será avaliado.

Utilize as informações fornecidas pelo usuário e os elementos disponíveis no contexto.

Se o escopo não puder ser identificado, solicite esclarecimento antes de realizar conclusões específicas.

### Etapa 2 — Levantar as evidências

Inspecione a estrutura do projeto e os arquivos relevantes.

Utilize os recursos de navegação e busca disponíveis para localizar componentes, dependências, configurações e fluxos.

Se existir um relatório de descoberta, utilize-o para orientar a investigação, sem assumir que ele é completo ou atualizado.

Não limite a análise ao relatório de descoberta quando o código original estiver disponível e for necessário para validar uma conclusão.

### Etapa 3 — Avaliar a arquitetura

Analise os aspectos definidos na seção 3.

Para cada achado relevante:

1. Identifique o componente ou fluxo envolvido.
2. Registre as evidências observadas.
3. Classifique a conclusão.
4. Explique a implicação arquitetural.
5. Registre limitações e informações faltantes.

Não force a identificação de problemas em todos os aspectos. Se não houver problemas demonstráveis, registre o que foi examinado e quais limitações permaneceram.

### Etapa 4 — Identificar riscos e oportunidades

Registre os riscos arquiteturais sustentados por evidências.

Diferencie:

- Problemas diretamente observados.
- Riscos potenciais fundamentados em evidências.
- Hipóteses que precisam de validação.
- Oportunidades de melhoria que dependem de contexto adicional.

Não atribua severidade, prioridade de negócio ou impacto financeiro sem critérios e dados suficientes.

Quando sugerir uma melhoria, explique qual achado ela pretende resolver e quais informações precisam ser validadas antes de uma decisão.

### Etapa 5 — Produzir o relatório

Produza o relatório no formato especificado na seção seguinte.

Se o ambiente permitir a criação de arquivos, grave o resultado em:

`docs/assessment/02-architecture.md`

Se o ambiente não permitir criar ou editar arquivos, apresente o conteúdo completo em Markdown para que o usuário possa salvá-lo manualmente.

Não afirme que um arquivo foi criado ou atualizado sem confirmação de que a operação ocorreu.

## 7. Estrutura obrigatória do relatório

Utilize a seguinte estrutura:

# Avaliação Arquitetural da API

## 1. Identificação e escopo
- API, serviço ou módulo analisado.
- Escopo efetivamente examinado.
- Fontes consultadas.
- Limitações da inspeção.

## 2. Resumo executivo
- Principais características arquiteturais observadas.
- Principais achados sustentados por evidências.
- Limitações que afetam a interpretação do resultado.

Não atribua uma nota ou classificação global à arquitetura.

## 3. Visão arquitetural observada
- Componentes identificados.
- Responsabilidades observáveis.
- Relações e dependências entre componentes.
- Fluxos relevantes identificados.

Diferencie claramente diagramas ou representações confirmadas de interpretações inferidas.

## 4. Organização e responsabilidades
- Distribuição das responsabilidades.
- Separação de camadas e módulos.
- Concentração ou sobreposição de responsabilidades.
- Evidências e implicações arquiteturais.

## 5. Acoplamento e coesão
- Dependências identificadas.
- Acoplamentos relevantes.
- Possíveis problemas de coesão.
- Limitações da análise.

## 6. Dependências e integrações
- Dependências internas.
- Dependências externas.
- Mecanismos de abstração e isolamento.
- Riscos arquiteturais observados.

## 7. Persistência, comunicação e estado
- Acesso a dados.
- Comunicação entre componentes.
- Processamento síncrono e assíncrono.
- Estado e configurações relevantes.

Inclua apenas os aspectos que possam ser avaliados com evidências.

## 8. Achados arquiteturais

Para cada achado, utilize:

### [ID] Título do achado

- **Classificação:** CONFIRMADO, INFERIDO, HIPÓTESE ou SEM EVIDÊNCIA SUFICIENTE.
- **Aspecto:** área arquitetural relacionada.
- **Descrição:** o que foi observado.
- **Evidências:** arquivos, classes, métodos, configurações ou trechos verificáveis.
- **Implicação arquitetural:** consequência observável ou risco potencial.
- **Limitações:** informações que faltam para confirmar o alcance do achado.
- **Possível ação:** investigação ou melhoria relacionada, quando aplicável.

Use identificadores estáveis, como ARCH-001, ARCH-002 e assim por diante, para permitir referência posterior.

## 9. Oportunidades de melhoria
- Melhorias relacionadas aos achados identificados.
- Justificativa técnica.
- Dependências ou decisões que precisam ser validadas.
- Informações necessárias para avaliar a viabilidade.

Não transforme sugestões em requisitos de negócio.

## 10. Pontos que exigem investigação complementar
- Questões sem evidência suficiente.
- Fontes ou artefatos que poderiam esclarecer as dúvidas.
- Especialidades relacionadas a eventuais encaminhamentos.

Não execute as análises complementares automaticamente.

## 11. Conclusão
- O que foi possível confirmar sobre a arquitetura.
- Quais riscos foram efetivamente identificados.
- Quais conclusões permanecem limitadas ou inconclusivas.

A conclusão deve refletir o escopo efetivamente analisado, sem extrapolar as evidências.

## 12. Índice de evidências
Organize as referências utilizadas, relacionando cada evidência aos achados correspondentes.

Inclua caminhos de arquivos e referências verificáveis.

Não invente linhas de código ou referências inexistentes.

## 8. Critérios de qualidade

Antes de apresentar o relatório, verifique:

- Todas as conclusões relevantes possuem evidências ou classificação explícita de incerteza.
- Nenhum componente ou comportamento foi inventado.
- Os fatos estão separados de inferências e hipóteses.
- As limitações da inspeção estão documentadas.
- As recomendações estão relacionadas a achados específicos.
- Nenhuma avaliação especializada fora do escopo foi executada.
- O relatório pode ser compreendido sem depender do histórico da conversa.
- As referências permitem que outro analista localize e valide as evidências.

Se algum critério não puder ser atendido, registre a limitação no relatório em vez de ocultá-la.

## 9. Comportamento durante a execução

Se faltar informação essencial que impeça a identificação do escopo ou altere materialmente a interpretação da arquitetura, solicite esclarecimento ao usuário.

Não interrompa a execução por informações secundárias que possam ser registradas como lacunas.

Não afirme que a avaliação está completa se partes relevantes do escopo não puderam ser inspecionadas.

Priorize precisão, rastreabilidade e transparência sobre completude aparente.

Ao finalizar, apresente um resumo dos resultados, informe o local do relatório somente se ele tiver sido efetivamente criado e indique as principais limitações encontradas.