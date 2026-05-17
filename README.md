# ⚡ Prime - E-commerce Premium Mobile-First

Um e-commerce moderno, interativo e visualmente premium, focado em experiência de usuário estilo apps como Amazon, Mercado Livre e Apple Store.

## 🚀 Características

### Design & UX
- ✨ **Design Mobile-First**: Totalmente otimizado para celulares
- 🎨 **Tema Escuro Premium**: Visual elegante com gradientes e glassmorphism
- ⚡ **Animações Fluidas**: Microinterações suaves com Framer Motion
- 📱 **Navegação Mobile**: Bottom navigation estilo app nativo
- 🎯 **Alta Conversão**: Interface limpa e intuitiva

### Funcionalidades
- 🛍️ **Catálogo de Produtos**: Browsing intuitivo com filtros
- 🛒 **Carrinho de Compras**: Atualização em tempo real
- 💳 **Checkout Simplificado**: Processo de compra em etapas
- ❤️ **Wishlist/Favoritos**: Salve produtos favoritos
- 👤 **Conta de Usuário**: Perfil, pedidos e endereços
- ⚡ **Flash Sale**: Ofertas com countdown
- 🔍 **Busca Inteligente**: Exploração de categorias
- ⭐ **Avaliações**: Sistema de ratings visual

### Componentes Visuais
- 🎴 **Cards Interativos**: Com hover effects e animações
- 🖼️ **Galeria de Imagens**: Com zoom e visualização em fullscreen
- 📸 **Seletores de Variantes**: Cores e tamanhos
- 🔢 **Seletor de Quantidade**: Com controles intuitivos
- 💳 **Resumo de Compra**: Sticky e responsivo
- 🎫 **Badges e Tags**: Destaque de promoções

## 🛠️ Tecnologias

- **Framework**: Next.js 14
- **Linguagem**: TypeScript
- **Styling**: TailwindCSS 3
- **Animações**: Framer Motion
- **State Management**: Zustand
- **Icons**: Lucide React
- **Utilities**: clsx, tailwind-merge

## 📁 Estrutura do Projeto

```
premium-ecommerce/
├── app/                          # Next.js app router
│   ├── layout.tsx               # Layout global
│   ├── page.tsx                 # Homepage
│   ├── globals.css              # Estilos globais
│   ├── product/[id]/page.tsx    # Página de produto
│   ├── cart/page.tsx            # Carrinho
│   ├── checkout/page.tsx        # Checkout
│   ├── account/page.tsx         # Conta do usuário
│   ├── wishlist/page.tsx        # Favoritos
│   ├── flash-sale/page.tsx      # Flash sale
│   ├── explore/page.tsx         # Exploração
│   ├── featured/page.tsx        # Destaques
│   └── category/[id]/page.tsx   # Categoria específica
│
├── components/                   # Componentes React
│   ├── common/
│   │   ├── Navbar.tsx           # Barra de navegação
│   │   ├── BottomNav.tsx        # Navegação inferior
│   │   └── ProductCard.tsx      # Card de produto
│   ├── home/
│   │   ├── Banner.tsx           # Banner principal
│   │   ├── ProductCarousel.tsx  # Carrossel de produtos
│   │   └── CategorySection.tsx  # Seção de categorias
│   ├── product/
│   │   ├── ImageGallery.tsx     # Galeria de imagens
│   │   ├── VariantSelector.tsx  # Seletor de variantes
│   │   ├── QuantitySelector.tsx # Seletor de quantidade
│   │   └── RatingSection.tsx    # Seção de avaliações
│   └── cart/
│       ├── CartItem.tsx         # Item do carrinho
│       └── CartSummary.tsx      # Resumo do carrinho
│
├── store/                        # Zustand stores
│   ├── cart.ts                  # Store do carrinho
│   └── wishlist.ts              # Store de favoritos
│
├── data/                         # Dados mock
│   └── products.ts              # Produtos e categorias
│
├── types/                        # TypeScript types
│   └── index.ts                 # Definições de tipos
│
├── lib/                          # Utilitários
│   └── utils.ts                 # Funções auxiliares
│
├── public/                       # Assets estáticos
│
├── package.json                 # Dependências
├── tailwind.config.ts           # Configuração do Tailwind
├── tsconfig.json                # Configuração do TypeScript
├── postcss.config.js            # Configuração do PostCSS
└── next.config.js               # Configuração do Next.js
```

## 🚀 Como Usar

### Instalação

```bash
# Clonar ou criar o projeto
cd premium-ecommerce

# Instalar dependências
npm install
# ou
yarn install
```

