# Visão do Produto — Time Tracker

**Versão:** 1.0.0  
**Status:** Rascunho  
**Data:** Setembro de 2026

---

## 1. Visão Geral

O **Time Tracker** é uma solução open source corporativa para acompanhamento de **tasks, atividades e jornada de trabalho** em estações Windows.

O sistema possui dois perfis:

- **Colaborador:** executa tasks e acompanha seus próprios registros;
- **Gestor:** organiza a equipe, cria tasks, define o escopo de monitoramento e consulta relatórios.

O Time Tracker é composto por:

```text
Agente Desktop
      ↓
    HTTPS
      ↓
Backend / API
      ↓
PostgreSQL
      ↓
Dashboard PWA
```

O **Agente Desktop** é utilizado pelo colaborador.

O **Dashboard PWA** é utilizado pelo gestor.

---

## 2. Princípio do Monitoramento

A **task é a unidade central do monitoramento**.

Não deve existir monitoramento genérico ou permanente da estação.

Todo monitoramento deve:

- estar associado a uma task ativa;
- possuir finalidade definida;
- possuir aplicações previamente definidas;
- ser informado ao colaborador antes do início;
- limitar a coleta ao necessário para aquela atividade.

> **Nenhum monitoramento deve ocorrer sem uma task ativa e sem que o colaborador saiba previamente quais aplicações e informações serão monitoradas.**

---

## 3. Tasks

O gestor cria as tasks através do Dashboard.

Cada task deve definir:

- título e descrição;
- colaboradores associados;
- aplicações ou serviços monitorados;
- condições de monitoramento.

Exemplo:

```text
TASK-24 — Desenvolvimento do Dashboard

Colaboradores:
- Marley
- Ana

Aplicações monitoradas:
- Visual Studio Code
- Chrome
- Terminal

Dados:
- aplicação utilizada
- duração
- atividade/inatividade
```

Após realizar login no Agente Desktop, o colaborador visualiza somente as tasks às quais foi atribuído.

---

## 4. Transparência e Início da Task

Selecionar uma task não inicia imediatamente o monitoramento.

Antes do início, o colaborador deve visualizar:

- qual task será executada;
- finalidade da atividade;
- aplicações monitoradas;
- informações coletadas;
- uso de mouse e teclado para identificar atividade/inatividade;
- informações que não serão coletadas.

Exemplo:

```text
TASK-24 — Desenvolvimento do Dashboard

Monitorado:
✓ Visual Studio Code
✓ Chrome
✓ Terminal

Registrado:
✓ aplicação em utilização
✓ duração
✓ atividade/inatividade

Não coletamos:
✗ conteúdo digitado
✗ teclas pressionadas
✗ screenshots
✗ câmera
✗ microfone

[ Cancelar ]
[ Estou ciente e iniciar task ]
```

A confirmação representa a **ciência das condições apresentadas**, não devendo ser tratada pelo sistema como definição automática da base legal para o tratamento dos dados.

A organização responsável pelo uso da ferramenta deve definir a finalidade e a hipótese legal adequada para o tratamento.

O sistema deve registrar a versão das condições apresentadas ao colaborador no início da task.

---

## 5. Escopo da Coleta

Durante uma task, somente aplicações pertencentes ao seu escopo podem gerar informações detalhadas.

Exemplo:

```text
TASK-24

VS Code  → monitorado
Chrome   → monitorado
Spotify  → fora do escopo
Terminal → monitorado
```

Aplicações fora do escopo não devem gerar para o gestor informações como:

- nome da aplicação;
- título da janela;
- conteúdo;
- detalhes de utilização.

O sistema poderá apenas identificar que naquele período não houve atividade dentro das aplicações previstas pela task, quando necessário.

---

## 6. Informações Coletadas

Quando previstas pela task, poderão ser registrados:

- colaborador;
- task;
- sessão da task;
- aplicação autorizada;
- horário de início;
- horário de término;
- duração;
- atividade/inatividade;
- usuário Windows;
- hostname da estação.

O título da janela somente deverá ser coletado quando existir necessidade definida e previamente informada.

Mouse e teclado serão utilizados somente para determinar se houve interação recente.

```text
Houve interação?
      ↓
   sim / não
      ↓
Ativo / Inativo
```

O sistema não deve coletar:

- conteúdo das teclas digitadas;
- senhas;
- screenshots automáticos;
- áudio;
- câmera;
- conteúdo de mensagens;
- conteúdo de arquivos;
- histórico completo de navegação;
- dados detalhados de aplicações fora da task.

---

## 7. Registro e Sincronização

