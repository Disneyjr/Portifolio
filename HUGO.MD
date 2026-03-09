# Guia do Projeto: Portfólio + Blog (Hugo)

Este repositório contém o código-fonte do portfólio pessoal e do blog integrados. A página inicial (Portfólio) é construída de forma estática com HTML e CSS nativos para máxima performance e controle visual, enquanto a seção do Blog é gerenciada pelo poderoso gerador de sites estáticos **Hugo**, utilizando o tema Ananke customizado.

## 🏗️ Estrutura de Diretórios

As principais pastas e arquivos para você gerenciar o projeto:

*   **`layouts/index.html`**: O coração do seu portfólio. O Hugo está configurado para priorizar este arquivo como a página principal `/`, mantendo a capa original do seu site intacta.
*   **`static/`**: Arquivos estáticos globais (CSS, JS, Imagens). Tudo que estiver aqui será copiado diretamente para a raiz do site. Por exemplo, `static/styles.css` (visual do portfólio) e `static/css/blog-custom.css` (visual extra do blog).
*   **`content/blog/`**: O diretório onde ficam os seus posts do blog escritos em Markdown (`.md`).
*   **`themes/ananke/`**: O tema base do blog.
*   **`hugo.yaml`**: Arquivo central de configuração do Hugo (baseURL, título, configuração do menu principal).
*   **`.gitignore`**: Arquivo que instrui o Git a ignorar pastas geradas automaticamente (como `public/` e `resources/`), mantendo o repositório limpo.
*   **`.github/workflows/pages.yml`**: A action do GitHub que orquestra o build e o deploy automaticamente no GitHub Pages em cada `push` na branch principal.

## 🚀 Desenvolvimento Local

Para rodar e testar o site no seu computador antes de publicar:

1. Abra o terminal na raiz do projeto (pasta `Portifolio`).
2. Inicie o servidor embutido do Hugo, habilitando a visualização de rascunhos com a flag `-D`:
   ```bash
   hugo server -D
   ```
3. Acesse as URLs no seu navegador:
   *   **Portfólio (Página Inicial):** [http://localhost:1313/](http://localhost:1313/)
   *   **Blog:** [http://localhost:1313/blog/](http://localhost:1313/blog/)

As alterações no código possuem _Live Reload_. Ao salvar qualquer arquivo (HTML, CSS ou Markdown), o navegador será recarregado automaticamente.

## ✍️ Gestão de Conteúdo

### Editando o Portfólio
Para atualizar suas informações pessoais, tecnologias ou adicionar novos projetos à capa principal:
1. Edite o conteúdo no arquivo `layouts/index.html`.
2. Para alterações de identidade visual ou layout da capa, modifique o `static/styles.css`.

### Criando um Novo Post no Blog
Recomenda-se utilizar a CLI do Hugo para facilitar a criação, pois ele já injeta o cabeçalho base (_front matter_) no arquivo:

```bash
hugo new blog/o-titulo-do-seu-post.md
```

1. O arquivo será criado em `content/blog/o-titulo-do-seu-post.md`.
2. Abra o arquivo em seu editor.
3. Altere o título se necessário. **Importante:** Mude a variável `draft` para `false` para que o post se torne público durante a publicação (`draft: false`).
4. Escreva o conteúdo do texto, estruturado usando Markdown, logo abaixo dos traços `---`.

## 🌐 Deploy / Publicação

O processo de hospedagem está simplificado e automatizado via CI/CD. Você não precisa se preocupar em rodar o comando `hugo` e cuidar de diretórios gerados.

Concluído o seu trabalho, basta enviar as alterações para o GitHub:

```bash
git add .
git commit -m "feat: Novo post no blog sobre Golang"
git push
```

Pronto! Ao receber o código, o GitHub Actions assumirá o comando, baixará a versão oficial do Hugo, realizará o _build_ completo e hospedará de forma transparente na sua URL de destino: `https://disneyjr.github.io/`.
