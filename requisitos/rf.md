# Requisitos Funcionais — Time Tracker

**Versão:** 1.0.0  
**Status:** Rascunho  
**Data:** Setembro de 2026

---

## 1. Objetivo

Este documento define os **Requisitos Funcionais (RF)** do Time Tracker.

Os requisitos descrevem **o que o sistema deve fazer** para atender às regras de negócio definidas no projeto.

---

# 2. Agente Desktop

### RF-01 — Autenticar colaborador

**Relacionado:** RN-04

O Agente Desktop deve permitir que o colaborador se autentique no Time Tracker utilizando suas credenciais.

Após uma autenticação válida, o sistema deve identificar o colaborador responsável pela sessão.

---

### RF-02 — Identificar usuário Windows

**Relacionado:** RN-09

O agente deve identificar o usuário Windows da estação utilizada pelo colaborador.

Essa informação deve poder ser associada aos registros produzidos durante a execução de uma task.

---

### RF-03 — Listar tasks do colaborador

**Relacionado:** RN-04

Após a autenticação, o agente deve apresentar somente as tasks atribuídas ao colaborador autenticado.

---

### RF-04 — Exibir condições da task

**Relacionado:** RN-05, RN-20

Antes do início de uma task, o agente deve apresentar:

- identificação da task;
- descrição;
- serviços ou aplicações monitorados;
- informação sobre registro do tempo de utilização;
- informação sobre detecção de atividade e inatividade.

---

### RF-05 — Registrar ciência do colaborador

**Relacionado:** RN-06, RN-07

O agente deve solicitar confirmação de ciência das condições apresentadas antes de permitir o início da task.

O sistema deve registrar:

- colaborador;
- task;
- data e horário;
- serviços apresentados;
- confirmação de ciência.

---

### RF-06 — Iniciar task

**Relacionado:** RN-01, RN-06, RN-12

O agente deve permitir iniciar uma task após a confirmação de ciência do colaborador.

Ao iniciar a task, o sistema deve:

- criar uma sessão de execução;
- associá-la ao colaborador;
- ativar o monitoramento;
- apresentar o colaborador como Online para o gestor.

---

### RF-07 — Encerrar task

**Relacionado:** RN-13

O agente deve permitir que o colaborador encerre a task ativa.

Ao encerrar, o sistema deve:

- finalizar o período de atividade atual;
- encerrar o monitoramento;
- finalizar a sessão da task;
- deixar de apresentar o colaborador como Online.

---

### RF-08 — Trocar de task

**Relacionado:** RN-14

O agente deve permitir que o colaborador troque de task.

Antes de iniciar a nova task, o sistema deve:

1. encerrar a task atual;
2. apresentar as condições da nova task;
3. solicitar nova confirmação de ciência;
4. iniciar uma nova sessão.

O sistema não deve manter duas tasks ativas simultaneamente para o mesmo colaborador.

---

# 3. Monitoramento

### RF-09 — Identificar aplicação em execução

**Relacionado:** RN-03, RN-08

Durante uma task ativa, o agente deve identificar a aplicação ou serviço atualmente em execução.

---

### RF-10 — Comparar aplicação com serviços da task

**Relacionado:** RN-08

O agente deve verificar se a aplicação identificada corresponde a um dos serviços configurados para a task ativa.

```text id="wbtfuv"
Aplicação detectada
        ↓
Está configurada na task?
     ┌────┴────┐
    não       sim
     │         │
  ignora    monitora
```

Aplicações que não correspondam aos serviços configurados não devem gerar registros de monitoramento.

---

### RF-11 — Registrar período de utilização

**Relacionado:** RN-09

Quando uma aplicação pertencente à task estiver sendo utilizada, o agente deve registrar seu período de utilização.

O registro deve conter:

- colaborador;
- usuário Windows;
- task;
- serviço ou aplicação;
- horário de início;
- horário de término;
- duração;
- estado de atividade/inatividade.

---

### RF-12 — Detectar mudança de aplicação

**Relacionado:** RN-08, RN-09

O agente deve identificar quando ocorrer mudança entre aplicações monitoradas.

Quando houver mudança, o sistema deve:

1. finalizar o período anterior;
2. registrar seu horário de término;
3. iniciar um novo período para a nova aplicação.

Exemplo:

```text id="njpuhm"
VS Code
10:00 → 10:32

Chrome
10:32 → 10:48
```

O sistema deve evitar produzir registros repetidos enquanto a aplicação monitorada permanecer a mesma.

---

### RF-13 — Detectar inatividade

**Relacionado:** RN-10, RN-11

