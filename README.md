# Agente de IA Agêntica para Gestão de RH - Chocolatetech

Este repositório contém o desenvolvimento de um ecossistema de Inteligência Artificial Agêntica criado durante a **Imersão Agentes de IA (Alura + Oracle)**. O objetivo do projeto é construir um assistente inteligente autônomo para triagem, consulta de políticas internas de RH e gestão de dados de funcionários da empresa fictícia Chocolatetech.

## 🚀 Status do Projeto: Em Desenvolvimento (Aula 2/3 concluída)

---

## 🛠️ Tecnologias e Ferramentas Utilizadas

* **n8n:** Orquestração de fluxos de automação e conexão de nós de IA.
* **MySQL:** Banco de dados relacional utilizado para persistência e gerenciamento das informações estruturadas dos funcionários.
* **Cohere:** Modelos de LLM para processamento de linguagem natural (*Cohere Chat Model*) e geração de vetores (*Cohere Embeddings*).
* **Vector Store:** Armazenamento vetorial dos dados não-estruturados para busca eficiente.
* **HTTP/API:** Requisições para consumo de dados brutos (*raw documents*).

---

## 🏗️ Arquitetura do Sistema (O que foi implementado)

O ecossistema no n8n foi expandido e agora opera unindo dados não-estruturados (documentos) e dados estruturados (banco de dados):

### 1. Pipeline de Ingestão de Dados (ETL Vetorial)
* Criação de um fluxo automático que realiza uma requisição HTTP para buscar documentos e manuais de políticas de RH brutos no GitHub.
* Tratamento dos dados com um *Data Loader* e conversão do texto em representações numéricas utilizando o modelo de *Embeddings* da Cohere.
* Armazenamento e indexação das informações em um banco de dados vetorial (*Simple Vector Store*).

* <img width="912" height="685" alt="Captura de tela 2026-06-15 232400" src="https://github.com/user-attachments/assets/e1718b55-dd3a-4892-acd1-f2e6eaee03c1" />

### 2. Integração com Banco de Dados Relacional (MySQL)
* Modelagem e população da tabela `funcionarios` contendo registros de ID, nome, e-mail, departamento, cargo, data de admissão, saldo de férias, banco de horas e regime de trabalho.
* Conexão do banco de dados ao **AI Agent** através de uma Tool customizada de seleção de linhas (`Select rows from a table in MySQL`).

* <img width="1204" height="698" alt="Captura de tela 2026-06-16 224655" src="https://github.com/user-attachments/assets/21fc48b4-7d0c-49dc-81ff-d07ac6693060" />

### 3. Fluxo do Agente Inteligente Multiferramentas (Multi-Tool Agent)
* Configuração do componente principal de **IA Agêntica (AI Agent)** integrado ao modelo de chat da Cohere e à **Memória de Conversação (Simple Memory)**.
* O agente agora é capaz de decidir autonomamente qual ferramenta usar de acordo com a dúvida do usuário:
  * Se o usuário pergunta sobre uma **política ou regra da empresa**, o agente usa a ferramenta do *Vector Store* (RAG).
  * Se o usuário pergunta sobre o **saldo de férias, cargo ou dados de um colaborador específico**, o agente consulta diretamente o banco de dados *MySQL*.
 
  * <img width="1036" height="626" alt="Captura de tela 2026-06-16 230624" src="https://github.com/user-attachments/assets/83688c8a-e6e6-4ef3-b195-b02065903e7d" />

---

## 📅 Próximos Passos

* [x] Integração do fluxo com um banco de dados relacional para consulta e manipulação de informações cadastrais dos funcionários em tempo real (Aula 2).
* [ ] Refinamento das tomadas de decisão autônomas do agente baseado em permissões, automações completas e regras de negócio.
