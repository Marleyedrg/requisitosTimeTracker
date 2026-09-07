# Documentação de Requisitos — Time Tracker

Este repositório concentra a documentação funcional e de requisitos do **Time Tracker**.

Seu objetivo é manter uma fonte clara e rastreável sobre:

* o que o sistema deve fazer;
* como a implementação deve ser organizada;
* como validar cada comportamento;
* como identificar diferenças entre requisito e código.

---

# Sumário

## Para Desenvolvedores

1. [O que você precisa saber](#desenvolvedor)
2. [Documentos principais](#documentos-do-desenvolvedor)
3. [Como os requisitos chegam até o código](#fluxo-do-desenvolvedor)
4. [Como ler um épico](#como-ler-um-épico)
5. [Antes de implementar](#antes-de-implementar)
6. [Quando considerar uma implementação pronta](#quando-considerar-uma-implementação-pronta)

## Para Analistas de Requisitos

1. [O que você precisa saber](#analista-de-requisitos)
2. [Documentos principais](#documentos-do-analista)
3. [Documento principal de análise](#relatório-rq-gap)
4. [Como realizar uma análise](#fluxo-do-analista)
5. [Quando criar um GAP](#quando-criar-um-gap)
6. [Quando um requisito muda](#quando-um-requisito-muda)

## Referência rápida

1. [Mapa dos documentos](#mapa-dos-documentos)
2. [Identificadores](#identificadores)
3. [Informações ainda não definidas](#informações-a-definir)

---

# Desenvolvedor

O **Desenvolvedor** transforma requisitos em software.

Sua principal pergunta deve ser:

> **O que preciso implementar para atender ao critério de aceite?**

<a id="documentos-do-desenvolvedor"></a>

## Documentos do Desenvolvedor

### `epicos/`

É o principal ponto de entrada para implementação.

Um épico organiza o trabalho:

```text
EP-01
│
└── US-01
    │
    └── CA-01
        │
        ├── TASK-01
        ├── TASK-02
        └── TASK-03
```

### `visao.md`

Contém os requisitos que justificam a implementação:

* `RN` — Regra de Negócio;
* `RF` — Requisito Funcional;
* `RNF` — Requisito Não Funcional;
* `CA` — Critério de Aceite.

### `rbac.md`

Consultar quando a funcionalidade envolver:

* perfis;
* permissões;
* acesso a dados;
* autorização.

### `sitemap.md`

Consultar quando houver interface ou navegação.

### `responsividade.md`

Consultar quando houver comportamento responsivo.

### `relatorio-rq-gap.md`

Consultar quando o Analista identificar:

* comportamento ausente;
* implementação parcial;
* divergência;
* pendência;
* necessidade de correção.

---

<a id="fluxo-do-desenvolvedor"></a>

## Fluxo do Desenvolvedor

```text
visao.md
   ↓
RF / RNF / RN
   ↓
CA
   ↓
EP / US
   ↓
TASK
   ↓
Código
   ↓
Teste / Evidência
```

O Desenvolvedor não deve decidir sozinho comportamentos que não estejam definidos.

---

<a id="como-ler-um-épico"></a>

## Como ler um épico

Ao abrir um épico, procure responder:

1. Qual funcionalidade está sendo entregue?
2. Qual CA precisa ser atendido?
3. Quais requisitos estão relacionados?
4. Quais TASKs precisam ser implementadas?
5. Como o comportamento será testado?

Exemplo:

```text
EP-01 — Captura da janela ativa

CA-01
├── RF-01
├── RNF-01
│
├── TASK-01 — obter executável
├── TASK-02 — obter título
├── TASK-03 — capturar screenshot
└── TASK-04 — montar registro
```

---

<a id="antes-de-implementar"></a>

## Antes de implementar

* [ ] Sei qual EP estou implementando.
* [ ] Sei qual CA precisa ser atendido.
* [ ] Conheço os RF, RNF e RN relacionados.
* [ ] O CA é testável.
* [ ] As permissões necessárias estão definidas.
* [ ] Não existe `A definir` bloqueando a implementação.
* [ ] As TASKs estão relacionadas ao CA.

Se uma decisão necessária estiver indefinida, não invente o comportamento no código.

---

<a id="quando-considerar-uma-implementação-pronta"></a>

## Quando considerar uma implementação pronta

Uma funcionalidade não está pronta apenas porque o código foi escrito.

Verifique:

* [ ] CA executado.
* [ ] Evidência coletada.
* [ ] Permissões seguem o RBAC.
* [ ] Interface segue os documentos relacionados, quando aplicável.

Exemplos de evidência:

* teste automatizado;
* execução manual;
* log;
* screenshot;
* resposta da API;
* registro no banco.

---

# Analista de Requisitos

O **Analista de Requisitos** verifica se o que foi especificado está realmente sendo entregue.

Sua principal pergunta deve ser:

> **O sistema está atendendo ao que foi especificado?**

<a id="documentos-do-analista"></a>

## Documentos do Analista

O Analista consulta o conjunto completo da documentação.

### `visao.md`

Fonte principal de:

* problema;
* escopo;
* regras de negócio;
* requisitos funcionais;
* requisitos não funcionais;
* critérios de aceite.

### `epicos/`

Mostra como os requisitos foram organizados para implementação.

### `rbac.md`

Define perfis e permissões.

### `sitemap.md`

Define interfaces e navegação.

### `responsividade.md`

Define comportamento responsivo.

### `relatorio-rq-gap.md`

É o **documento principal de análise do Analista de Requisitos**.

---

<a id="relatório-rq-gap"></a>

## Relatório RQ-GAP

Os documentos de requisitos dizem:

```text
O que deveria existir
```

O código mostra:

```text
O que existe
```

O relatório RQ-GAP registra:

```text
O que foi encontrado
e se está de acordo
```

Fluxo:

```text
Requisito
   ↓
Implementação
   ↓
Evidência
   ↓
Status
   ↓
GAP, se necessário
```

### Status utilizados

* **Atendido**
* **Parcial**
* **Ausente**
* **Divergente**
* **Não verificável**

Exemplo:

```text
RF-01 → Atendido → teste + evidência

RF-03 → Parcial → GAP-01

RF-04 → Não verificável → teste pendente
```

O relatório não substitui o requisito original.

```text
visao.md
└── RF-01
```

continua sendo a definição oficial.

No relatório:

```text
RF-01
└── Atendido
    └── Evidência
```

---

<a id="fluxo-do-analista"></a>

## Fluxo do Analista

### 1. Identificar o requisito

Exemplo:

```text
RF-01
CA-01
```

### 2. Verificar a implementação

Procure:

* código;
* endpoint;
* função;
* banco;
* interface;
* teste relacionado.

### 3. Executar ou verificar o comportamento

Sempre que possível, valide o CA.

### 4. Coletar evidência

Exemplo:

```text
CA-01
→ teste executado
→ registro gerado
→ screenshot coletado
```

### 5. Definir o status

```text
Atendido
Parcial
Ausente
Divergente
Não verificável
```

### 6. Criar GAP quando necessário

Se existir algo que precise ser corrigido, investigado ou decidido.

---

<a id="quando-criar-um-gap"></a>

## Quando criar um GAP

Crie um GAP quando houver:

* parte do requisito não implementada;
* requisito ausente;
* comportamento diferente do especificado;
* teste necessário ainda não realizado;
* evidência insuficiente;
* dúvida que impede a conclusão;
* divergência entre documentação e implementação.

Exemplo:

```text
RF-04

Esperado:
sincronizar o registro quando a conexão retornar.

Encontrado:
registro permanece apenas no SQLite.

GAP-02
```

O GAP deve explicar:

```text
Esperado
   ↓
Encontrado
   ↓
Diferença
   ↓
Ação necessária
   ↓
Como validar
```

---

<a id="quando-um-requisito-muda"></a>

## Quando um requisito muda

Atualize primeiro o documento principal da informação.

### RF, RNF ou RN

```text
visao.md
   ↓
CA
   ↓
EP / US
   ↓
TASK
   ↓
Código
   ↓
RQ-GAP
```

### Permissão

```text
rbac.md
   ↓
CA
   ↓
Implementação
   ↓
RQ-GAP
```

### Interface

```text
sitemap.md
   ↓
responsividade.md
   ↓
EP
   ↓
Implementação
   ↓
RQ-GAP
```

---

# Referência rápida

<a id="mapa-dos-documentos"></a>

## Mapa dos documentos

```text
documentacao/
│
├── README.md
├── visao.md
├── sitemap.md
├── rbac.md
├── responsividade.md
├── relatorio-rq-gap.md
│
└── epicos/
    ├── EP-01-*.md
    ├── EP-02-*.md
    └── ...
```

| Documento             | Função                             |
| --------------------- | ---------------------------------- |
| `visao.md`            | Define requisitos                  |
| `epicos/`             | Organiza a implementação           |
| `sitemap.md`          | Define interfaces                  |
| `rbac.md`             | Define permissões                  |
| `responsividade.md`   | Define comportamento responsivo    |
| `relatorio-rq-gap.md` | Analisa requisito vs implementação |

Em resumo:

```text
visao.md = define
epicos/ = organiza
código = implementa
RQ-GAP = analisa
```

---

<a id="identificadores"></a>

## Identificadores

| ID     | Significado                                 |
| ------ | ------------------------------------------- |
| `RN`   | Regra de Negócio                            |
| `RF`   | Requisito Funcional                         |
| `RNF`  | Requisito Não Funcional                     |
| `CA`   | Critério de Aceite                          |
| `EP`   | Épico                                       |
| `US`   | User Story                                  |
| `TASK` | Tarefa                                      |
| `GAP`  | Problema ou diferença encontrada na análise |

Não crie outro identificador para analisar um requisito existente.

Use:

```text
RF-01 → Atendido
RF-03 → Parcial → GAP-01
CA-04 → Não verificável
```

em vez de criar `RQ-01`, `RQ-02`, etc.

---

<a id="informações-a-definir"></a>

## Informações a definir

Quando uma decisão ainda não foi tomada, registre:

```text
A definir: [decisão necessária]
```

Exemplo:

```text
A definir: o Colaborador poderá visualizar suas próprias atividades?
```

Não transforme uma dúvida em requisito aprovado.

---

**Última revisão:** 2026-09-06
