# 📚 RAG Automatizado com n8n + Google Drive + Supabase + OpenAI

Este projeto implementa um fluxo RAG (Retrieval-Augmented Generation) utilizando **n8n** para automatizar a ingestão de arquivos do **Google Drive**, gerar embeddings com **OpenAI**, armazenar vetores no **Supabase** e permitir consultas contextuais com base nos documentos.

---

## 🧠 Visão Geral do Projeto

Sempre que um arquivo for **criado ou atualizado** em uma pasta do Google Drive, este workflow realiza automaticamente:

1. 🗑️ **Remove embeddings antigos** (caso existam).
2. 📥 **Baixa o novo arquivo** do Google Drive.
3. 🧾 **Extrai o conteúdo textual** do arquivo.
4. 🧩 **Divide o texto em blocos pequenos**.
5. 🤖 **Gera embeddings** com OpenAI.
6. 🚀 **Armazena os vetores** no Supabase (pgvector).

> O objetivo é manter os dados sempre atualizados para sistemas que fazem consultas contextuais com base em documentos.

---

## 📌 Stack Utilizada

| Ferramenta            | Finalidade                            |
|-----------------------|----------------------------------------|
| [n8n](https://n8n.io) | Orquestração dos workflows             |
| Google Drive          | Fonte dos documentos monitorados       |
| Supabase + pgvector   | Armazenamento de embeddings vetoriais  |
| OpenAI API            | Geração de embeddings semânticos       |

---

## 🔁 Fluxo do Workflow

![Captura de tela 2025-04-21 122654](https://github.com/user-attachments/assets/640c1d2f-83ef-4bf6-810e-b7c74b3a2f0e)

---

## ⚙️ Etapas do Workflow

1. **Triggers:**
   - `Was file created?`
   - `Was file updated?`

2. **Pipeline:**
   - `Set file_id`: define o ID do arquivo.
   - `Delete Row`: remove registros antigos.
   - `Google Drive - Download`: baixa o arquivo atualizado.
   - `Extract From File`: extrai o texto do arquivo.
   - `Recursive Text Splitter`: divide o conteúdo em pedaços.
   - `OpenAI Embeddings`: gera vetores semânticos.
   - `Supabase Vector Store`: salva os embeddings no banco vetorial.

---

## ✅ Casos de Uso

- Chatbots corporativos com base em documentos internos.
- Ferramentas de pesquisa inteligente em conteúdos empresariais.
- Assistentes virtuais para suporte técnico e RH.
- FAQ dinâmico e contextualizado.

---

## 🚀 Como Usar

1. Clone o repositório.
2. Importe o arquivo `.json` do workflow no seu ambiente n8n.
3. Configure suas credenciais:
   - Google Drive (OAuth)
   - Supabase (URL + Key)
   - OpenAI API Key
4. Defina a pasta que será monitorada no Google Drive.
5. Execute o workflow e monitore automaticamente.

---

## 📂 Arquivo do Workflow

> (Adicione aqui o arquivo exportado do n8n em `.json` para facilitar a importação)



## ✨ Autor

Desenvolvido por **Lucas Oliveira**  
[@23.lucasdoliveira](mailto:23.lucasdoliveira@gmail.com)

---

