# RULE — Cadeia de Evidências

## Objetivo

Permitir que diferentes etapas do assessment compartilhem conhecimento sem depender do histórico completo do chat.

Os documentos localizados em `docs/assessment/` representam resultados persistidos de análises anteriores.

---

## Tipos de evidência

### Evidência primária

Possui maior nível de confiabilidade.

Inclui:

* código-fonte;
* arquivos de configuração;
* manifests;
* contratos da API;
* documentação oficial existente no projeto;
* informações fornecidas explicitamente pelo usuário.

### Evidência derivada

Informações registradas nos documentos produzidos durante o assessment.

Exemplos:

* `01-discovery.md`;
* `02-architecture.md`;
* `03-scalability.md`;
* demais documentos em `docs/assessment/`.

---

## Uso de análises anteriores

Documentos anteriores podem ser utilizados para:

* fornecer contexto;
* evitar repetição de descoberta;
* localizar componentes relevantes;
* identificar pontos que precisam ser investigados;
* transferir conhecimento entre diferentes etapas do assessment.

Entretanto, uma conclusão registrada em relatório anterior não deve ser automaticamente tratada como nova evidência primária.

Quando uma conclusão relevante depender de código ou configuração, consultar a evidência primária indicada no relatório sempre que ela estiver disponível no contexto.

---

## Rastreabilidade

Todo achado deve, sempre que possível, registrar sua origem.

Exemplo:

**Status:** CONFIRMADO

**Evidência primária:**
`src/.../ClaimClient.java`

**Identificado durante:**
Discovery

**Observação:**
Existe um client responsável por realizar chamadas HTTP externas.

---

## Ausência da evidência primária

Caso um relatório anterior cite uma evidência primária que não esteja disponível no contexto atual:

1. não inventar seu conteúdo;
2. não expandir conclusões além do que está registrado;
3. indicar que a evidência original não foi revalidada;
4. solicitar o arquivo original caso ele seja necessário para uma nova conclusão.

---

## Conflitos

Se uma análise atual encontrar evidência que contradiga um documento anterior:

não tente reconciliar as informações por suposição.

Registre:

**CONFLITO DE EVIDÊNCIA**

Informe:

* conclusão anterior;
* nova evidência;
* arquivo de origem;
* impacto do conflito.

Solicite validação do usuário quando necessário.

---

## Regra de precedência

Quando houver conflito, evidência primária analisada diretamente possui precedência sobre evidência derivada.

Nenhum relatório anterior deve substituir o código como fonte de verdade.

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
