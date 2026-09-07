# EP-01 — Captura da atividade

**Projeto:** Time Tracker Open Source  
**Versão:** 1.0.0 (MVP)  
**Status:** ABERTO  
**Data:** Setembro de 2026

---

## 1. Objetivo

Implementar o mecanismo base de coleta do agente, conforme definido pela **CA-01**.

O sistema deve:
- Capturar nome do executável ativo no computador.
- Capturar título da janela ativa no computador.
- Capturar screenshot da tela no display ativo.
- Capturar o usuário do Windows logado.
- Capturar o hostname da máquina.

**Requisitos relacionados:** RF-01, RN-01, RNF-01.

**Critério de aceite:** `CA-01-captura_da_atividade`

---

## 2. US-01 — Capturar contexto da estação

**Como** Colaborador que está com o agente ativo e usando algum programa.

**quero** que a aplicação capture os metadados da janela ativa, identificação da máquina e um screenshot da tela no intervalo configurado,

**para que** o sistema registre automaticamente minha atividade e possibilite a análise correta da distribuição do tempo monitorado.

---

## 3. Tarefas

| ID | Tarefa | Resultado esperado |
| --- | --- | --- |
| TASK-01 [ ]| Implementar integração com Win32 API para obter o nome do processo em primeiro plano. | Executável ativo identificado (ex: `chrome.exe`). |
| TASK-02 [ ]| Obter o título da janela ativa atual através da API nativa do Windows. | Título da janela extraído em formato de texto. |
| TASK-03 [ ]| Desenvolver método para capturar o screenshot do display principal. | Imagem capturada com sucesso em memória ou arquivo temporário. |
| TASK-04 [ ]| Obter variáveis de ambiente para identificar Usuário Windows e Hostname. | Identificadores da máquina e do usuário resgatados. || 
| TASK-05 [ ]| Testar CA-01. | Comportamento verificado e dados validados. |

---

## 4. Antes de entregar

- [ ] TASKs implementadas.
- [ ] CA-01 testado.
- [ ] Requisitos relacionados respeitados.
- [ ] Evidência disponível.

