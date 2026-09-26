# CLAUDE.md — MOBILIINTELLIGENTI

Site gerado pelo **SF (Site Factory)** em 15/04/2026. Migrado para o modelo Cloudflare + Supabase em 25/09/2026.

## Contexto do Site

**Nome:** MOBILIINTELLIGENTI
**Nicho:** Casa e Decoração
**Keywords:** Alphaville foi o local escolhido para receber o primeiro Showroom da Mobili
**Paleta de cores:** ocean | **Fonte:** outfit

Alphaville foi o local escolhido para receber o primeiro Showroom da Mobili Intelligenti, uma verdadeira inovação em mobiliário que vem para solucionar o problema dos espaços compactos. A correria do dia a dia faz com que as pessoas escolham cada vez mais morar em espaços reduzidos, como apartamentos pequenos e de fácil manutenção, onde móveis funcionais são peças-chave para atender estas necessidades. Seguindo as tendências norte-americana e europeia, a Mobili Intelligenti traz, com exclusividade para o Brasil, móveis transformáveis. Importados de várias partes do mundo, os móveis com design moderno e de alta qualidade se transformam em outros móveis em questão de segundos, graças à tecnologia utilizada nas diversas ferragens. Com este lançamento exclusivo, a Mobili Intelligenti se instala no país com três palavras de ordem: versatilidade, design e qualidade. Showroom: Alameda Araguaia, 122 — G7 — Alphaville/São Paulo.

## Componentes visuais usados

| Seção | Variante |
|-------|----------|
| Header | Header-D |
| Hero | Hero-H |
| Features | Features-G |
| About Section | About-B |
| Posts | Posts-H |
| Footer | Footer-G |
| Página Sobre | Sobre-G |
| Página Contato | Contato-C |

## Estrutura do projeto

```
src/
  sections/        # Layout escolhido pelo SF — Header, Hero, Features, About, Posts, Footer, Sobre, Contato
  data/            # JSONs com todo o conteúdo editável
  lib/             # supabase.ts (cliente) e posts.ts (getPosts/getPostBySlug)
  components/      # Seo.astro (meta tags + JSON-LD)
  pages/           # Rotas Astro (index, sobre, contato, blog, privacidade, termos, [...slug])
  layouts/         # BaseLayout com fonte e cores dinâmicas
  styles/          # global.css com variáveis CSS de cor
public/
  images/          # hero.jpg, about.jpg, sobre.jpg
```

## O que editar

### Textos e conteúdo
- **`src/data/home.json`** — hero (título, subtítulo, botão), features (título, items), about section (título, desc, stats), posts
- **`src/data/sobre.json`** — conteúdo completo da página Sobre (hero, texto, stats)
- **`src/data/contato.json`** — título, subtítulo, email, tempo de resposta
- **`src/data/siteConfig.json`** — nome, slug, email, redes sociais, menu (título/descrição/OG/JSON-LD derivam daqui)

### Imagens
Imagens já estão em `public/images/` (via Pexels). Para substituir, mantenha os mesmos nomes de arquivo:
- `hero.jpg` — imagem de fundo do Hero (e og:image padrão)
- `about.jpg` — imagem da seção About (home)
- `sobre.jpg` — imagem de fundo da página Sobre

### Posts do blog
Os posts NÃO ficam mais em markdown local. São carregados do Supabase (tabela `network_posts`, filtrados por `domain = mobiliintelligenti.com.br`).
- `src/lib/posts.ts` — `getPosts()` e `getPostBySlug()`; `formatContentToHtml()` converte markdown → HTML.
- Sem painel admin. Novos posts/posts editados entram pela plataforma 8links e publicam automaticamente (via Git/CF).

### Cores
Variáveis em `src/styles/global.css`: `--color-primary`, `--color-accent`, `--color-dark`.

## SEO

- `src/components/Seo.astro` injetado pelo `BaseLayout`: title, description, canonical, OG, Twitter, `name="robots"`, JSON-LD (WebSite nas páginas estáticas, BlogPosting nos artigos).
- `src/pages/robots.txt.ts` e `src/pages/sitemap.xml.ts` gerados dinamicamente (sitemap inclui posts com lastmod).

## Deploy

```bash
bun install
bun run build
# Publicar no Cloudflare: a pasta dist/ é servida como Worker (adaptador @astrojs/cloudflare)
# Envs opcionais no CF: SUPABASE_URL e SUPABASE_ANON_KEY (fallbacks embutidos no código)
```