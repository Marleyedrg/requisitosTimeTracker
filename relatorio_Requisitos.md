# Relatório de RQ-GAP — Análise de Requisitos

**Projeto:** TimeTracker

---

## Sumário

### Como preencher

1. [Objetivo](#1-objetivo)
2. [Fluxo da análise](#2-fluxo-da-análise)
3. [Como preencher um épico](#3-como-preencher-um-épico)
4. [Como registrar um GAP](#4-como-registrar-um-gap)

### Dados da análise

5. [Análise de requisitos](#5-análise-de-requisitos)
6. [GAPs identificados](#6-gaps-identificados)
7. [Conclusão](#7-conclusão)

---

# 1. Objetivo

Este documento registra a análise dos **épicos entregues pela equipe de desenvolvimento**.

No projeto TimeTracker, cada épico está diretamente relacionado ao seu respectivo Critério de Aceite:

```text id="ih0rgj"
EP-01 → CA-01
EP-02 → CA-02
EP-03 → CA-03
...
```

Quando a equipe de desenvolvimento informar que um épico foi implementado, ele deve ser adicionado à área de análise.

O Analista de Requisitos verifica o **Critério de Aceite correspondente**, executa os testes necessários, coleta evidências e registra o resultado.

O objetivo é responder:

> **O que foi entregue atende ao que foi especificado?**

---

# 2. Fluxo da análise

O processo é:

```text id="wn8pkq"
Desenvolvimento informa o épico
              ↓
     Adicionar à lista
              ↓
   Consultar o CA correspondente
              ↓
      Verificar implementação
              ↓
        Executar testes
              ↓
       Coletar evidências
              ↓
        Definir status
              ↓
    Registrar GAP, se houver
```

Exemplo:

```text id="s4ehbe"
Desenvolvimento informou:
"EP-02 foi implementado."

↓

Adicionar EP-02 à lista de análise.

↓

Consultar CA-02.

↓

Verificar o comportamento esperado.

↓

Executar os testes e coletar evidências.

↓

Definir o status.

↓

Registrar GAP, caso necessário.
```

---

# 3. Como preencher um épico

Cada épico entregue pela equipe de desenvolvimento recebe uma seção própria.

Exemplo:

```text id="wrybhq"
EP-02 — Detecção de inatividade
CA correspondente: CA-02
```

Para cada análise, registre:

* versão analisada;
* data da análise;
* responsável;
* situação da análise;
* comportamento esperado;
* status;
* evidência;
* GAP, caso exista.

## Situação da análise

Indica **em que etapa está o trabalho do analista**.

| Situação       | Significado                                              |
| -------------- | -------------------------------------------------------- |
| **Pendente**   | O épico foi registrado, mas a análise ainda não começou. |
| **Em análise** | A verificação está sendo realizada.                      |
| **Concluída**  | A análise foi finalizada e possui um resultado.          |

## Status

Indica **o resultado da verificação do Critério de Aceite**.

| Status              | Significado                                                   |
| ------------------- | ------------------------------------------------------------- |
| **Atendido**        | O comportamento foi testado e funciona conforme especificado. |
| **Parcial**         | Apenas parte do comportamento esperado funciona.              |
| **Ausente**         | O comportamento esperado não foi encontrado.                  |
| **Divergente**      | Existe implementação, mas funciona diferente do especificado. |
| **Não verificável** | Não há evidência suficiente para concluir.                    |

> **Importante:** encontrar a implementação no código não é suficiente para marcar o CA como **Atendido**. Deve existir evidência de que o comportamento esperado realmente funciona.

## Evidência

Registre **como o resultado foi comprovado**.

Pode ser:

* teste automatizado;
* execução manual;
* arquivo ou função;
* endpoint;
* log;
* registro no banco;
* screenshot;
* resposta da API.

---

# 4. Como registrar um GAP

Quando a análise identificar um problema ou uma questão que precise de acompanhamento, registre um `GAP-XX`.

Um GAP pode representar algo que precisa ser:

* corrigido;
* investigado;
* testado;
* esclarecido;
* decidido.

Exemplo:

```text id="odkcfb"
GAP-01 — Detecção de inatividade divergente
Relacionado a: EP-02 / CA-02
```

No bloco do épico, basta informar o identificador do GAP. Os detalhes ficam centralizados na seção [GAPs identificados](#6-gaps-identificados).

---

# 5. Análise de requisitos

Esta é a **principal área de trabalho do documento**.

Adicione os épicos conforme forem entregues pela equipe de desenvolvimento.

---

## EP-01 — [Nome do épico]

| Informação          | Valor                             |
| ------------------- | --------------------------------- |
| Versão analisada    | [branch / commit / versão]        |
| Data da análise     | [DD/MM/AAAA]                      |
| Responsável         | [Nome]                            |
| Situação da análise | Pendente / Em análise / Concluída |

**Comportamento esperado:**

[Resumo do comportamento esperado.]

**Status:** [Atendido / Parcial / Ausente / Divergente / Não verificável]

**Evidência:**

[Teste / execução / arquivo / log / screenshot / resposta da API.]

**GAP:** — / GAP-XX

---

## EP-02 — [Nome do épico]

| Informação          | Valor                             |
| ------------------- | --------------------------------- |
| Versão analisada    | [branch / commit / versão]        |
| Data da análise     | [DD/MM/AAAA]                      |
| Responsável         | [Nome]                            |
| Situação da análise | Pendente / Em análise / Concluída |

**Comportamento esperado:**

[Resumo do comportamento esperado.]

**Status:** [Atendido / Parcial / Ausente / Divergente / Não verificável]

**Evidência:**

[Teste / execução / arquivo / log / screenshot / resposta da API.]

**GAP:** — / GAP-XX

---

## EP-03 — [Nome do épico]

| Informação          | Valor                             |
| ------------------- | --------------------------------- |
| Versão analisada    | [branch / commit / versão]        |
| Data da análise     | [DD/MM/AAAA]                      |
| Responsável         | [Nome]                            |
| Situação da análise | Pendente / Em análise / Concluída |

**Comportamento esperado:**

[Resumo do comportamento esperado.]

**Status:** [Atendido / Parcial / Ausente / Divergente / Não verificável]

**Evidência:**

[Teste / execução / arquivo / log / screenshot / resposta da API.]

**GAP:** — / GAP-XX

---

# 6. GAPs identificados

Use esta seção somente quando algum épico apresentar um problema que precise de detalhamento.

## GAP-01 — [Título curto]

**Relacionado a:** EP-XX 
**Status:** Aberto / Resolvido

**Esperado:**

[O que deveria acontecer.]

**Encontrado:**

[O que foi encontrado durante a análise.]

**Problema:**

[Diferença entre o esperado e o encontrado.]

**Ação necessária:**

[O que precisa ser feito.]

**Como validar:**

[Como comprovar que o problema foi resolvido.]

**Evidência:**

[Teste, log, screenshot, arquivo etc.]

---

# 7. Conclusão

| Situação da análise | Quantidade |
| ------------------- | ---------: |
| Pendente            |          0 |
| Em análise          |          0 |
| Concluída           |          0 |

| Resultado dos CAs | Quantidade |
| ----------------- | ---------: |
| Atendido          |          0 |
| Parcial           |          0 |
| Ausente           |          0 |
| Divergente        |          0 |
| Não verificável   |          0 |
| GAPs abertos      |          0 |

**Situação geral:** Adequada / Requer ajustes / Bloqueada / Não conclusiva

**Resultado:**

[Resumo do estado atual dos requisitos analisados e dos principais problemas encontrados.]

---

**Última revisão:** [DD/MM/AAAA]
