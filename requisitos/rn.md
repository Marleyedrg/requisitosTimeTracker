# Regras de Negócio — Time Tracker

**Versão:** 1.0.0  
**Status:** Rascunho  
**Data:** Setembro de 2026

---

## 1. Objetivo

Este documento define as **Regras de Negócio (RN)** do Time Tracker.

As regras estabelecem condições e limites que devem ser respeitados pelo sistema, independentemente da forma como serão implementados.

---

## 2. Regras de Negócio

### RN-01 — Monitoramento vinculado à task

Todo monitoramento deve estar associado a uma **task ativa**.

Não deve existir monitoramento de atividade sem uma task em execução.

---

### RN-02 — Configuração da task pelo gestor

Toda task deve ser criada e configurada por um gestor.

A task deve definir, no mínimo:

- identificação;
- descrição;
- colaboradores associados;
- serviços ou aplicações que serão monitorados.

---

### RN-03 — Serviços monitorados

O gestor deve definir previamente quais serviços ou aplicações fazem parte do monitoramento de cada task.

Cada serviço deve possuir uma identificação que permita ao agente reconhecê-lo durante sua execução.

Exemplo:

```text
TASK-24 — Desenvolvimento do Dashboard

Serviços monitorados:
- chrome
- code
- terminal
```

---

### RN-04 — Acesso às tasks

O colaborador deve visualizar somente as tasks às quais estiver associado.

Uma task somente pode ser iniciada por um colaborador vinculado a ela.

---

### RN-05 — Transparência antes do início

Antes de iniciar uma task, o colaborador deve ser informado sobre:

- qual task será iniciada;
- quais serviços ou aplicações serão monitorados;
- que será registrado o tempo de utilização desses serviços;
- que sua atividade e inatividade serão identificadas através da interação com mouse e teclado.

A task não deve iniciar antes da apresentação dessas informações.

---

### RN-06 — Ciência do colaborador

O colaborador deve confirmar que está ciente das condições de monitoramento antes de iniciar cada execução de uma task.

A confirmação representa ciência das condições apresentadas.

Sem a confirmação:

- a task não deve ser iniciada;
- o monitoramento não deve começar;
- o colaborador não deve ser apresentado como Online naquela task.

---

### RN-07 — Registro da ciência

O sistema deve manter registro das condições apresentadas ao colaborador no início da task.

O registro deve permitir relacionar, no mínimo:

- colaborador;
- task;
- data e horário;
- serviços monitorados;
- confirmação de ciência.

---

### RN-08 — Monitoramento limitado aos serviços da task

Durante a execução de uma task, o agente deve monitorar somente os serviços ou aplicações definidos pelo gestor para aquela task.

O agente deve identificar o serviço em execução e verificar sua correspondência com os serviços configurados.

```text
Aplicação detectada
        ↓
corresponde a um serviço da task?
        ↓
    ┌───┴───┐
   não     sim
    │       │
 ignora   registra
```

Aplicações que não correspondam aos serviços definidos na task não devem gerar registros de monitoramento.

---

### RN-09 — Informações registradas

Quando um serviço pertencente à task estiver sendo utilizado, o sistema poderá registrar:

- colaborador;
- usuário Windows;
- task;
- serviço ou aplicação identificada;
- horário de início;
- horário de término;
- duração;
- estado de atividade ou inatividade.

O registro deve permanecer relacionado à task em execução.

---

### RN-10 — Identificação de atividade e inatividade

A interação com mouse e teclado deve ser utilizada somente para determinar se o colaborador está **Ativo** ou **Inativo**.

O sistema deve considerar um colaborador inativo quando o período sem interação ultrapassar o limite configurado.

Exemplo:

```text
Última interação:
14:20

Limite:
5 minutos

14:25
↓
Inativo
```

Quando uma nova interação ocorrer:

```text
14:42
↓
Ativo
```

O conteúdo das interações não faz parte do monitoramento.

---

### RN-11 — Limite de inatividade

O limite utilizado para determinar inatividade deve ser configurável pelo gestor.

Exemplo:

```text
Limite configurado:
5 minutos

Sem interação por 5 minutos
↓
Inativo
```

---

### RN-12 — Estado Online

Para o gestor, o colaborador deve ser considerado **Online** somente quando possuir uma task efetivamente iniciada.

Estar autenticado no agente não significa estar Online.

