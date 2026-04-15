# CLAUDE.md — MOBILIINTELLIGENTI

Site gerado pelo **SF (Site Factory)** em 15/04/2026.

## Contexto do Site

**Nome:** MOBILIINTELLIGENTI
**Nicho:** Casa e Decoração
**Keywords:** Alphaville foi o local escolhido para receber o primeiro Showroom da Mobili
**Paleta de cores:** ocean | **Fonte:** outfit

Alphaville foi o local escolhido para receber o primeiro Showroom da Mobili Intelligenti, uma verdadeira inovação em mobiliário que vem para solucionar o problema dos espaços compactos. A correria do dia a dia faz com que as pessoas escolham cada vez mais morar em espaços reduzidos, como apartamentos pequenos e de fácil manutenção, onde móveis funcionais são peças chave para atender estas necessidades. Pensando exatamente nesta crescente demanda do mercado, e seguindo as tendências norte americana e europeia, a Mobili Intelligenti traz, com exclusividade para o Brasil, móveis transformáveis. Importados de várias partes do mundo, os móveis com design moderno e de alta qualidade, se transformam em outros móveis em questão de segundos, isso graças à tecnologia utilizada nas diversas ferragens. Práticos, todos os móveis podem ser manuseados com facilidade por homens ou mulheres de todas as idades. Com este lançamento exclusivo, a Mobili Intelligenti se instala no país com três palavras de ordem que combinam perfeitamente com o séc. XXI: versatilidade, design e qualidade. CONHEÇA NOSSO SHOWROOM: Alameda Araguaia, 122 – G7 – Alphaville/São Paulo Tel. 55 11 4195-6903  –   WhatsApp 55 11 97761-4863



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
  content/blog/    # Posts em Markdown
  pages/           # Rotas Astro (index, sobre, contato, blog, privacidade, termos)
  layouts/         # BaseLayout com fonte e cores dinâmicas
  styles/          # global.css com variáveis CSS de cor
public/
  images/          # hero.jpg, about.jpg, blog/*.jpg — inseridos automaticamente via Pexels
```

## O que editar

### Textos e conteúdo
- **`src/data/home.json`** — hero (título, subtítulo, botão), features (título, items), about section (título, desc, stats), posts
- **`src/data/sobre.json`** — conteúdo completo da página Sobre (hero, texto, missão)
- **`src/data/contato.json`** — título, subtítulo, email, tempo de resposta
- **`src/data/siteConfig.json`** — nome, slug, email, redes sociais, menu

### Imagens
Imagens já estão em `public/images/` (via Pexels). Para substituir, mantenha os mesmos nomes de arquivo:
- `hero.jpg` — imagem de fundo do Hero
- `about.jpg` — imagem da seção About (home)
- `sobre.jpg` — imagem de fundo da página Sobre
- `blog/{slug}.jpg` — imagens dos posts

### Posts do blog
Arquivos em `src/content/blog/`. Ajuste o tom de voz, adicione dados específicos do nicho e personalize conforme a identidade do site.

### Cores
Variáveis em `src/styles/global.css`: `--color-primary`, `--color-accent`, `--color-dark`.

## Deploy

```bash
bun install
bun run build
# Faça upload da pasta dist/ para Netlify, Vercel ou hosting estático
```
