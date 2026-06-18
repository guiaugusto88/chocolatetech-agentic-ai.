# Agente de IA Agêntica para Gestão de RH - Chocolatetech

Este repositório contém o desenvolvimento de um ecossistema de Inteligência Artificial Agêntica completo, criado durante a **Imersão Agentes de IA (Alura + Oracle)**. O objective do projeto é construir um assistente inteligente autônomo para triagem, consulta de políticas internas de RH e gerenciamento de dados de colaboradores da empresa fictícia Chocolatetech, operando em tempo real integrado ao Telegram.

## 🚀 Status do Projeto: Concluído ✨

---

## 🛠️ Tecnologias e Ferramentas Utilizadas

* **n8n:** Orquestração de fluxos de automação e conexão de nós de IA.
* **Telegram API:** Interface de usuário e canal de produção para interação direta com o agente.
* **MySQL:** Banco de dados relacional para persistência e gerenciamento das informações estruturadas dos funcionários.
* **Cohere:** Modelos de LLM para processamento de linguagem natural (*Cohere Chat Model*) e geração de vetores (*Cohere Embeddings*).
* **Vector Store:** Armazenamento vetorial de dados não-estruturados para a arquitetura RAG.
* **HTTP/API:** Requisições para consumo de documentos corporativos brutos.

---

## 🏗️ Arquitetura do Sistema (Ecossistema Completo)

O ecossistema final foi implantado com sucesso, unindo o processamento de dados não-estruturados, consultas relacionais e disponibilização para o usuário final:

### 1. Ingestão e Processamento (ETL Vetorial)
* Fluxo automatizado via requisições HTTP para ler manuais brutos de RH.
* Divisão e conversão de texto em vetores numéricos através do modelo de *Embeddings* da Cohere, indexados no *Simple Vector Store*.

### 2. Camada Relacional (MySQL)
* Banco de dados estruturado com a tabela `funcionarios` populada, permitindo buscas dinâmicas de dados sensíveis (cargo, saldo de férias, banco de horas, etc.).
* Conexão direta ao agente central como uma ferramenta analítica automatizada.

### 3. Disponibilização em Produção (Telegram Bot)
* Integração de um nó de Webhook configurado com a API do Telegram (`Telegram Trigger`) para escutar os comandos enviados pelos usuários.
* O **AI Agent** orquestra o fluxo de ponta a ponta: recebe a mensagem, retém o histórico na **Simple Memory** e escolhe autonomamente se vai consultar os manuais (RAG) ou buscar as linhas da tabela no **MySQL** para responder através do nó de envio de mensagens do Telegram.

* <img width="1064" height="605" alt="Captura de tela 2026-06-18 075105" src="https://github.com/user-attachments/assets/fcaabf6f-e94c-4b99-b962-04345b9c4c93" />

---

## 📱 Demonstração Prática (Produção)

O agente foi validado com sucesso simulando um cenário corporativo. No teste abaixo, o usuário interage diretamente pelo aplicativo do Telegram com o assistente, que aciona o raciocínio lógico e a arquitetura RAG para retornar diretrizes sobre políticas internas e banco de horas sem alucinar:

<img width="1064" height="605" alt="Captura de tela 2026-06-18 075105" src="https://github.com/user-attachments/assets/424ea4b3-51c5-4373-9fbd-5820e429ff06" />

---

## 🏁 Entrega Final e Certificação

<img width="879" height="613" alt="Captura de tela 2026-06-17 233749" src="https://github.com/user-attachments/assets/9b72e398-0609-4579-9a6c-60bc75b6f2d9" />

* [x] Ingestão de dados e arquitetura básica de RAG (Aula 1).
* [x] Integração com banco de dados MySQL para consultas estruturadas (Aula 2).
* [x] Configuração de Webhook e Deploy completo do bot integrado à API do Telegram (Aula 3).
