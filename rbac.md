# RBAC — Controle de Acesso Baseado em Perfil

**Projeto:** Time Tracker Open Source
**Versão:** 1.0.0 (MVP)
**Status:** Rascunho
**Data:** Setembro de 2026

## 1. Objetivo

Existem dois perfis:

| Perfil          | Descrição                                                                                      |
| --------------- | ---------------------------------------------------------------------------------------------- |
| **Gestor**      | Acompanha atividades dos colaboradores, consulta relatórios e altera configurações do sistema. |
| **Colaborador** | Utiliza a estação Windows monitorada pelo agente.                                              |

> A forma de autenticação e atribuição desses perfis ainda precisa ser definida.

---

## 2. Permissões

### Dashboard e relatórios

| Ação                     | Gestor | Colaborador | Referência   |
| ------------------------ | ------ | ----------- | ------------ |
| Acessar dashboard        | Sim    | A definir   | RF-10, RF-14 |
| Visualizar atividades    | Sim    | A definir   | RF-10        |
| Consultar sumário diário | Sim    | A definir   | RF-11        |
| Filtrar por colaborador  | Sim    | Não         | RF-11        |
| Exportar CSV/PDF         | Sim    | A definir   | RF-16        |

### Configurações

| Ação                         | Gestor    | Colaborador | Referência       |
| ---------------------------- | --------- | ----------- | ---------------- |
| Consultar configurações      | Sim       | Não         | RF-09, RF-12     |
| Alterar intervalo de captura | Sim       | Não         | RF-12            |
| Alterar tempo de inatividade | Sim       | Não         | RF-12            |
| Consultar categorias         | Sim       | A definir   | RF-09            |
| Criar palavra-chave          | Sim       | Não         | RF-08            |
| Editar palavra-chave         | Sim       | Não         | RF-08            |
| Excluir palavra-chave        | A definir | Não         | Não especificado |

### Agente desktop

| Ação                               | Gestor    | Colaborador |
| ---------------------------------- | --------- | ----------- |
| Utilizar agente na estação Windows | Não       | Sim         |
| Visualizar status Online/Offline   | Não       | Sim         |

A captura, sincronização e atualização de configurações são realizadas automaticamente pelo agente e não são consideradas ações manuais do Colaborador.

---

## 3. Acesso às interfaces

| Interface                  | Gestor    | Colaborador |
| -------------------------- | --------- | ----------- |
| Painel de acompanhamento   | Sim       | Não  |
| Configurações do sistema   | Sim       | Não         |
| Relatório de produtividade | Sim       | A definir   |
| Agente na System Tray      | A definir | Sim         |

A organização dessas interfaces está definida em [`sitemap.md`](sitemap.md).

---

## 4. Escopo dos dados

As permissões indicam **o que** cada perfil pode fazer. Também é necessário definir **quais dados** cada perfil pode acessar.

### Gestor

Ainda precisa ser definido se o Gestor poderá acessar:

* todos os colaboradores;
* apenas colaboradores vinculados a ele;
* colaboradores de uma equipe ou departamento;
* registros históricos.

### Colaborador

Ainda precisa ser definido se o Colaborador poderá consultar suas próprias atividades ou se utilizará apenas o agente desktop.

Também precisa ser definido como uma conta do sistema será relacionada ao `username` do Windows registrado pelo agente.

---

## 5. Regras de acesso

* Uma ação só deve ser permitida para os perfis autorizados.
* Uma permissão não definida não deve ser considerada permitida.
* O backend deve validar as permissões, mesmo que a interface esconda determinada ação.
* O acesso deve considerar tanto o perfil quanto o escopo dos dados.

---

## 6. Pendências

* [ ] Definir como Gestor e Colaborador realizam autenticação.
* [ ] Definir como os perfis são atribuídos.
* [ ] Definir acesso do Colaborador ao dashboard e relatórios.
* [ ] Definir quais colaboradores cada Gestor pode visualizar.
* [ ] Definir se o Colaborador pode consultar suas próprias atividades.
* [ ] Definir vínculo entre conta e `username` do Windows.
* [ ] Definir se palavras-chave podem ser excluídas.
* [ ] Definir autenticação e autorização do agente.
* [ ] Definir comportamento quando um acesso é negado.

---

## 7. Referências

| Documento                  | Relação                       |
| -------------------------- | ----------------------------- |
| [`visao.md`](visao.md)     | Requisitos RF-08 a RF-16      |
| [`sitemap.md`](sitemap.md) | Interfaces e áreas por perfil |

**Última revisão:** 2026-09-06
