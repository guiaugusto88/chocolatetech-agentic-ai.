# chocolatetech-agentic-ai.
Ecossistema de IA Agêntica com arquitetura RAG, desenvolvido com n8n e Cohere para automação de consultas de políticas de RH da Chocolatetech (Imersão Alura + Oracle).

# Agente de IA Agêntica para Gestão de RH - Chocolatetech

Este repositório contém o desenvolvimento de um ecossistema de Inteligência Artificial Agêntica criado durante a **Imersão Agentes de IA (Alura + Oracle)**. O objetivo do projeto é construir um assistente inteligente autônomo para triagem, consulta de políticas internas de RH e gestão de dados de funcionários da empresa fictícia Chocolatetech.

## 🚀 Status do Projeto: Em Desenvolvimento (Aula 1/3 concluída)

---

## 🛠️ Tecnologias e Ferramentas Utilizadas

* **n8n:** Orquestração de fluxos de automação e conexão de nós de IA.
* **Cohere:** Modelos de LLM para processamento de linguagem natural (*Cohere Chat Model*) e geração de vetores (*Cohere Embeddings*).
* **Vector Store:** Armazenamento vetorial dos dados não-estruturados para busca eficiente.
* **HTTP/API:** Requisições para consumo de dados brutos (*raw documents*).

---

## 🏗️ Arquitetura do Sistema (O que foi implementado até agora)

Na primeira etapa do projeto, estruturei duas frentes principais de arquitetura de dados dentro do n8n:

### 1. Pipeline de Ingestão de Dados (ETL Vetorial)
* Criação de um fluxo automático que realiza uma requisição HTTP para buscar documentos e manuais de políticas de RH brutos no GitHub.
* Tratamento dos dados com um *Data Loader* e conversão do texto em representações numéricas utilizando o modelo de *Embeddings* da Cohere.
* Armazenamento e indexação das informações em um banco de dados vetorial (*Simple Vector Store*).

* <img width="1093" height="523" alt="Captura de tela 2026-06-15 232421" src="https://github.com/user-attachments/assets/9607f60f-4f4a-43e7-b563-da1af6d8160c" />

### 2. Fluxo do Agente Inteligente com RAG
* Configuração do componente principal de **IA Agêntica (AI Agent)** integrado ao modelo de chat da Cohere.
* Implementação de **Memória de Conversação (Simple Memory)** para que o agente retenha o contexto do diálogo com o usuário.
* Conexão do banco de dados vetorial como uma **Tool (Ferramenta)** do agente. Isso ativa a arquitetura **RAG (Retrieval-Augmented Generation)**, garantindo que o agente responda com base estritamente nos manuais da empresa, eliminando alucinações.

* <img width="912" height="685" alt="Captura de tela 2026-06-15 232400" src="https://github.com/user-attachments/assets/a056127f-3eb3-42f9-8049-88864c5988aa" />

---

## 📅 Próximos Passos

* [ ] Integração do fluxo com um banco de dados relacional para consulta e manipulação de informações cadastrais dos funcionários em tempo real (Aula 2).
* [ ] Refinamento das tomadas de decisão autônomas do agente baseado em permissões e regras de negócio.
