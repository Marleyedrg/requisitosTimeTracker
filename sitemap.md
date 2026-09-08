# Sitemap — Time Tracker

**Projeto:** Time Tracker Open Source

**Versão:** 1.0.0 (MVP)

**Status:** Rascunho

**Data:** Setembro de 2026

## Legenda de acesso por perfil

| Símbolo | Perfil      |
| ------- | ----------- |
| `[P1]`  | Gestor      |
| `[P2]`  | Colaborador |

### Estados do colaborador

O sistema diferencia o **status de conexão** do **estado de atividade**:

| Estado | Significado |
| --- | --- |
| `Online` | Colaborador autenticado, com o agente conectado ao sistema e uma Task ativa. |
| `Offline` | Colaborador não está conectado ao sistema ou não possui uma sessão ativa. |
| `Ativo` | Colaborador apresentou interação recente com mouse ou teclado. |
| `Inativo` | O tempo sem interação com mouse ou teclado ultrapassou o limite configurado. |

> Um colaborador pode estar `Online` e `Inativo` ao mesmo tempo.

> Rotas, autenticação e pontos de entrada não especificados permanecem como **A definir**.

## 1. Área pública

### Dashboard PWA

O Gestor cria uma conta e realiza login pelo Dashboard.

```text id="ftxpxd"
Dashboard
   │
   ├── Criar conta
   │
   └── Login
          ↓
    Área do Gestor
```

### Agente Desktop

O Colaborador realiza login no sistema através do Agente Desktop.

Após o login, o colaborador seleciona uma Task disponível para iniciar o monitoramento da atividade.

```text id="qfjg8h"
Agente
   │
   └── Login
        ↓
   Selecionar Task
        ↓
   Monitoramento
```

> O fluxo de criação da conta do Colaborador ainda precisa ser definido.

## 2. Área do Gestor

**Acesso:** `[P1]` Gestor

**Ponto de entrada:** `2.1 Painel de acompanhamento`

| #   | Tela                           | Descrição                                                                                                                                                                      | Épico/US  |
| --- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------- |
| 2.1 | **Painel de acompanhamento** | Exibe status do sistema, seletor de data, KPIs de horas monitoradas, colaboradores Online/Offline, estado Ativo/Inativo, software em uso, distribuição por categoria e atividades dos colaboradores. 
| 2.2 | **Tasks**                      | Permite criar e gerenciar Tasks e associar colaboradores a elas.                                                                                                               
| 2.3 | **Configurações do sistema**   | Permite consultar e atualizar tempo de inatividade, regras de categorização e demais configurações disponíveis para o agente.                                                  
| 2.4 | **Relatório de produtividade** | Apresenta horas por colaborador, Task e categoria, com filtros e exportação em CSV e PDF.                                                                                      

### 2.1 Painel de acompanhamento

```text id="8hxd6y"
Painel
├── Colaboradores Online/Offline
├── Estado Ativo/Inativo
├── Atividade atual
├── Software mais utilizado
├── Horas monitoradas
├── Distribuição por categoria
└── Timeline de atividades
```

### 2.2 Tasks

```text id="yhvslm"
Tasks
├── Visualizar Tasks
├── Criar Task
├── Editar Task
└── Associar colaboradores
```

### 2.3 Configurações do sistema

```text id="g2h1ec"
Configurações
├── Tempo de inatividade
└── Regras de categorização
```

### 2.4 Relatório de produtividade

```text id="lzc8l3"
Relatórios
├── Filtrar por data
├── Filtrar por colaborador
├── Filtrar por Task
├── Distribuição por categoria
├── Total de horas
├── Exportar CSV
└── Exportar PDF
```

## 3. Área do Colaborador

**Acesso:** `[P2]` Colaborador na estação Windows

**Ponto de entrada:** `3.1 Login no Agente`

