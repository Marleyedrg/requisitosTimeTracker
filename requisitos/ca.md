# Critérios de Aceite — Time Tracker

**Versão:** 1.0.0  
**Status:** Rascunho  
**Data:** Setembro de 2026

---

## 1. Objetivo

Este documento define os **Critérios de Aceite (CA)** do Time Tracker.

Os critérios verificam os principais fluxos do sistema e indicam quando uma funcionalidade pode ser considerada atendida.

---

## 2. Critérios de Aceite

### CA-01 — Autenticação e acesso às tasks

**Requisitos relacionados:** RF-01, RF-02, RF-03

- **Dado que:** o Agente Desktop está em execução;
- **Quando:** o colaborador realizar login com credenciais válidas;
- **Então:**
  - o colaborador deve ser autenticado;
  - o usuário Windows deve ser identificado;
  - devem ser apresentadas somente as tasks atribuídas ao colaborador.

- [ ] Critério verificado e atendido.

---

### CA-02 — Início da task e transparência

**Requisitos relacionados:** RF-04, RF-05, RF-06, RF-16

- **Dado que:** o colaborador está autenticado e selecionou uma task;
- **Quando:** solicitar seu início;
- **Então:** o agente deve apresentar:
  - descrição da task;
  - serviços monitorados;
  - informações registradas;
  - informação sobre atividade/inatividade por mouse e teclado.

- **E:** o monitoramento somente deve iniciar após a confirmação de ciência.

- **E:** após o início:
  - a task deve ficar ativa;
  - o colaborador deve aparecer como Online;
  - as condições de monitoramento devem permanecer disponíveis para consulta.

- [ ] Critério verificado e atendido.

---

### CA-03 — Monitoramento da atividade

**Requisitos relacionados:** RF-09, RF-10, RF-11, RF-12, RF-13, RF-14, RF-15

- **Dado que:** existe uma task ativa;
- **Quando:** o agente identificar uma aplicação em execução;
- **Então:**
  - deve verificar se ela corresponde a um serviço definido na task;
  - aplicações fora da task devem ser ignoradas;
  - aplicações pertencentes à task devem gerar registro de utilização.

- **E:** o registro deve permitir identificar:
  - colaborador;
  - usuário Windows;
  - task;
  - serviço;
  - início;
  - término;
  - duração;
  - estado Ativo/Inativo.

- **E:** quando o tempo sem interação atingir o limite configurado, o colaborador deve ser marcado como Inativo.

- **E:** ao ocorrer nova interação, deve voltar para Ativo.

- [ ] Critério verificado e atendido.

---

### CA-04 — Encerramento e troca de task

**Requisitos relacionados:** RF-07, RF-08, RF-17

- **Dado que:** existe uma task ativa;
- **Quando:** o colaborador encerrá-la;
- **Então:**
  - o período atual deve ser finalizado;
  - o monitoramento deve ser encerrado;
  - o colaborador deve deixar de aparecer como Online.

- **E:** ao iniciar outra task:
  - a task anterior deve estar encerrada;
  - as condições da nova task devem ser apresentadas;
  - uma nova confirmação de ciência deve ocorrer.

- **E:** o colaborador não deve possuir duas tasks ativas simultaneamente.

- [ ] Critério verificado e atendido.

---

### CA-05 — Armazenamento e sincronização

**Requisitos relacionados:** RF-18, RF-19, RF-20, RF-21

- **Dado que:** o agente produziu registros de atividade;
- **Quando:** houver comunicação com o servidor;
- **Então:** os registros devem ser enviados e confirmados pelo backend.

- **Quando:** a comunicação estiver indisponível;
- **Então:**
  - os registros devem permanecer armazenados localmente;
  - o monitoramento deve continuar;
  - nenhuma informação pendente deve ser perdida.

- **E:** quando a comunicação retornar, os registros pendentes devem ser sincronizados.

- [ ] Critério verificado e atendido.

---

### CA-06 — Gestão de tasks

**Requisitos relacionados:** RF-22, RF-23, RF-24, RF-25

- **Dado que:** o gestor está autenticado no Dashboard;
- **Quando:** criar ou editar uma task;
- **Então:** deve conseguir definir:
  - título;
  - descrição;
  - colaboradores;
  - serviços ou aplicações monitorados.

- **E:** somente colaboradores associados devem visualizar a task no agente.

- **E:** alterações no escopo de uma task em execução devem ser informadas ao colaborador antes de serem aplicadas.

- [ ] Critério verificado e atendido.

---

### CA-07 — Jornada, equipe e relatórios

**Requisitos relacionados:** RF-26, RF-27, RF-28, RF-29, RF-30, RF-31, RF-32, RF-33, RF-34, RF-35, RF-36, RF-37, RF-38

- **Dado que:** existem colaboradores e registros disponíveis;
- **Quando:** o gestor acessar o Dashboard;
- **Então:** deve conseguir:
  - visualizar somente os colaboradores sob sua responsabilidade;
  - identificar colaboradores Online;
  - acompanhar tasks;
  - consultar atividade e inatividade;
  - consultar jornadas;
  - identificar possíveis horas extras;
  - consultar relatórios;
  - exportar relatórios em CSV e PDF.

- **E:** o colaborador deve conseguir consultar somente seus próprios registros.

- [ ] Critério verificado e atendido.

---

### CA-08 — Segurança, privacidade e operação

**Requisitos relacionados:** RNF-01 a RNF-15

- **Dado que:** o Time Tracker está em funcionamento;
- **Quando:** houver coleta, armazenamento, transmissão ou consulta de dados;
- **Então:**
  - o agente deve funcionar em Windows 10/11 x64;
  - a comunicação com a API deve utilizar HTTPS;
  - credenciais não devem ser armazenadas em texto puro;
  - o controle de acesso deve ser aplicado pelo backend;
  - o estado do monitoramento deve permanecer visível ao colaborador;
  - falhas de rede não devem provocar perda dos registros;
  - o agente deve operar sem degradação perceptível da estação;
  - somente informações necessárias ao monitoramento definido devem ser tratadas.

- [ ] Critério verificado e atendido.

---