```text
Login
  ↓
Autenticado
  ↓
Seleciona task
  ↓
Visualiza condições
  ↓
Confirma ciência
  ↓
Inicia task
  ↓
Online
```

---

### RN-13 — Encerramento da task

Ao encerrar uma task:

- o monitoramento daquela task deve ser encerrado;
- o período de atividade atual deve ser finalizado;
- novos registros não devem ser associados à sessão encerrada;
- o colaborador deve deixar de ser apresentado como Online.

O colaborador poderá permanecer autenticado no agente.

---

### RN-14 — Troca de task

O colaborador não deve manter duas tasks ativas simultaneamente.

Para iniciar uma nova task, a task atual deve ser encerrada.

A nova task deve apresentar novamente suas próprias condições de monitoramento antes do início.

---

### RN-15 — Alteração dos serviços monitorados

Alterações no conjunto de serviços monitorados não devem ampliar silenciosamente o monitoramento de uma task já iniciada.

Caso o gestor altere os serviços da task durante sua execução, o colaborador deve ser informado sobre a nova configuração antes que ela passe a valer para o monitoramento.

---

### RN-16 — Jornada de trabalho

O gestor poderá definir a jornada dos colaboradores sob sua responsabilidade.

A jornada poderá considerar:

- dias de trabalho;
- horário previsto de entrada;
- horário previsto de saída;
- intervalo;
- carga horária.

**Jornada, task e atividade são conceitos distintos.**

```text
Jornada
= período previsto de trabalho

Task
= trabalho selecionado

Atividade
= interação registrada durante a task
```

---

### RN-17 — Possível hora extra

Quando uma task permanecer ativa após o horário previsto para encerramento da jornada, o período posterior poderá ser identificado como **possível hora extra**.

A identificação realizada pelo sistema não representa automaticamente aprovação da hora extra.

---

### RN-18 — Acesso do colaborador

O colaborador deve visualizar somente seus próprios dados disponibilizados pelo sistema.

Ele não deve possuir acesso aos registros de outros colaboradores.

---

### RN-19 — Acesso do gestor

O gestor deve visualizar somente dados dos colaboradores sob sua responsabilidade.

O acesso a colaboradores fora do seu escopo não deve ser concedido automaticamente.

---

### RN-20 — Transparência durante a task

Enquanto uma task estiver ativa, o colaborador deve conseguir consultar:

- qual task está em execução;
- quais serviços estão sendo monitorados;
- se o monitoramento está ativo;
- seu estado de atividade ou inatividade.

As informações de monitoramento não devem estar disponíveis apenas antes do início da task.

---

### RN-21 — Finalidade e minimização

O monitoramento deve ser limitado às informações necessárias para acompanhamento das tasks, atividade, inatividade e jornada.

O Time Tracker não deve ampliar a coleta além do escopo necessário para essas funcionalidades.

---

### RN-22 — Atividade não representa produtividade

Os dados de atividade, inatividade, tempo e utilização dos serviços podem auxiliar o gestor na análise do trabalho.

O sistema não deve considerar automaticamente que:

```text
maior tempo ativo
=
maior produtividade
```

Atividade é uma informação de acompanhamento e não uma medida absoluta de produtividade.

---

## 3. Fluxo das Regras de Negócio

```text
GESTOR
   ↓
cria task
   ↓
define colaboradores
   ↓
define serviços monitorados
   ↓
disponibiliza task
   ↓

COLABORADOR
   ↓
seleciona task
   ↓
visualiza condições
   ↓
confirma ciência
   ↓
inicia task
   ↓
fica Online
   ↓

AGENTE
   ↓
identifica aplicação em execução
   ↓
corresponde a serviço da task?
   ┌───────────┴───────────┐
  não                     sim
   │                       │
ignora                  registra
                           │
                           ├── serviço
                           ├── duração
                           ├── usuário Windows
                           └── ativo/inativo
```

---

## 4. Regras Fundamentais

As principais regras do Time Tracker são:

1. **não existe monitoramento sem uma task ativa;**
2. **o gestor define previamente os serviços monitorados pela task;**
3. **o colaborador deve conhecer as condições antes de iniciar;**
4. **somente serviços configurados na task podem gerar registros;**
5. **mouse e teclado são utilizados somente para determinar atividade ou inatividade;**
6. **todo registro deve permanecer relacionado ao colaborador e à task;**
7. **o colaborador fica Online somente enquanto uma task estiver ativa;**
8. **encerrar a task encerra o monitoramento.**