O agente deve registrar as atividades como **períodos**, evitando leituras repetidas quando nada mudou.

Exemplo:

```text
Visual Studio Code
10:00 → 10:32

Chrome
10:32 → 10:48

Visual Studio Code
10:48 → 11:02
```

Os registros devem ser persistidos localmente antes da transmissão.

```text
Atividade
   ↓
SQLite
   ↓
HTTPS
   ↓
API
   ↓
PostgreSQL
```

O SQLite atua como armazenamento temporário e fila de sincronização.

Caso exista falha de comunicação, os registros permanecem localmente e são enviados quando a conexão for restabelecida.

---

## 8. Estados e Jornada

O sistema deve diferenciar:

```text
Autenticação
↓
Autenticado / Não autenticado

Conexão
↓
Conectado / Sem conexão

Task
↓
Ativa / Sem task

Atividade
↓
Ativo / Inativo
```

Para o gestor, o colaborador será considerado **Online** quando possuir uma task efetivamente iniciada.

```text
Login
  ↓
Seleciona task
  ↓
Visualiza condições
  ↓
Confirma ciência
  ↓
Inicia task
  ↓
ONLINE
```

Ao encerrar a task, o monitoramento é encerrado e o colaborador passa a ser apresentado como Offline.

O gestor também poderá definir a jornada dos colaboradores, incluindo:

- dias de trabalho;
- entrada;
- saída;
- intervalo;
- carga horária.

Atividades realizadas após o término previsto poderão ser identificadas como **possível hora extra**.

---

## 9. Dashboard e Relatórios

O gestor utiliza o Dashboard PWA para:

- organizar sua equipe;
- criar e editar tasks;
- atribuir colaboradores;
- definir aplicações monitoradas;
- acompanhar colaboradores Online;
- consultar atividade e inatividade;
- consultar jornadas;
- consultar possíveis horas extras;
- gerar relatórios;
- exportar informações.

O gestor somente deve visualizar os colaboradores sob sua responsabilidade.

O colaborador poderá consultar seus próprios registros.

Os relatórios poderão incluir:

- jornada;
- tasks executadas;
- tempo por task;
- tempo ativo;
- tempo inativo;
- aplicações monitoradas;
- possíveis horas extras.

A exportação poderá ser realizada inicialmente em:

- CSV;
- PDF.

---

## 10. Privacidade, Segurança e Direção do Produto

O Time Tracker deve considerar proteção de dados desde a concepção.

Os principais princípios são:

### Transparência

O colaborador deve saber **quando, por que e sobre quais atividades está sendo monitorado**.

### Minimização

Somente informações necessárias à finalidade da task devem ser coletadas.

### Escopo Limitado

Aplicações fora da task não devem gerar informações detalhadas.

### Segurança

A comunicação entre Agente, API e Dashboard deve utilizar HTTPS.

Os dados armazenados localmente e no backend devem possuir proteção contra acesso não autorizado.

### Controle de Acesso

```text
Colaborador
↓
seus próprios dados

Gestor
↓
sua equipe
```

As restrições de acesso devem ser aplicadas pelo backend.

### Retenção

Os dados não devem permanecer armazenados indefinidamente sem necessidade.

A organização deverá definir políticas de retenção compatíveis com suas finalidades e obrigações.

### Rastreabilidade

Eventos importantes, como início da task, ciência das condições e alterações no escopo de monitoramento, devem possuir histórico.

### Atividade não significa produtividade

O Time Tracker registra **tempo, atividade, jornada e execução de tasks**.

Essas informações podem auxiliar análises, mas o sistema não deve concluir automaticamente que maior tempo de atividade representa maior produtividade.

---

## Fluxo Geral

```text
GESTOR
  ↓
cria task
  ↓
define colaboradores
  ↓
define aplicações
  ↓
disponibiliza task
  ↓
COLABORADOR
  ↓
faz login
  ↓
seleciona task
  ↓
visualiza condições
  ↓
confirma ciência
  ↓
inicia task
  ↓
ONLINE
  ↓
monitoramento limitado à task
  ↓
SQLite
  ↓
HTTPS / API
  ↓
PostgreSQL
  ↓
Dashboard
```

---

## Direção do Produto

O Time Tracker não deve evoluir para uma ferramenta de monitoramento indiscriminado do colaborador.

Sua finalidade é utilizar registros técnicos necessários e previamente informados para apoiar:

- organização do trabalho;
- acompanhamento de tasks;
- acompanhamento da jornada;
- análise de atividade;
- geração de relatórios;

mantendo limites claros sobre **o que é monitorado, quando o monitoramento ocorre e quem pode acessar os dados**.