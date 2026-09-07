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

> Rotas, autenticação e pontos de entrada não especificados permanecem como **A definir**.

## 1. Área pública

**A definir.**

O escopo atual não especifica telas públicas, autenticação ou recuperação de acesso.

## 2. Área do Gestor

**Acesso:** `[P1]` Gestor
**Ponto de entrada:** `2.1 Painel de acompanhamento`

| #   | Tela                           | Descrição                                                                                                                                                                                 | Épico/US      |
| --- | ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| 2.1 | **Painel de acompanhamento**   | Exibe status da API, seletor de data, KPIs de horas monitoradas, colaboradores ativos, software mais utilizado, visão em tempo real, distribuição por categoria e timeline de atividades. | EP-01 / US-02 |
| 2.2 | **Configurações do sistema**   | Permite consultar e atualizar intervalo de captura, tempo de inatividade e regras de categorização.                                                                                       | EP-01 / US-03 |
| 2.3 | **Relatório de produtividade** | Apresenta horas por colaborador e distribuição por categoria, com exportação em CSV e PDF.                                                                                                | EP-01 / US-02 |

## 3. Área do Colaborador

**Acesso:** `[P2]` Colaborador na estação Windows
**Ponto de entrada:** `3.1 Agente na System Tray`

| #   | Tela ou visualização      | Descrição                                                                                                                                | Épico/US      |
| --- | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| 3.1 | **Agente na System Tray** | Exibe o status `Online` ou `Offline` e executa, em segundo plano, a captura de atividades, sincronização e atualização de configurações. | EP-01 / US-01 |

> Não está definida uma área web específica para o Colaborador.

## 4. Área administrativa

**Não definida.**

O escopo atual não estabelece um perfil de Administrador separado do Gestor.

## 5. Fluxos transversais

| #   | Comportamento                    | Descrição                                                                                                                         | Épico/US              |
| --- | -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| 5.1 | **Atualização de configurações** | O agente consulta periodicamente as configurações do servidor e aplica os valores recebidos durante a execução.                   | EP-01 / US-01 / US-03 |
| 5.2 | **Sincronização offline**        | Em caso de falha de rede, o agente armazena os registros localmente em SQLite e os sincroniza após o restabelecimento da conexão. | EP-01 / US-01         |
| 5.3 | **Categorização automática**     | O backend classifica os registros por palavras-chave nas categorias Desenvolvimento, Design, Comunicação, Social e Outros.        | EP-01 / US-03         |
| 5.4 | **Exportação de relatórios**     | Os dados de produtividade podem ser exportados nos formatos CSV e PDF.                                                            | EP-01 / US-02         |

## 6. Pendências

* Definir autenticação e autorização.
* Definir rotas e navegação.
* Definir a existência e o escopo da área pública.
* Confirmar se **Relatório de produtividade** e **Configurações do sistema** serão telas independentes ou componentes do painel.
* Definir permissões detalhadas para Gestor e Colaborador.
* Confirmar a existência de uma área web para o Colaborador.
* Avaliar a necessidade de um perfil Administrador separado do Gestor.
* Definir o fluxo e os detalhes da exportação em CSV e PDF.

**Última revisão:** 2026-09-06
