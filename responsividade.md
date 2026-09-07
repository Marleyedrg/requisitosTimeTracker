# Responsividade — Time Tracker

**Projeto:** Time Tracker Open Source
**Versão:** 1.0.0 (MVP)
**Status:** Parcial
**Data:** Setembro de 2026

## 1. Visão geral

O Time Tracker possui um dashboard web para gestores, desenvolvido com **React, Vite, Tailwind CSS e Recharts**.

O escopo atual não define dispositivos prioritários, navegadores suportados, largura mínima, breakpoints ou protótipos responsivos. Portanto, este documento registra os componentes conhecidos e as decisões de responsividade ainda necessárias.

> O agente desktop, destinado ao Windows 10/11 x64, não faz parte do escopo de responsividade web.

## 2. Breakpoints

Ainda não há breakpoints definidos para o dashboard.

| Faixa         | Largura   | Comportamento |
| ------------- | --------- | ------------- |
| Menor         | A definir | A definir     |
| Intermediária | A definir | A definir     |
| Maior         | A definir | A definir     |

Também devem ser definidos:

* base de medição: viewport ou contêiner;
* menor largura suportada;
* pontos de mudança de layout.

## 3. Comportamento por componente

| Componente               | Função                                                             | Comportamento responsivo |
| ------------------------ | ------------------------------------------------------------------ | ------------------------ |
| **Header**               | Seletor de data e status da API                                    | A definir                |
| **Cards de KPI**         | Horas monitoradas, colaboradores ativos e software mais utilizado  | A definir                |
| **Gráfico de rosca**     | Distribuição das atividades por categoria                          | A definir                |
| **Tabela em tempo real** | Exibe colaborador, máquina, aplicativo, janela, categoria e status | A definir                |
| **Timeline**             | Distribui as atividades ao longo do expediente                     | A definir                |
| **Exportação**           | Permite exportar relatórios em CSV e PDF                           | A definir                |

Componentes não especificados no escopo atual, como sidebar, modais e formulários, não são considerados requisitos até que sua necessidade seja confirmada.

## 4. Critérios de aceitação

Os critérios deverão ser validados após a definição dos breakpoints e implementação da interface.

A responsividade deverá considerar:

* ausência de transbordamento horizontal indesejado;
* legibilidade e acesso às informações em diferentes larguras;
* comportamento da tabela em telas menores;
* adaptação de cards, gráficos e timeline;
* preservação das ações disponíveis no dashboard;
* acessibilidade e navegação por teclado;
* navegadores e ambientes suportados.

**Verificação atual:** não realizada, pois ainda não há implementação ou evidências de testes disponíveis.

## 5. Protótipo

**Ferramenta:** A definir
**Telas contempladas:** painel de acompanhamento, configurações e relatório, conforme [sitemap.md](sitemap.md).
**Frames e estados:** A definir

## 6. Convenções de frontend

| Aspecto                       | Definição                            |
| ----------------------------- | ------------------------------------ |
| **Tecnologias**               | React, Vite, Tailwind CSS e Recharts |
| **Estratégia de estilos**     | Tailwind CSS                         |
| **Breakpoints**               | A definir                            |
| **Componentes reutilizáveis** | A definir                            |
| **Preservação de estado**     | A definir                            |
| **Estratégia de testes**      | A definir                            |

## 7. Referências cruzadas

| Referência               | Relação                             |
| ------------------------ | ----------------------------------- |
| [visao.md](visao.md)     | RF-14 a RF-16 e RNF-01 a RNF-07     |
| [sitemap.md](sitemap.md) | Telas e componentes do dashboard    |
| PDF, seção 8             | Componentes principais do dashboard |

## 8. Pendências

* Definir dispositivos e larguras prioritárias.
* Definir largura mínima suportada.
* Definir breakpoints e mudanças de layout.
* Definir comportamento responsivo dos componentes.
* Definir navegadores e ambientes suportados.
* Definir requisitos de acessibilidade e navegação por teclado.
* Criar ou definir protótipos responsivos.
* Definir estratégia e critérios de teste de responsividade.

**Última revisão:** 2026-09-06
