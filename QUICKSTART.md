/**
 * ⚡ PRIME - E-commerce Premium Mobile-First
 * 
 * INSTRUÇÕES DE INICIALIZAÇÃO RÁPIDA
 * ==================================
 */

# 1️⃣ INSTALAÇÃO

```bash
npm install
# ou
yarn install
```

# 2️⃣ DESENVOLVIMENTO

```bash
npm run dev
# ou
yarn dev
```

Acesse: http://localhost:3000

# 3️⃣ ESTRUTURA RÁPIDA

## Páginas Principais
- `/` - Homepage com banner e produtos
- `/product/[id]` - Detalhes do produto
- `/cart` - Carrinho de compras
- `/checkout` - Finalizando pedido
- `/account` - Perfil do usuário

## Componentes Principais
- `ProductCard` - Card de produto reutilizável
- `ImageGallery` - Galeria de imagens com zoom
- `CartItem` - Item do carrinho
- `Banner` - Banner animado com carousel

## Stores (Zustand)
- `useCart` - Gerenciar carrinho
- `useWishlist` - Gerenciar favoritos

# 4️⃣ CUSTOMIZAÇÃO

## Trocar Cores
Edit: tailwind.config.ts
```typescript
colors: {
  primary: {
    500: "#sua-cor",
  }
}
```

## Adicionar Produtos
Edit: data/products.ts
```typescript
{
  id: "9",
  name: "Novo Produto",
  price: 99.90,
  // ... resto dos campos
}
```

## Criar Nova Página
1. Criar arquivo em: app/nova-pagina/page.tsx
2. Usar layout automático do Next.js

# 5️⃣ RECURSOS PRONTOS

✅ Carrinho com persistência
✅ Favoritos (Wishlist)
✅ Checkout em etapas
✅ Flash Sale com countdown
✅ Galeria de imagens com zoom
✅ Seletores de variantes
✅ Responsivo mobile-first
✅ Animações suaves
✅ Dark mode elegante
✅ Bottom navigation mobile

# 6️⃣ VARIÁVEIS DE AMBIENTE

Crie arquivo `.env.local`:
```
NEXT_PUBLIC_API_URL=https://api.seu-dominio.com
```

# 7️⃣ BUILD & DEPLOY

```bash
# Build para produção
npm run build

# Testar build localmente
npm run start
```

Deploy em Vercel:
```bash
vercel deploy
```

# 8️⃣ PRÓXIMOS PASSOS

[ ] Implementar autenticação real
[ ] Conectar com API backend
[ ] Adicionar pagamento real (Stripe)
[ ] Configurar SEO
[ ] Adicionar analytics
[ ] Implementar busca avançada
[ ] Adicionar avaliações de usuários
[ ] Sistema de cupons
[ ] Rastreamento de pedidos
[ ] Notificações em tempo real

# 9️⃣ COMANDOS ÚTEIS

```bash
# Desenvolvimento
npm run dev

# Build
npm run build

# Produção
npm run start

# Linting
npm run lint

# Limpar cache
rm -rf .next node_modules
npm install
```

# 🔟 DOCUMENTAÇÃO

- Next.js: https://nextjs.org/docs
- TailwindCSS: https://tailwindcss.com/docs
- Framer Motion: https://www.framer.com/motion
- Zustand: https://github.com/pmndrs/zustand
- TypeScript: https://www.typescriptlang.org/docs

---

⚡ Seu e-commerce premium está pronto! Divirta-se desenvolvendo!