### Desenvolvimento

```bash
# Iniciar servidor de desenvolvimento
npm run dev
# ou
yarn dev
```

Abra [http://localhost:3000](http://localhost:3000) no navegador.

### Build & Deploy

```bash
# Build para produção
npm run build

# Iniciar servidor de produção
npm run start
```

## 📱 Páginas Disponíveis

| Página | Rota | Descrição |
|--------|------|-----------|
| Home | `/` | Página inicial com banner, categorias e produtos |
| Produto | `/product/[id]` | Detalhes do produto com galeria e compra |
| Carrinho | `/cart` | Visualizar e gerenciar itens do carrinho |
| Checkout | `/checkout` | Processo de compra em etapas |
| Conta | `/account` | Perfil, pedidos e endereços |
| Favoritos | `/wishlist` | Produtos salvos como favoritos |
| Explorar | `/explore` | Exploração de categorias |
| Flash Sale | `/flash-sale` | Ofertas especiais com countdown |
| Destaques | `/featured` | Produtos em destaque da semana |
| Categoria | `/category/[id]` | Produtos de uma categoria específica |

## 🎨 Design System

### Cores
- **Primary**: Purpura (#a855f7)
- **Dark**: Preto (#0a0a0a)
- **Background**: Dark-900 (#0a0a0a)

### Tipografia
- **Títulos**: Fonte bold
- **Corpo**: Fonte regular
- **Pequeno**: Texto xs para labels

### Componentes
- **Buttons**: Primary, Secondary com hover effects
- **Cards**: Com glass effect e borders
- **Badges**: Gradientes com sombras
- **Loading**: Skeleton shimmer

## 🎯 Funcionalidades Adicionais

### State Management
- Zustand para gerenciamento de cart e wishlist
- Persistência automática entre sessões

### Animações
- Framer Motion para transições suaves
- Motion effects em cards e botões
- Skeleton loading animado
- Contadores regressivos

### Responsividade
- Mobile-first approach
- Breakpoints: md (768px), lg (1024px)
- Touch-friendly buttons e spacing

## 🔧 Customização

### Adicionar Novos Produtos
Edite `data/products.ts`:

```typescript
export const products: Product[] = [
  {
    id: "9",
    name: "Seu Produto",
    price: 99.90,
    rating: 4.5,
    reviews: 100,
    image: "https://...",
    category: "Eletrônicos",
    description: "Descrição do produto",
    inStock: true,
  },
  // ...
];
```

### Modificar Cores
Edite `tailwind.config.ts`:

```typescript
colors: {
  primary: {
    500: "#sua-cor",
    // ...
  },
},
```

### Adicionar Novos Componentes
1. Criar arquivo em `components/[tipo]/NomeComponente.tsx`
2. Importar e usar em páginas

## 📊 Performance

- ✅ Imagens otimizadas com Next.js Image
- ✅ Code splitting automático
- ✅ CSS-in-JS otimizado
- ✅ Lazy loading de componentes
- ✅ Sem dependências pesadas

## 🤝 Contribuindo

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/NovaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona nova feature'`)
4. Push para a branch (`git push origin feature/NovaFeature`)
5. Abra um Pull Request

## 📝 Licença

MIT - Sinta-se livre para usar este projeto comercialmente

## 💡 Dicas & Boas Práticas

### Para Desenvolvedores
1. Use componentes reutilizáveis
2. Mantenha tipos TypeScript atualizados
3. Aproveite Framer Motion para interações
4. Teste em múltiplos dispositivos
5. Considere acessibilidade

### Para Designers
1. Respeite o design system
2. Mantenha consistência visual
3. Teste animações em dispositivos reais
4. Use grid TailwindCSS
5. Considere performance

### Para Produção
1. Adicione autenticação real
2. Implemente pagamento real (Stripe, PagSeguro)
3. Configure analytics
4. Implemente SEO
5. Configure CDN para imagens
6. Adicione monitoring e logging

## 🐛 Troubleshooting

### Problema: Estilos não aplicando
**Solução**: Execute `npm run build` ou reinicie o servidor dev

### Problema: Imagens não carregando
**Solução**: Verifique URLs no `data/products.ts`

### Problema: Animações lentas
**Solução**: Verifique desempenho do dispositivo, reduza número de animações simultâneas

## 📞 Suporte

Para dúvidas ou sugestões, abra uma issue no GitHub.

---

**⚡ Desenvolvido usando React, Next.js e Tailwind CSS**
