# 📊 Mapeamento e Modelagem de Processos de Negócio (BPMN 2.0)

[![Notação BPMN 2.0](https://img.shields.io/badge/Standard-BPMN%202.0-blue.svg)](https://www.omg.org/bpmn/)
[![Ferramentas](https://img.shields.io/badge/Tools-Camunda%20%7C%20Bizagi%20%7C%20Draw.io-orange.svg)]()
[![Engenharia de Requisitos](https://img.shields.io/badge/Focus-Engenharia%20de%20Requisitos-green.svg)]()
[![Status](https://img.shields.io/badge/Status-Conclu%C3%ADdo-brightgreen.svg)]()

---

## 📌 Sobre o Projeto

Este repositório contém a documentação técnica, modelagem e diagramação de processos de negócio utilizando a notação **BPMN 2.0 (Business Process Model and Notation)**. 

O objetivo principal deste projeto é mapear o fluxo de trabalho operacional, identificar gargalos, automatizar etapas manuais e derivar **Requisitos Funcionais (RF)** e **Requisitos Não-Funcionais (RNF)** para o desenvolvimento do sistema **SGPD (Sistema de Gestão de Processos e Documentos)**.

A abordagem une a **vivência operacional prática** na área de logística e suprimentos à **Engenharia de Requisitos** e **Análise e Desenvolvimento de Sistemas**, garantindo que as soluções propostas resolvam dores reais de negócio.

---

## 🎯 Objetivos

- 🔄 **Mapeamento AS-IS**: Documentar os processos atuais com precisão, evidenciando pontos de ineficiência, falhas de comunicação e retrabalho.
- 🚀 **Modelagem TO-BE**: Projetar fluxos otimizados com integração de sistemas, redução de tempo de ciclo (lead time) e automação de tarefas repetitivas.
- 📑 **Levantamento de Requisitos**: Transformar cada raia (lane), evento e tarefa do diagrama em especificações claras para a equipe de desenvolvimento de software.
- 📐 **Padronização**: Aplicar rigorosamente as boas práticas e padrões da especificação OMG BPMN 2.0.

---

## 📐 Estrutura dos Diagramas Mapeados

O repositório está organizado nos seguintes fluxos de processos:

### 1. Fluxo Principal de Processamento e Triagem (SGPD)
- **Pool**: Organização / Sistema SGPD
- **Lanes**: 
  - `Operador`: Entrada de dados, triagem manual, conferência física/digital.
  - `Analista de Sistemas / Validador`: Análise de regras de negócio e validações de exceção.
  - `Sistema SGPD`: Execução de rotinas automáticas, validação de schemas, geração de notificações.
  - `Gestão`: Aprovações e acompanhamento de métricas (KPIs).

### 2. Visão Comparativa (AS-IS vs. TO-BE)

| Característica | Processo AS-IS (Atual) | Processo TO-BE (Otimizado) |
| :--- | :--- | :--- |
| **Entrada de Dados** | Manual em planilhas / papel | Formulários digitais validados e upload automatizado |
| **Validação de Exceções** | Comunicação via e-mail sem rastreabilidade | Gateways de decisão automáticos com alertas via sistema |
| **Notificações** | Checagem manual de pendências | Eventos de Mensagem/Tempo automatizados (Service Tasks) |
| **Rastreabilidade** | Baixa visibilidade do status das solicitações | Dashboards em tempo real com histórico completo |
| **Tempo Médio de Ciclo** | Elevado (24h - 48h) | Reduzido (< 2h para fluxos padrão) |

---

## 🛠️ Elementos BPMN 2.0 Utilizados

Para garantir expressividade técnica e clareza na comunicação entre áreas de negócio e TI, os diagramas utilizam:

- 🟢 **Eventos de Início (Start Events)**: Início por Mensagem, Início de Timer/Cronogramas.
- 🔴 **Eventos de Fim (End Events)**: Fim Normal, Evento de Erro e Cancelamento.
- 🟡 **Eventos Intermediários**: Timer (SLA de espera), Mensagem e Sinal.
- 🔷 **Gateways (Decisões)**:
  - `Exclusive (XOR)`: Roteamento condicional único.
  - `Parallel (AND)`: Tarefas paralelas de conferência e envio de alertas.
  - `Inclusive (OR)`: Caminhos alternativos simultâneos baseados em regras.
- ⚙️ **Tipos de Tarefas**:
  - `User Task`: Interação direta do usuário na interface do SGPD.
  - `Service Task`: Serviços de backend, APIs e integrações automáticas.
  - `Manual Task`: Atividades físicas operacionais.
  - `Script Task`: Scripts automatizados de processamento.

---

## 📂 Estrutura do Repositório

```text
.
├── docs/
│   ├── especificacao_requisitos.md    # Requisitos de software derivados do BPMN
│   └── dicionario_de_processos.md     # Glossário e descrição das tarefas
├── diagrams/
│   ├── bpmn/                           # Arquivos fonte em formato XML/BPMN 2.0 (.bpmn)
│   │   ├── sgpd_fluxo_principal.bpmn
│   │   ├── sgpd_processo_asis.bpmn
│   │   └── sgpd_processo_tobe.bpmn
│   └── exports/                        # Diagramas exportados para visualização rápida
│       ├── sgpd_fluxo_principal.png
│       ├── sgpd_fluxo_principal.svg
│       └── sgpd_fluxo_principal.pdf
└── README.md                           # Documentação principal do projeto
```

---

## 💡 Rastreabilidade de Requisitos (BPMN → Software)

A partir da modelagem dos fluxos, foram formalizados os seguintes requisitos de software para a implementação no sistema:

- **[RF-001] Cadastro e Triagem Digitais**: O sistema deve permitir a entrada estruturada de dados com validação de campos obrigatórios.
- **[RF-002] Roteamento Automático**: O sistema deve direcionar pendências para o papel correto (`Lane`) com base nas regras de negócio mapeadas nos *Gateways*.
- **[RF-003] Alertas de SLA**: O sistema deve disparar notificações automáticas quando um evento intermediário de tempo (*Timer Event*) atingir o limite estipulado.
- **[RNF-001] Padrão Interoperável**: Os diagramas devem ser mantidos no formato XML standard da OMG para permitir importação em motores de execução de processos (ex: Camunda Engine).

---

## 💻 Como Visualizar e Editar os Diagramas

1. **Camunda Modeler (Recomendado)**:
   - Baixe e instale o [Camunda Modeler](https://camunda.com/download/modeler/).
   - Abra os arquivos `.bpmn` localizados na pasta `diagrams/bpmn/`.

2. **Visual Studio Code**:
   - Utilize a extensão **BPMN-driven modeling** ou **BPMN Preview** para abrir os arquivos diretamente no editor.

3. **Navegador Web / Visualização Rápida**:
   - Os arquivos na pasta `diagrams/exports/` (`.svg` e `.png`) podem ser visualizados diretamente no GitHub ou em qualquer navegador.
   - Utilize o [bpmn.io/demo](https://demo.bpmn.io/) para importar e visualizar online sem instalação.

---

## 👨‍💻 Autor

**Juan Medeiros**  
Estudante de Análise e Desenvolvimento de Sistemas (ADS) | Engenharia de Requisitos & BPMN  
📍 Caxias do Sul - RS, Brasil  

- **LinkedIn**: [linkedin.com/in/juanmedeiros](https://www.linkedin.com)
- **GitHub**: [github.com/juanmedeiros](https://github.com)

---
*Projeto desenvolvido como parte do portfólio de Engenharia de Requisitos e Modelagem de Processos de Negócio.*
