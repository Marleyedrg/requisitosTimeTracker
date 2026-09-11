# Regras de Negócio e Requisitos Funcionais — Time Tracker

**Versão:** 1.0.0  
**Status:** Rascunho  
**Data:** Setembro de 2026

---

## 1. Objetivo

Este documento organiza as **Regras de Negócio (RN)** e os **Requisitos Funcionais (RF)** do Time Tracker.

Cada regra apresenta abaixo as funcionalidades necessárias para atendê-la.

---

# RN-01 — Contas de usuário

A criação da conta do **Colaborador** deve ocorrer pelo Agente Desktop quando não existir um usuário registrado na estação.

O **Gestor** deve possuir sempre a opção de criar uma conta por e-mail através do Dashboard.

### RF-01 — Criar ou acessar conta do colaborador

O Agente Desktop deve verificar se existe um usuário registrado na estação e, quando necessário, permitir a criação da conta do colaborador.

### RF-02 — Criar e acessar conta do gestor

O Dashboard deve permitir ao gestor criar uma conta utilizando e-mail e posteriormente acessar o sistema.

---

# RN-02 — Associação entre gestor e colaborador

A associação inicial entre gestor e colaborador deve ser realizada através de um **código de 6 dígitos**.

Após a associação, o colaborador poderá ser incluído nas tasks do gestor.

### RF-03 — Gerar código de associação

O Dashboard deve permitir ao gestor gerar um código de 6 dígitos para associação.

### RF-04 — Associar colaborador

O Agente Desktop deve permitir ao colaborador informar o código e realizar a associação ao gestor.

### RF-05 — Gerenciar colaboradores associados

O Dashboard deve permitir ao gestor consultar os colaboradores associados a ele.

---

# RN-03 — Configuração da task

Toda task deve ser criada pelo gestor e definir:

- descrição;
- colaboradores associados;
- serviços ou aplicações monitorados.

### RF-06 — Criar e editar tasks

O Dashboard deve permitir ao gestor criar e editar tasks e definir seus colaboradores e serviços monitorados.

---

# RN-04 — Acesso às tasks

O colaborador deve visualizar e iniciar somente as tasks às quais estiver associado.

### RF-07 — Listar tasks do colaborador

O agente deve apresentar somente as tasks disponíveis para o colaborador autenticado.

---

# RN-05 — Monitoramento vinculado à task

Todo monitoramento deve estar associado a uma **task ativa**.

Não deve existir monitoramento sem uma task em execução.

### RF-08 — Iniciar task

O agente deve permitir o início de uma task somente após o cumprimento das condições necessárias para o monitoramento.

---

# RN-06 — Transparência e ciência

Antes de iniciar uma task, o colaborador deve conhecer:

- a task selecionada;
- os serviços monitorados;
- as informações registradas;
- o uso de mouse e teclado para atividade/inatividade.

O colaborador deve confirmar sua ciência antes do início.

### RF-09 — Exibir condições da task

O agente deve apresentar as condições de monitoramento antes do início da task.

### RF-10 — Registrar ciência

O agente deve solicitar e registrar a confirmação de ciência do colaborador antes de iniciar o monitoramento.

---

# RN-07 — Alteração do monitoramento

Alterações nos serviços monitorados de uma task em execução devem ser informadas ao colaborador antes de serem aplicadas.

### RF-11 — Alterar serviços monitorados

O Dashboard deve permitir ao gestor alterar os serviços da task e o agente deve informar o colaborador quando o escopo da task ativa for alterado.

---

# RN-    — Serviços monitorados

O agente deve monitorar os serviços ou aplicações definidos.

### RF-12 — Monitorar serviços da task

O agente deve identificar a aplicação utilizada, comparar com os serviços definidos na task e registrar quando houver correspondência e quando não houver.

---

# RN-09 — Informações registradas

Durante o monitoramento poderão ser registrados:

- colaborador;
- usuário Windows;
- task;
- serviço ou aplicação;
- início;
- término;
- duração;
- estado Ativo/Inativo.

### RF-13 — Registrar períodos de utilização

O agente deve registrar os períodos de utilização dos serviços monitorados com as informações definidas pela task.

---

# RN-10 — Atividade e inatividade

Mouse e teclado devem ser utilizados somente para determinar o estado **Ativo/Inativo**.

O conteúdo das interações não deve ser coletado.

### RF-14 — Controlar atividade e inatividade

O agente deve alterar o estado entre Ativo e Inativo conforme o tempo sem interação e o limite configurado pelo gestor.

---

# RN-11 — Estado e execução da task

O colaborador será considerado **Online** somente enquanto estiver login no sistema.