| #   | Tela ou visualização      | Descrição                                                                                                          | Épico/US  |
| --- | ------------------------- | ------------------------------------------------------------------------------------------------------------------ | --------- |
| 3.1 | **Login no Agente**       | Permite que o colaborador realize login no sistema através do Agente Desktop.                                      
| 3.2 | **Seleção de Task**       | Exibe as Tasks disponíveis para o colaborador e permite selecionar em qual está trabalhando.                       
| 3.3 | **Agente na System Tray** | Exibe o status Online/Offline, o estado Ativo/Inativo e a Task ativa. O agente executa em segundo plano o monitoramento e a sincronização dos registros. 

System Tray
├── Task ativa
├── Status Online/Offline
├── Estado Ativo/Inativo
└── Monitoramento

### Fluxo do Colaborador

```text id="65vbgr"
Login
  ↓
Selecionar Task
  ↓
Task ativa
  ↓
Monitoramento
  ↓
System Tray
```

Enquanto uma Task estiver ativa, os registros de atividade gerados pelo agente serão relacionados a ela.

> Não está definida uma área web específica para o Colaborador.

## 4. Área administrativa

**Não definida.**

O escopo atual não estabelece um perfil de Administrador separado do Gestor.

## 5. Fluxos transversais

| #   | Comportamento                    | Descrição                                                                                                                  | Épico/US  |
| --- | -------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | --------- |
| 5.1 | **Atualização de configurações** | O agente consulta as configurações disponíveis no servidor e aplica os valores recebidos.                                  
| 5.2 | **Registro e sincronização**     | Quando uma mudança de atividade é detectada, o registro é armazenado no SQLite e enviado ao backend.                       
| 5.3 | **Sincronização offline**        | Em caso de falha de comunicação, os registros permanecem no SQLite e são sincronizados após o restabelecimento da conexão. 
| 5.4 | **Categorização automática**     | O backend classifica os registros por palavras-chave nas categorias Desenvolvimento, Design, Comunicação, Social e Outros. 
| 5.5 | **Relação com Task**             | Os registros de atividade são relacionados à Task ativa do colaborador.                                                    
| 5.6 | **Exportação de relatórios**     | Os dados de produtividade podem ser exportados nos formatos CSV e PDF.                                                     
| 5.7 | **Detecção de inatividade** | O agente considera o colaborador Ativo enquanto houver interação recente com mouse ou teclado. Quando o tempo sem interação ultrapassar o limite configurado, seu estado passa para Inativo. | A definir |

## 6. Visão geral da navegação

```text id="7rwdnj"
Time Tracker
│
├── Dashboard PWA [P1]
│   │
│   ├── Criar conta
│   └── Login
│       │
│       ├── Painel de acompanhamento
│       ├── Tasks
│       │   ├── Criar Task
│       │   ├── Editar Task
│       │   └── Associar colaboradores
│       │
│       ├── Configurações
│       │   ├── Tempo de inatividade
│       │   └── Regras de categorização
│       │
│       └── Relatórios
│           ├── Filtros
│           ├── CSV
│           └── PDF
│
└── Agente Desktop [P2]
    │
    └── Login
        │
        ├── Selecionar Task
        │
        └── System Tray
            │
            ├── Task ativa
            ├── Estado do agente
            └── Monitoramento
```

## 7. Pendências

* Definir autenticação e autorização.
* Definir as rotas do Dashboard PWA.
* Definir o fluxo de criação de conta do Colaborador.
* Definir como as contas dos colaboradores serão associadas aos gestores ou à organização.
* Definir se o Colaborador pode trocar ou encerrar uma Task durante a execução.
* Definir o comportamento do agente quando nenhuma Task estiver ativa.
* Definir se **Relatório de produtividade** e **Configurações do sistema** serão telas independentes ou componentes do painel.
* Definir permissões detalhadas para Gestor e Colaborador.
* Confirmar se haverá uma área web específica para o Colaborador.
* Avaliar a necessidade de um perfil Administrador separado do Gestor.
* Definir o fluxo e os detalhes da exportação em CSV e PDF.
* Definir as regras de retry, duplicidade e idempotência da sincronização.

**Última revisão:** 2026-09-08
