# Critérios de Aceite — Time Tracker

**Versão:** 1.0.0  
**Status:** Rascunho  
**Data:** Setembro de 2026

---

## CA-01 — Conta e associação

**Requisitos relacionados:** RF-01, RF-02, RF-03, RF-04, RF-05.

- **Dado que:** um usuário acessa o Time Tracker;
- **Quando:** realiza o fluxo inicial de acesso;
- **Então:**
  - o colaborador pode criar uma conta pelo Agente quando não existir usuário registrado na estação;
  - o gestor pode criar uma conta por e-mail pelo Dashboard;
  - o gestor pode gerar um código de associação de 6 dígitos;
  - o colaborador pode informar esse código;
  - após a associação, o colaborador passa a pertencer à equipe do gestor.

- [ ] Critério verificado e atendido.

---

## CA-02 — Tasks e início do monitoramento

**Requisitos relacionados:** RF-06, RF-07, RF-08, RF-09, RF-10.

- **Dado que:** o colaborador está associado a um gestor e possui uma task atribuída;
- **Quando:** seleciona uma task;
- **Então:**
  - somente tasks atribuídas ao colaborador são exibidas;
  - as condições de monitoramento são apresentadas;
  - os serviços monitorados são informados;
  - as informações registradas são informadas;
  - o colaborador confirma sua ciência antes do início;
  - o monitoramento começa somente após essa confirmação.

- [ ] Critério verificado e atendido.

---

## CA-03 — Monitoramento da atividade

**Requisitos relacionados:** RF-11, RF-12, RF-13, RF-14.

- **Dado que:** existe uma task ativa;
- **Quando:** o colaborador utiliza a estação;
- **Então:**
  - somente aplicações pertencentes ao escopo da task são registradas;
  - aplicações fora do escopo são ignoradas;
  - os períodos de utilização são registrados;
  - o registro pode conter colaborador, usuário Windows, task, serviço, início, término e duração;
  - o estado Ativo/Inativo é determinado pela interação com mouse ou teclado;
  - o conteúdo das interações não é coletado.

- [ ] Critério verificado e atendido.

---

## CA-04 — Estado e execução da task

**Requisitos relacionados:** RF-15, RF-16, RF-17.

- **Dado que:** o colaborador possui uma task em execução;
- **Quando:** consulta, encerra ou troca a task;
- **Então:**
  - o estado atual do monitoramento é exibido;
  - o gestor visualiza o colaborador como Online enquanto houver uma task ativa;
  - o colaborador não pode possuir duas tasks ativas simultaneamente;
  - ao encerrar a task, o monitoramento também é encerrado;
  - ao trocar de task, a anterior é finalizada antes do início da nova.

- [ ] Critério verificado e atendido.

---

## CA-05 — Armazenamento e sincronização

**Requisitos relacionados:** RF-18, RF-19.

- **Dado que:** registros são produzidos pelo agente;
- **Quando:** ocorre comunicação com o backend;
- **Então:**
  - os registros permanecem armazenados localmente até confirmação do servidor;
  - uma falha de comunicação não provoca perda dos registros;
  - registros pendentes permanecem disponíveis;
  - a sincronização é retomada quando a comunicação for restabelecida.

- [ ] Critério verificado e atendido.

---

## CA-06 — Jornada e inatividade

**Requisitos relacionados:** RF-20, RF-21, RF-22.

- **Dado que:** o gestor possui colaboradores associados;
- **Quando:** configura as condições de acompanhamento;
- **Então:**
  - pode definir a jornada do colaborador;
  - pode definir o limite de inatividade;
  - o agente utiliza o limite configurado para determinar o estado Inativo;
  - atividades após o término previsto da jornada podem ser identificadas como possível hora extra.

- [ ] Critério verificado e atendido.

---

## CA-07 — Consulta, relatórios e exportação

**Requisitos relacionados:** RF-23, RF-24, RF-25.

- **Dado que:** existem registros disponíveis;
- **Quando:** colaborador ou gestor consultam os dados;
- **Então:**
  - o colaborador visualiza somente seus próprios registros;
  - o gestor visualiza somente os colaboradores associados a ele;
  - o gestor pode consultar relatórios de tasks, atividade, jornada e possíveis horas extras;
  - a tela de relatórios possui um botão de exportação;
  - o gestor pode escolher entre CSV e PDF.

- [ ] Critério verificado e atendido.

---

## CA-08 — Histórico do colaborador

**Requisitos relacionados:** RF-26.

- **Dado que:** o agente já enviou registros ao sistema;
- **Quando:** o colaborador acessa o histórico pela System Tray;
- **Então:**
  - o histórico é apresentado em formato TXT;
  - somente informações efetivamente enviadas ao sistema são exibidas;
  - o histórico pertence ao próprio colaborador.

- [ ] Critério verificado e atendido.

---

## CA-09 — Privacidade e segurança

**Requisitos relacionados:** RNF aplicáveis.

- **Dado que:** o agente está executando uma task;
- **Quando:** informações são coletadas, armazenadas ou transmitidas;
- **Então:**
  - aplicações fora do escopo da task não são registradas;
  - teclas digitadas não são capturadas;
  - câmera, microfone e screenshots não fazem parte da coleta;
  - mouse e teclado são utilizados somente para identificar atividade/inatividade;
  - a comunicação com o servidor utiliza HTTPS;
  - as restrições de acesso aos dados são aplicadas pelo sistema.

- [ ] Critério verificado e atendido.

---

## CA-10 — Dashboard analítico

**Requisitos relacionados:** RF-27.

- **Dado que:** o gestor possui colaboradores associados e existem registros disponíveis;

- **Quando:** acessa o Dashboard e aplica os filtros disponíveis;

- **Então:**

  - são exibidos somente dados dos colaboradores associados ao gestor;

  - o Dashboard apresenta a quantidade de colaboradores Online e Offline;

  - o Dashboard apresenta a quantidade de tasks ativas;

  - são apresentados o tempo total Ativo e o tempo total Inativo;

  - é apresentado o tempo registrado por task;

  - é apresentada a comparação entre jornada planejada e jornada realizada;

  - possíveis horas extras são apresentadas como indicação;

  - o gestor pode visualizar a Activity Timeline dos colaboradores;

  - a Activity Timeline apresenta os períodos de utilização das aplicações monitoradas e os períodos de inatividade;

  - o gestor pode filtrar as informações por período, colaborador e task;

  - ao alterar um filtro, os indicadores e visualizações relacionados são atualizados;

  - aplicações fora do escopo da task não são apresentadas;

  - o Dashboard não apresenta métricas ou rankings de produtividade.

- [ ] Critério verificado e atendido.