O colaborador não pode possuir duas tasks ativas simultaneamente.

### RF-15 — Exibir estado do monitoramento

O agente deve apresentar ao colaborador:

- task ativa;
- serviços monitorados;
- estado Online/Offline;
- estado Ativo/Inativo.

### RF-16 — Acompanhar colaboradores Online

O Dashboard deve permitir ao gestor visualizar o estado dos colaboradores associados.

### RF-17 — Encerrar ou trocar task

O agente deve permitir encerrar ou trocar a task ativa, finalizando o monitoramento anterior antes de iniciar uma nova task.

---

# RN-12 — Continuidade dos registros

Falhas de comunicação não devem causar perda dos registros produzidos durante uma task.

### RF-18 — Armazenar registros localmente

O agente deve manter localmente os registros até que sejam confirmados pelo servidor.

### RF-19 — Sincronizar registros

O agente deve enviar os registros pendentes ao backend e retomar a sincronização após o restabelecimento da comunicação.

---

# RN-13 — Configurações do gestor

A **jornada de trabalho** e o **limite de inatividade** devem ser configurados pelo gestor.

### RF-20 — Configurar jornada

O Dashboard deve permitir ao gestor definir:

- dias de trabalho;
- entrada;
- saída;
- intervalo;
- carga horária.

### RF-21 — Configurar limite de inatividade

O Dashboard deve permitir ao gestor definir o tempo sem interação necessário para considerar o colaborador Inativo.

---

# RN-14 — Possível hora extra

Atividades realizadas após o término previsto da jornada poderão ser identificadas como **possível hora extra**.

### RF-22 — Identificar possível hora extra

O sistema deve identificar períodos de task ativa após o horário previsto de término da jornada.

---

# RN-15 — Acesso aos dados

O colaborador deve acessar somente seus próprios dados.

O gestor deve acessar somente dados dos colaboradores associados a ele.

### RF-23 — Consultar registros

O sistema deve permitir:

- ao colaborador consultar seus próprios registros;
- ao gestor consultar registros dos colaboradores associados.

---

# RN-16 — Relatórios e exportação

O gestor poderá consultar e exportar informações referentes aos colaboradores sob sua responsabilidade.

### RF-24 — Gerar relatórios

O Dashboard deve permitir consultar relatórios contendo:

- tasks;
- tempo por task;
- serviços monitorados;
- atividade/inatividade;
- jornada;
- possíveis horas extras.

### RF-25 — Exportar relatórios

A área de relatórios deve possuir um **botão de exportação** permitindo escolher entre:

- CSV;
- PDF.

---

# RN-17 — Histórico do colaborador

O colaborador deve poder consultar um histórico contendo somente as informações que foram efetivamente enviadas ao sistema.

### RF-26 — Consultar histórico TXT

A System Tray deve permitir ao colaborador visualizar seu histórico em formato **TXT**, contendo os registros enviados ao backend.

---

# RN-18 — Finalidade e minimização

O monitoramento deve ser limitado às informações necessárias para:

- acompanhamento de tasks;
- serviços utilizados;
- atividade e inatividade;
- jornada;
- relatórios.

Dados fora do escopo definido não devem fazer parte do monitoramento.

### RFs relacionados

Esta regra deve ser respeitada principalmente por:

- **RF-12 — Monitorar serviços da task**;
- **RF-13 — Registrar períodos de utilização**;
- **RF-14 — Controlar atividade e inatividade**.

---

# RN-19 — Visão gerencial do Dashboard

O gestor deve possuir uma visão consolidada das informações dos colaboradores associados a ele.

As informações apresentadas no Dashboard devem permitir acompanhar:

- estado Online/Offline dos colaboradores;
- tasks em andamento;
- tempo ativo e inativo;
- tempo registrado por task;
- jornada planejada e realizada;
- possíveis horas extras;
- sequência das atividades registradas.

As informações devem respeitar os filtros selecionados e as regras de acesso aos dados.

### RF-27 — Exibir Dashboard analítico

O Dashboard deve permitir ao gestor visualizar informações consolidadas dos colaboradores associados, incluindo:

- quantidade de colaboradores Online e Offline;
- quantidade de tasks ativas;
- tempo total ativo;
- tempo total inativo;
- tempo registrado por task;
- jornada planejada e realizada;
- possíveis horas extras;
- status dos colaboradores;
- Activity Timeline das tasks.

O Dashboard deve permitir filtrar as informações por:

- período;
- colaborador;
- task.

Ao alterar um filtro, os indicadores e visualizações relacionados devem ser atualizados de acordo com a seleção.

O Dashboard deve apresentar somente informações que o gestor possui permissão para consultar.

---