# Requisitos Não Funcionais — Time Tracker

**Versão:** 1.0.0  
**Status:** Rascunho  
**Data:** Setembro de 2026

---

## 1. Objetivo

Este documento define os **Requisitos Não Funcionais (RNF)** do Time Tracker.

Os RNFs estabelecem características de qualidade, segurança, desempenho, compatibilidade e operação que devem ser respeitadas pelo sistema.

---

## 2. Requisitos Não Funcionais

### RNF-01 — Compatibilidade do Agente

O Agente Desktop deve ser compatível com:

- Windows 10 x64;
- Windows 11 x64.

A coleta de informações da aplicação em execução e da atividade do usuário deve funcionar nessas plataformas.

---

### RNF-02 — Desempenho do Agente

O Agente Desktop deve operar com baixo impacto sobre os recursos da estação do colaborador.

O monitoramento não deve provocar degradação perceptível no uso normal da máquina.

Devem ser avaliados durante os testes:

- consumo de CPU;
- consumo de memória;
- utilização de disco;
- impacto provocado pela coleta e sincronização.

Os limites quantitativos deverão ser definidos após medições do agente em ambiente de teste.

---

### RNF-03 — Comunicação Segura

Toda comunicação entre os componentes do Time Tracker deve ocorrer através de conexão segura.

```text
Agente ──HTTPS──→ API

Dashboard ──HTTPS──→ API
```

Não deve ser utilizada comunicação HTTP sem proteção para transmissão de dados do sistema.

---

### RNF-04 — Proteção de Credenciais e Sessões

Credenciais de autenticação não devem ser armazenadas em texto puro.

Tokens e informações utilizadas para manutenção de sessão devem ser armazenados e transmitidos de forma segura.

Informações sensíveis de autenticação também não devem ser registradas indevidamente em logs.

---

### RNF-05 — Controle de Acesso

O controle de acesso aos dados deve ser aplicado pelo backend.

A interface não deve ser considerada o único mecanismo de restrição.

O sistema deve garantir que:

```text
COLABORADOR
     ↓
seus próprios dados

GESTOR
     ↓
colaboradores sob sua responsabilidade
```

Requisições sem autorização adequada devem ser rejeitadas.

---

### RNF-06 — Privacidade e Minimização

O sistema deve tratar somente as informações necessárias para as funcionalidades previstas.

O monitoramento não deve capturar o conteúdo das interações do colaborador.

A utilização de mouse e teclado deve limitar-se à identificação de:

```text
Ativo / Inativo
```

sem armazenar conteúdo digitado ou detalhes das interações.

A implementação deve seguir os princípios de finalidade, necessidade, minimização e transparência definidos para o produto.

---

### RNF-07 — Transparência do Monitoramento

O Agente Desktop deve manter o estado do monitoramento visível ao colaborador enquanto estiver em execução.

O colaborador deve conseguir identificar facilmente:

- se existe uma task ativa;
- se o monitoramento está ativo;
- quais serviços estão sendo monitorados;
- seu estado de atividade/inatividade.

O agente deve permanecer acessível através da **System Tray** enquanto estiver em execução.

---

### RNF-08 — Resiliência a Falhas de Rede

Falhas temporárias de comunicação com o backend não devem causar perda dos registros já produzidos pelo agente.

O agente deve continuar funcionando localmente quando a API estiver temporariamente indisponível.

Os registros pendentes devem permanecer disponíveis para sincronização posterior.

---

### RNF-09 — Integridade da Sincronização

A sincronização deve preservar a integridade dos registros enviados pelo agente.

O mecanismo de sincronização deve evitar, quando possível:

- perda de registros;
- envio incorreto;
- inconsistência entre registros locais e servidor;
- duplicação causada por novas tentativas de envio.

A estratégia específica de identificação e idempotência deverá ser definida na arquitetura.

---

### RNF-10 — Proteção do Armazenamento Local

