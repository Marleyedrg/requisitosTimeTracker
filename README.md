# Documentação de Requisitos — TimeTracker

Este repositório organiza os **requisitos, o trabalho de desenvolvimento e a análise das entregas** do TimeTracker.

![workFlowAnalista_dev](/epicos/workFlowAnalista_dev.png)


> **Analista:** define e mantém os requisitos e organiza o trabalho nos EPs.  

> **Desenvolvedor:** usa o EP como ponto de entrada para implementar o que foi definido.

---

# Sumário

## Desenvolvedor — comece aqui

**→ [Como desenvolver um EP](#1-desenvolvedor)**

O seu ponto de entrada é sempre o **EP**.

## Analista de Requisitos — comece aqui

**→ [Como definir e analisar requisitos](#2-analista-de-requisitos)**

O Analista mantém os requisitos, cria EPs e CAs e verifica as entregas.

## Referência

3. [Requisitos e trabalho](#3-requisitos-e-trabalho)
4. [Mapa dos documentos](#4-mapa-dos-documentos)
5. [Identificadores](#5-identificadores)

---

# 1. Desenvolvedor

> **Objetivo:** implementar o comportamento definido no EP.

O Desenvolvedor começa em:

```text
epicos/
```

O EP deve informar:

- o que será implementado;
- qual CA precisa ser atendido;
- quais TASKs precisam ser realizadas;
- quais documentos precisam ser consultados;
- como o comportamento será validado.

Não é necessário procurar requisitos pelo repositório inteiro.

> **Siga as referências indicadas no EP.**

## Fluxo

```text
Abrir EP
   ↓
Consultar referências indicadas
   ↓
Implementar TASKs
   ↓
Atender ao CA
   ↓
Testar
   ↓
Informar EP concluído
```

## Antes de entregar

- [ ] TASKs implementadas.
- [ ] CA atendido.
- [ ] Referências indicadas no EP respeitadas.
- [ ] Comportamento testado.
- [ ] Evidência disponível.

Quando estiver pronto:

```text
EP-02 implementado e pronto para análise.
```

---

# 2. Analista de Requisitos

> **Objetivo:** transformar necessidades em requisitos claros para o Desenvolvimento e verificar se o resultado atende ao especificado.

O Analista é responsável por:

- criar e manter `RN`, `RF` e `RNF`;
- definir os Critérios de Aceite (`CA`);
- criar e atualizar os Épicos (`EP`);
- relacionar requisitos e trabalho;
- indicar no EP quais documentos o Desenvolvedor deve consultar;
- atualizar a documentação quando necessário;
- analisar os EPs entregues;
- registrar evidências e GAPs.

## Ao preparar um EP

O Analista parte dos requisitos e organiza o trabalho:

```text
REQUISITOS                     TRABALHO

RF-03 ───────────────┐         EP-02
RN-02 ───────────────┼──────→  └── US-03
CA-02 ───────────────┘             ├── TASK-01
                                   ├── TASK-02
                                   └── TASK-03
```

O EP deve permitir que o Desenvolvedor responda rapidamente:

1. **O que preciso fazer?**
2. **Qual CA preciso atender?**
3. **Onde estão as informações necessárias?**
4. **Como saber se terminei?**

Se uma informação estiver em outro documento, **referencie-a no EP**.

Exemplo:

```text
Consultar:
- visao.md → RF-03
- rbac.md → permissões do Colaborador
- sitemap.md → tela de atividades
```

Assim, o EP funciona como **mapa para a implementação**, sem duplicar toda a documentação.

## Quando um EP for entregue

O Desenvolvimento informa:

```text
EP-02 implementado.
```

Então:

```text
EP entregue
    ↓
Consultar CA
    ↓
Verificar implementação
    ↓
Executar teste
    ↓
Coletar evidência
    ↓
Definir status
    ↓
Registrar GAP, se necessário
```

O resultado é registrado em:

```text
relatorio-rq-gap.md
```

Use somente:

| Status | Significado |
| --- | --- |
| **Atendido** | Funciona conforme especificado |
| **Parcial** | Apenas parte funciona |
| **Ausente** | Não foi implementado |
| **Divergente** | Funciona diferente do especificado |
| **Não verificável** | Não há evidência suficiente |

> Encontrar código não é suficiente para marcar um CA como **Atendido**. O comportamento precisa ser verificado.

As instruções detalhadas de análise, evidência e GAP ficam no `relatorio-rq-gap.md`.

---

# 3. Requisitos e trabalho

Requisitos e trabalho são **estruturas diferentes, mas relacionadas**.

```text
REQUISITOS                     TRABALHO

RF-03 ───────────────┐         EP-02
RN-02 ───────────────┼──────→  └── US-03
CA-07 ───────────────┘             ├── TASK-08
                                   ├── TASK-09
                                   └── TASK-10
```

## Requisitos

Definem **o que precisa ser atendido**:

```text
RN   → Regra de Negócio
RF   → Requisito Funcional
RNF  → Requisito Não Funcional
CA   → Critério de Aceite
```

## Trabalho

Organiza **como será implementado**:

```text
EP
└── US
    ├── TASK
    ├── TASK
    └── TASK
```

---

# 4. Mapa dos documentos

| Local | Função |
| --- | --- |
| `visao.md` | Define requisitos e CAs |
| `epicos/` | Organiza o trabalho e direciona o Desenvolvedor |
| `rbac.md` | Define perfis e permissões |
| `sitemap.md` | Define interfaces e navegação |
| `responsividade.md` | Define comportamento responsivo |
| `relatorio-rq-gap.md` | Registra a análise das entregas |

Regra rápida:

```text
visao.md          = DEFINE
epicos/           = DIRECIONA
código            = IMPLEMENTA
relatorio-rq-gap  = VERIFICA
```

---

# 5. Identificadores

| Grupo | IDs |
| --- | --- |
| **Requisitos** | `RN`, `RF`, `RNF`, `CA` |
| **Trabalho** | `EP`, `US`, `TASK` |
| **Análise** | `GAP` |

## Convenção do TimeTracker

No TimeTracker:

```text
EP-01 ↔ CA-01
EP-02 ↔ CA-02
EP-03 ↔ CA-03
...
```

Cada EP possui um CA correspondente de mesmo número.

Essa é uma **convenção do projeto**, não uma regra geral de requisitos.

---

# Em resumo

```text
ANALISTA

Define requisitos
      ↓
Define CA
      ↓
Cria EP
      ↓
Indica referências
      │
      ▼
DESENVOLVEDOR

Abre EP
      ↓
Consulta referências
      ↓
Implementa
      ↓
Testa
      ↓
Entrega EP
      │
      ▼
ANALISTA

Verifica CA
      ↓
Coleta evidência
      ↓
Define status
      ↓
Registra GAP
se necessário
```

> **O Analista define e direciona. O Desenvolvedor implementa. O Analista verifica o resultado.**

---

**Última revisão:** 2026-09-07
