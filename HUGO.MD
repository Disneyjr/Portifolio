# Guia do Projeto: Portfólio + Blog Dual-Mode (Hugo)

Este repositório contém o código-fonte do portfólio pessoal e do blog técnico integrados. A página inicial (Portfólio) possui layout customizado conectado dinamicamente às últimas publicações do blog, enquanto a seção do Blog utiliza o gerador de sites estáticos **Hugo** com suporte ao modo **Dual-Mode (Humano + IA)**.

---

## 🏗️ Estrutura de Diretórios

* **`layouts/index.html`**: Página principal do Portfólio (`/`). Renderiza as seções profissionais e injeta automaticamente os 3 artigos mais recentes do blog.
* **`layouts/blog/`**:
  * `single.html`: Template de post individual com alternância **Original (Humano)**, **Versão IA** e **Comparação Lado a Lado** (`?view=ai` ou `?view=split`), além de badges de **Modelo LLM** e **Thinking Effort** e botão de copiar código.
  * `list.html` e `summary.html`: Listagem de artigos em grid responsivo com indicadores de tempo de leitura, tags e metadados da IA.
* **`layouts/_partials/`**: Cabeçalhos e meta tags de SEO (OpenGraph, Twitter Cards, Canonical URL e Favicons).
* **`static/`**: Arquivos estáticos globais (`styles.css` para o portfólio, `css/blog-custom.css` para o blog e `Imagens/`).
* **`content/blog/`**: Artigos do blog escritos em Markdown (`.md`).
* **`archetypes/default.md`**: Template padrão usado ao criar novos posts com `hugo new`.
* **`hugo.yaml`**: Configuração central do Hugo (SEO, Highlight de código Chroma `github-dark`, taxonomias e posts relacionados).
* **`.github/workflows/pages.yml`**: Pipeline CI/CD que compila e publica o site no GitHub Pages a cada push/merge na branch `main`.
* **`docs/TELEGRAM_BOT_INTEGRATION.md`**: Documentação completa da arquitetura do Bot do Telegram + Gemini API + GitHub PR para publicação automatizada.

---

## 🚀 Desenvolvimento Local

1. Abra o terminal na raiz do projeto.
2. Inicie o servidor do Hugo (incluindo rascunhos com `-D`):
   ```bash
   hugo server -D
   ```
3. Acesse no navegador:
   * **Portfólio (Home):** `http://localhost:1313/`
   * **Blog:** `http://localhost:1313/blog/`

---

## ✍️ Criando um Novo Post Dual-Mode (Humano + IA)

Crie o arquivo usando a CLI do Hugo:

```bash
hugo new blog/meu-novo-artigo.md
```

O arquivo gerado em `content/blog/meu-novo-artigo.md` utiliza o seguinte formato de **Front Matter**:

```yaml
---
title: "Arquitetura de Microserviços em Go"
date: "2026-11-08T20:00:00-03:00"
draft: false
description: "Resumo curto do artigo para SEO e cards de preview."
tags:
  - "Go"
  - "Microservices"
  - "Backend"
ai_meta:
  model: "gemini-2.5-pro"   # Modelo utilizado para gerar a versão IA
  effort: "high"            # Nível de esforço/raciocínio: low | medium | high
ai_content: |
  ## Versão Gerada pela LLM

  Texto completo em Markdown gerado pelo Gemini...
---

Aqui entra o seu texto original (humano), escrito em Markdown.
```

### Modos de Visualização por URL
* **Versão Original (Padrão):** `/blog/meu-novo-artigo/`
* **Link Direto para Versão IA:** `/blog/meu-novo-artigo/?view=ai`
* **Comparação Lado a Lado (Desktop):** `/blog/meu-novo-artigo/?view=split`

---

## 🤖 Publicação Automatizada via Telegram + Gemini + GitHub PR

O planejamento completo da integração para enviar textos pelo Telegram, gerar a versão expandida no Gemini (registrando `model` e `effort`), abrir o Pull Request e aprovar o merge pelo próprio chat está documentado em:

👉 **[`docs/TELEGRAM_BOT_INTEGRATION.md`](docs/TELEGRAM_BOT_INTEGRATION.md)**