O agente deve verificar o tempo desde a última interação de mouse ou teclado.

Quando o período sem interação atingir o limite configurado, o colaborador deve ser considerado **Inativo**.

---

### RF-14 — Detectar retorno à atividade

**Relacionado:** RN-10

Quando ocorrer nova interação após um período de inatividade, o agente deve alterar o estado do colaborador para **Ativo**.

O período de inatividade deve possuir início, término e duração identificáveis.

---

### RF-15 — Aplicar limite de inatividade

**Relacionado:** RN-11

O agente deve utilizar o limite de inatividade configurado pelo gestor para determinar a mudança entre os estados:

```text id="zxfdn6"
Ativo
  ↓
limite sem interação
  ↓
Inativo
```

---

### RF-16 — Exibir estado do monitoramento

**Relacionado:** RN-20

Enquanto uma task estiver ativa, o agente deve permitir que o colaborador visualize:

- task atual;
- estado do monitoramento;
- serviços monitorados;
- estado Ativo/Inativo.

---

### RF-17 — Atualizar alteração dos serviços da task

**Relacionado:** RN-15

Caso o gestor altere os serviços monitorados de uma task em execução, o agente deve informar o colaborador sobre a alteração antes de aplicar o novo escopo.

O novo conjunto de serviços somente deve ser utilizado após a apresentação das novas condições.

---

# 4. Armazenamento e Sincronização

### RF-18 — Armazenar registros localmente

O agente deve manter localmente os registros produzidos durante o monitoramento até que possam ser enviados ao servidor.

---

### RF-19 — Sincronizar registros

O agente deve enviar ao backend os registros produzidos durante a execução das tasks.

Após confirmação de recebimento pelo servidor, o registro local poderá ser considerado sincronizado.

---

### RF-20 — Manter registros em caso de falha

Caso a comunicação com o servidor esteja indisponível, o agente deve manter localmente os registros ainda não sincronizados.

O monitoramento não deve depender de comunicação contínua com o servidor.

---

### RF-21 — Sincronizar registros pendentes

Quando a comunicação com o servidor for restabelecida, o agente deve tentar enviar os registros pendentes.

---

# 5. Gestão de Tasks

### RF-22 — Criar task

**Relacionado:** RN-02

O Dashboard deve permitir que o gestor crie uma task.

A task deve permitir informar:

- identificação;
- título;
- descrição;
- colaboradores;
- serviços ou aplicações monitorados.

---

### RF-23 — Editar task

**Relacionado:** RN-02, RN-15

O Dashboard deve permitir que o gestor altere as informações de uma task.

Alterações no conjunto de serviços monitorados devem respeitar as regras aplicáveis às tasks já em execução.

---

### RF-24 — Atribuir colaboradores à task

**Relacionado:** RN-02, RN-04

O Dashboard deve permitir que o gestor associe colaboradores às tasks.

Somente colaboradores associados devem receber a task em seu Agente Desktop.

---

### RF-25 — Configurar serviços monitorados

**Relacionado:** RN-03

O Dashboard deve permitir que o gestor informe quais serviços ou aplicações serão monitorados em cada task.

Cada serviço deve possuir uma identificação utilizável pelo agente durante a detecção.

Exemplo:

```text id="nbg6pa"
Google Chrome
Tag: chrome

Visual Studio Code
Tag: code

Terminal
Tag: terminal
```

---

# 6. Gestão da Equipe

### RF-26 — Gerenciar colaboradores

**Relacionado:** RN-19

O Dashboard deve permitir ao gestor consultar e organizar os colaboradores sob sua responsabilidade.

---

### RF-27 — Restringir colaboradores por gestor

**Relacionado:** RN-19

O sistema deve apresentar ao gestor somente os colaboradores pertencentes ao seu escopo de acesso.

---

### RF-28 — Exibir colaboradores Online

**Relacionado:** RN-12

O Dashboard deve permitir ao gestor visualizar quais colaboradores possuem uma task ativa.

Para cada colaborador Online, o sistema poderá apresentar:

- colaborador;
- task ativa;
- estado Ativo/Inativo;
- serviço monitorado atualmente, quando aplicável.

---

# 7. Jornada

### RF-29 — Configurar jornada

**Relacionado:** RN-16

O Dashboard deve permitir que o gestor configure a jornada dos colaboradores sob sua responsabilidade.

A configuração poderá conter:

- dias de trabalho;
- horário de entrada;
- horário de saída;
- intervalo;
- carga horária.

---

### RF-30 — Identificar possível hora extra

**Relacionado:** RN-17

O sistema deve comparar a execução da task com o horário previsto de término da jornada.

