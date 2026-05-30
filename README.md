# 🏠 PremiumSC Imóveis

Site imobiliário premium completo construído com Next.js 15, TypeScript, TailwindCSS e Supabase.

## Stack

| Camada | Tecnologia |
|--------|-----------|
| Frontend | Next.js 15 (App Router) + TypeScript |
| Estilo | TailwindCSS + Google Fonts (Playfair Display + DM Sans) |
| Backend / BD | Supabase (PostgreSQL + Auth + Storage) |
| Hospedagem | Vercel ou Cloudflare Pages |
| SEO | Metadata API, sitemap.xml, robots.txt, schema.org |

## Funcionalidades

### Site público
- ✅ Homepage com hero fullscreen + busca avançada
- ✅ Listagem de imóveis com filtros dinâmicos (sidebar)
- ✅ Página individual do imóvel com galeria, mapa e formulário de lead
- ✅ Páginas SEO por cidade (`/cidade/balneario-camboriu`)
- ✅ Busca por tipo, finalidade, cidade, preço, quartos, área
- ✅ WhatsApp flutuante em todas as páginas
- ✅ Imóveis similares na página do imóvel
- ✅ Schema.org para SEO rico
- ✅ Sitemap.xml dinâmico
- ✅ Feed XML para portais (OLX, ZAP, VivaReal)

### Painel Admin
- ✅ Login com Supabase Auth
- ✅ Dashboard com estatísticas
- ✅ CRUD completo de imóveis
- ✅ Upload de múltiplas fotos para Supabase Storage
- ✅ Gestão de leads com atualização de status
- ✅ Exportação de leads em CSV
- ✅ Gestão de corretores

## Instalação

```bash
# 1. Clone e instale
npm install

# 2. Configure variáveis de ambiente
cp .env.example .env.local
# Edite .env.local com seus dados do Supabase

# 3. Execute o schema no Supabase
# Cole o conteúdo de supabase/migrations/001_initial_schema.sql
# no SQL Editor do Supabase

# 4. Rode em desenvolvimento
npm run dev
```

## Estrutura de pastas

```
src/
├── app/
│   ├── site/              # Páginas públicas
│   │   ├── page.tsx       # Homepage
│   │   ├── imoveis/       # Listagem com filtros
│   │   ├── imovel/[slug]/ # Página do imóvel
│   │   └── cidade/[slug]/ # Página SEO por cidade
│   ├── admin/             # Painel admin (protegido)
│   │   ├── dashboard/
│   │   ├── imoveis/
│   │   ├── leads/
│   │   └── corretores/
│   ├── auth/              # Login/logout
│   └── api/               # API routes
│       ├── leads/         # Captura de leads
│       ├── admin/         # APIs admin
│       ├── feed/          # XML para portais
│       └── sitemap.xml/   # Sitemap dinâmico
├── components/
│   ├── layout/            # Header, Footer, WhatsAppFloat
│   ├── property/          # Cards, Filtros, Galeria, LeadForm
│   ├── home/              # HeroSearch
│   └── admin/             # PropertyForm, LeadsTable
└── lib/
    ├── supabase/          # Clients (browser + server)
    ├── queries.ts         # Queries Supabase reutilizáveis
    └── utils.ts           # Formatação, slugify, XML, etc.
```

## Supabase Storage

Crie um bucket público chamado `property-images` no Supabase Storage.

## Deploy no Vercel

```bash
vercel deploy
```

Configure as variáveis de ambiente no painel do Vercel.

## Integração com portais (OLX/ZAP/VivaReal)

O endpoint `/api/feed` exporta todos os imóveis ativos no formato XML compatível.
Configure a URL `https://seusite.com.br/api/feed` nos portais imobiliários.

## SEO

- URLs amigáveis: `/imovel/apartamento-balneario-camboriu-abc123`
- Páginas por cidade: `/cidade/balneario-camboriu`
- Metadata dinâmica por imóvel (Open Graph + Twitter Card)
- Schema.org `RealEstateListing` em cada imóvel
- `sitemap.xml` automático com todos os imóveis ativos
- `robots.txt` configurado

## Personalização

- Cores principais: `#0A1628` (azul escuro) e `#C9A84C` (dourado)
- Altere em `src/app/globals.css` e `tailwind.config.ts`
- Número de WhatsApp: `NEXT_PUBLIC_WHATSAPP_NUMBER` no `.env.local`
- Nome da empresa e CRECI: edite `src/components/layout/Footer.tsx`