Os registros armazenados localmente pelo agente devem possuir acesso restrito ao contexto necessário para execução do Time Tracker.

O armazenamento local não deve conter:

- senhas;
- credenciais em texto puro;
- tokens expostos em logs.

Os registros locais sincronizados devem ser tratados conforme a política de armazenamento definida para o agente.

---

### RNF-11 — Rastreabilidade

Eventos relevantes para auditoria devem possuir informações suficientes para identificar:

```text
quem
↓
realizou o evento
↓
quando
```

Devem possuir rastreabilidade, quando aplicável:

- início de task;
- encerramento de task;
- confirmação de ciência;
- alteração do escopo de monitoramento;
- alterações realizadas pelo gestor.

---

### RNF-12 — Usabilidade

As principais ações do colaborador no agente devem possuir apresentação simples e compreensível.

O início de uma task deve permitir que o colaborador identifique facilmente:

- qual task está iniciando;
- quais serviços serão monitorados;
- quais informações serão registradas.

Mensagens relacionadas ao monitoramento devem utilizar linguagem clara e evitar termos técnicos desnecessários.

---

### RNF-13 — Disponibilidade da Documentação da API

O backend deve disponibilizar documentação das operações expostas pela API.

A documentação deve permitir à equipe de desenvolvimento identificar:

- endpoints;
- parâmetros;
- estruturas enviadas e recebidas;
- códigos de resposta.

Quando utilizado FastAPI, a documentação poderá ser disponibilizada através do Swagger/OpenAPI.

---

### RNF-14 — Implantação Reproduzível

Os componentes de servidor do Time Tracker devem possuir uma forma reproduzível de inicialização do ambiente.

A infraestrutura deverá permitir inicialização dos serviços através do Docker Compose conforme definido na arquitetura do projeto.

---

### RNF-15 — Manutenibilidade

O sistema deve possuir separação clara entre seus principais componentes:

```text
Agente Desktop
      │
Backend / API
      │
Dashboard
```

Alterações em um componente devem evitar dependência direta desnecessária da implementação interna dos demais componentes.

Os contratos de comunicação devem ser documentados.

---

## 3. Resumo

| ID | Requisito | Categoria |
| --- | --- | --- |
| RNF-01 | Compatibilidade Windows 10/11 x64 | Compatibilidade |
| RNF-02 | Baixo impacto de recursos | Desempenho |
| RNF-03 | Comunicação via HTTPS | Segurança |
| RNF-04 | Proteção de credenciais e sessões | Segurança |
| RNF-05 | Controle de acesso no backend | Segurança |
| RNF-06 | Privacidade e minimização | Privacidade |
| RNF-07 | Monitoramento visível ao colaborador | Usabilidade / Transparência |
| RNF-08 | Operação durante falha de rede | Resiliência |
| RNF-09 | Integridade da sincronização | Confiabilidade |
| RNF-10 | Proteção do armazenamento local | Segurança |
| RNF-11 | Rastreabilidade | Auditoria |
| RNF-12 | Clareza da interface | Usabilidade |
| RNF-13 | Documentação da API | Manutenibilidade |
| RNF-14 | Implantação reproduzível | Portabilidade |
| RNF-15 | Separação entre componentes | Manutenibilidade |

---

## 4. Pontos Ainda Não Definidos

Os seguintes valores não devem ser definidos arbitrariamente e precisam ser validados durante o desenvolvimento ou testes:

- limite máximo aceitável de CPU;
- limite máximo aceitável de memória;
- tempo máximo aceitável de sincronização;
- período de retenção dos dados;
- estratégia exata contra duplicação durante sincronização;
- tempo máximo de resposta da API;
- navegadores oficialmente suportados pelo Dashboard PWA.

Enquanto esses valores não forem definidos e validados, devem permanecer registrados como **pendências**, evitando transformar estimativas em requisitos oficiais.