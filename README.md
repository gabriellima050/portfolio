# Portfólio · Gabriel Lima Procópio

Currículo online interativo com projetos que podem ser testados direto no navegador.
É um site estático (HTML, CSS e JavaScript puros): não precisa de build, Node ou framework.

## Estrutura

```
index.html              → estrutura da página
assets/css/style.css    → visual (cores e fontes ficam no bloco :root, no topo)
assets/js/data.js       → TODO o conteúdo editável: projetos, trajetória, stack, certificados
assets/js/demos.js      → as mini-demos de cada projeto
assets/js/main.js       → montagem da página (console, cards, linha do tempo)
assets/img/foto.jpg     → foto de perfil
assets/img/favicon.svg  → ícone da aba
.nojekyll               → evita que o GitHub Pages processe o site com Jekyll
```

## Editar o conteúdo

Abra `assets/js/data.js`. Cada seção está comentada:

- `SITE.projetos`: título, descrição, stack, “o que foi construído”, resultado, nota de anonimização.
  - `vis: 'pub'` com `repo` mostra o link para o GitHub; `vis: 'priv'` fica como privado/anonimizado.
  - `feat: 1` deixa o card mais largo.
  - A demo de cada card fica em `assets/js/demos.js`, na função `DEMOS.<id>` com o mesmo `id` do projeto.
- `SITE.trajetoria`: empresas e cargos. `s` e `e` são anos decimais (ago/2025 ≈ 2025.58). `e: null` = emprego atual.
- `SITE.stack` e `SITE.certificados`: listas simples.
- Textos do topo, números de impacto e recomendações ficam direto no `index.html`.

## Testar no computador

Basta abrir o `index.html` no navegador. Se preferir um servidor local:

```bash
python -m http.server 8000
# abra http://localhost:8000
```

## Publicar no GitHub Pages

1. Crie um repositório no GitHub (ex.: `portfolio` ou `gabriellima050.github.io`).
2. Envie estes arquivos para a raiz do repositório:
   ```bash
   git init
   git add .
   git commit -m "Portfólio"
   git branch -M main
   git remote add origin https://github.com/gabriellima050/portfolio.git
   git push -u origin main
   ```
3. No repositório: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, pasta `/ (root)`. Salve.
4. Em 1 ou 2 minutos o site fica em `https://gabriellima050.github.io/portfolio/`.
   Se o repositório se chamar `gabriellima050.github.io`, o endereço fica `https://gabriellima050.github.io/`.

## Publicar na Vercel

1. Suba o repositório no GitHub (passos 1 e 2 acima).
2. Em [vercel.com/new](https://vercel.com/new), importe o repositório.
3. Framework Preset: **Other**. Deixe Build Command e Output Directory vazios.
4. Clique em **Deploy**. Cada novo `git push` publica de novo automaticamente.

Também dá para publicar sem GitHub: `npx vercel` dentro desta pasta.

## Depois de publicar

- Troque o `og:image` no `index.html` pelo endereço completo da foto
  (ex.: `https://seu-site/assets/img/foto.jpg`) para a prévia aparecer bonita ao compartilhar o link no LinkedIn e no WhatsApp.
- Domínio próprio: em GitHub Pages use **Settings → Pages → Custom domain**; na Vercel, **Project → Settings → Domains**.

## Privacidade dos projetos

Os projetos privados aparecem sem nome de empresa, sem regra de negócio e com dados fictícios.
Revise os textos de `SITE.projetos` antes de publicar.