Quando a task permanecer ativa após esse horário, o sistema deve identificar o período posterior como **possível hora extra**.

---

### RF-31 — Alertar fim da jornada

O agente deve poder informar ao colaborador quando o término previsto da jornada estiver próximo ou tiver sido atingido.

Exemplo:

```text id="4pq4yu"
Seu expediente terminou.

A continuidade desta task poderá
ser registrada como possível hora extra.

[ Encerrar task ]
[ Continuar ]
```

---

# 8. Consulta de Dados

### RF-32 — Consultar próprios registros

**Relacionado:** RN-18

O sistema deve permitir que o colaborador consulte seus próprios registros disponibilizados pelo Time Tracker.

---

### RF-33 — Consultar atividade da equipe

**Relacionado:** RN-19

O Dashboard deve permitir ao gestor consultar os registros dos colaboradores sob sua responsabilidade.

A consulta poderá apresentar:

- task;
- serviço monitorado;
- duração;
- tempo ativo;
- tempo inativo;
- jornada;
- possível hora extra.

---

### RF-34 — Consultar registros por task

O Dashboard deve permitir ao gestor consultar informações agrupadas por task.

A consulta poderá apresentar:

- colaboradores participantes;
- serviços configurados;
- tempo registrado;
- atividade;
- inatividade.

---

# 9. Relatórios

### RF-35 — Gerar relatório individual

O sistema deve permitir gerar relatório de um colaborador autorizado contendo, conforme disponibilidade:

- jornada;
- tasks executadas;
- tempo por task;
- tempo ativo;
- tempo inativo;
- serviços monitorados;
- possível hora extra.

---

### RF-36 — Gerar relatório da equipe

O Dashboard deve permitir que o gestor gere relatórios sobre sua equipe.

O relatório poderá consolidar:

- colaboradores;
- tasks;
- tempo registrado;
- atividade;
- inatividade;
- jornada;
- possíveis horas extras.

---

### RF-37 — Gerar relatório por task

O Dashboard deve permitir gerar relatório específico de uma task.

O relatório poderá apresentar:

- colaboradores associados;
- serviços monitorados;
- tempo total registrado;
- atividade e inatividade.

---

### RF-38 — Exportar relatórios

O Dashboard deve permitir exportar relatórios nos formatos:

- CSV;
- PDF.

A exportação deve respeitar o mesmo escopo de acesso disponível ao gestor no sistema.

---

# 10. Resumo dos Requisitos Funcionais

```text id="52akx2"
GESTOR
  ↓
cria task
  ↓
atribui colaborador
  ↓
define serviços
  ↓
COLABORADOR
  ↓
faz login
  ↓
visualiza task
  ↓
visualiza condições
  ↓
confirma ciência
  ↓
inicia task
  ↓
AGENTE
  ↓
identifica aplicação
  ↓
compara com serviços da task
  ↓
registra período
  ↓
identifica Ativo/Inativo
  ↓
sincroniza
  ↓
BACKEND
  ↓
DASHBOARD
  ↓
relatórios
```

---

## 11. Relação RN → RF

| Regra | Principais requisitos relacionados |
| --- | --- |
| RN-01 — Monitoramento vinculado à task | RF-06, RF-07 |
| RN-02 — Configuração da task | RF-22, RF-23 |
| RN-03 — Serviços monitorados | RF-09, RF-10, RF-25 |
| RN-04 — Acesso às tasks | RF-03, RF-24 |
| RN-05 — Transparência | RF-04 |
| RN-06 — Ciência | RF-05, RF-06 |
| RN-07 — Registro da ciência | RF-05 |
| RN-08 — Limitação aos serviços | RF-09, RF-10, RF-11 |
| RN-09 — Informações registradas | RF-02, RF-11 |
| RN-10 — Atividade/Inatividade | RF-13, RF-14 |
| RN-11 — Limite de inatividade | RF-15 |
| RN-12 — Online | RF-06, RF-28 |
| RN-13 — Encerramento | RF-07 |
| RN-14 — Troca de task | RF-08 |
| RN-15 — Alteração dos serviços | RF-17, RF-23 |
| RN-16 — Jornada | RF-29 |
| RN-17 — Possível hora extra | RF-30, RF-31 |
| RN-18 — Acesso do colaborador | RF-32 |
| RN-19 — Acesso do gestor | RF-26, RF-27, RF-33 |
| RN-20 — Transparência durante a task | RF-16 |
| RN-21 — Finalidade e minimização | RF-10, RF-11 |
| RN-22 — Atividade não representa produtividade | RF-33, RF-35, RF-36 |