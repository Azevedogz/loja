# 📋 GUIA DE BOAS PRÁTICAS E ESTILO

## 🎨 Guia de Estilo Visual

### Paleta de Cores Primária

```
Primary (Roxo):
- 50: #f8f6ff
- 100: #f0edff
- 500: #a855f7 (cor principal)
- 700: #7e22ce
- 900: #58147f

Dark (Fundo):
- 700: #404040
- 800: #202020
- 900: #0a0a0a (fundo principal)
```

### Tipografia

- **Headings**: Semibold, 28px+ (mobile), 36px+ (desktop)
- **Body**: Regular, 14px-16px
- **Labels**: Semibold, 12px
- **Micro**: Regular, 10px-12px

### Espaçamento

- Padding: 4px, 8px, 12px, 16px, 24px, 32px
- Margin: Seguir padrão de padding
- Gap: 8px (mobile), 12px (desktop)

### Bordas e Raios

- Pequeno: 6px
- Médio: 8px
- Grande: 12px
- Extra grande: 16px (cards, modals)

---

## ✅ Checklist de Boas Práticas

### Desenvolvimento

- [ ] Usar "use client" apenas quando necessário
- [ ] Componentes sem estado preferencialmente
- [ ] Extrair lógica em hooks customizados
- [ ] Usar TypeScript para tipagem
- [ ] Importar types do @/types
- [ ] Manter componentes pequenos e reutilizáveis
- [ ] Documentar componentes complexos
- [ ] Testar responsividade
- [ ] Verificar acessibilidade (alt text, labels)
- [ ] Otimizar imagens

### Performance

- [ ] Lazy loading de imagens
- [ ] Code splitting automático
- [ ] Evitar re-renders desnecessários
- [ ] Usar useCallback para funções
- [ ] Usememo para dados complexos
- [ ] Limitar quantidade de animações simultâneas
- [ ] Testar em dispositivos reais

### UX/UI

- [ ] Feedback visual em cliques
- [ ] Feedback em carregamentos
- [ ] Estados hover/active claros
- [ ] Transições suaves (200-300ms)
- [ ] Touch-friendly (min 44x44px)
- [ ] Contraste acessível (AA+)
- [ ] Mensagens de erro claras
- [ ] Empty states bem projetados
- [ ] Loading states
- [ ] Skeleton screens

### Código

- [ ] Nomes descritivos de variáveis/funções
- [ ] Funções pequenas e focadas
- [ ] DRY - Don't Repeat Yourself
- [ ] Comentários para lógica complexa
- [ ] Sem console.log em produção
- [ ] Tratamento de erros
- [ ] Sem qualquer código comentado

---

## 🎯 Padrões de Uso

### 1. Criar Novo Componente

```typescript
"use client"; // Se usar hooks

import { motion } from "framer-motion";
import { Component, ReactNode } from "react";

interface MeuComponenteProps {
  title: string;
  children?: ReactNode;
  variant?: "primary" | "secondary";
}

export function MeuComponente({
  title,
  children,
  variant = "primary",
}: MeuComponenteProps) {
  return (
    <motion.div
      initial={{ opacity: 0 }}
      animate={{ opacity: 1 }}
      className={`card p-4 ${
        variant === "primary" ? "bg-primary-500/10" : "bg-dark-700"
      }`}
    >
      <h3 className="font-semibold">{title}</h3>
      {children}
    </motion.div>
  );
}
```

### 2. Criar Novo Store

```typescript
// store/exemplo.ts
import { create } from "zustand";

interface ExemploStore {
  dados: string[];
  adicionar: (item: string) => void;
  remover: (item: string) => void;
}

export const useExemplo = create<ExemploStore>((set) => ({
  dados: [],

  adicionar: (item) =>
    set((state) => ({
      dados: [...state.dados, item],
    })),

  remover: (item) =>
    set((state) => ({
      dados: state.dados.filter((d) => d !== item),
    })),
}));
```

### 3. Usar em Componente

```typescript
"use client";

import { useExemplo } from "@/store/exemplo";

export function MeuComponente() {
  const { dados, adicionar, remover } = useExemplo();

  return (
    <div>
      {dados.map((item) => (
        <div key={item}>
          {item}
          <button onClick={() => remover(item)}>Remover</button>
        </div>
      ))}

      <button onClick={() => adicionar("novo")}>Adicionar</button>
    </div>
  );
}
```

### 4. Responsividade

```typescript
// Mobile-first approach
<div className="
  grid grid-cols-1          // 1 coluna mobile
  md:grid-cols-2            // 2 colunas em tablet
  lg:grid-cols-4            // 4 colunas em desktop
  gap-4                      // espaçamento
  px-4                       // padding horizontal
  md:px-6                    // padding aumentado em desktop
">
```

### 5. Animações

```typescript
// Usar Framer Motion
<motion.div
  initial={{ opacity: 0, y: 20 }}      // estado inicial
  animate={{ opacity: 1, y: 0 }}       // estado final
  exit={{ opacity: 0, y: -20 }}        // ao sair (com AnimatePresence)
  transition={{ duration: 0.3 }}       // duração
  whileHover={{ scale: 1.05 }}         // ao passar mouse
  whileTap={{ scale: 0.95 }}           // ao clicar
>
  Conteúdo
</motion.div>
```

---

## 📦 Estrutura de Pasta - Exemplo Novo Domínio

Ao criar novas features, manter a estrutura:

```
feature/
├── components/
│   ├── FeatureName.tsx
│   ├── FeatureDetail.tsx
│   └── FeatureCard.tsx
├── store/
│   └── feature.ts
├── types/
│   └── index.ts
├── page.tsx               // Página principal
└── [id]/
    └── page.tsx          // Página detalhes
```

---

## 🔒 Segurança

- [ ] Validar todos os inputs
- [ ] Sanitizar dados antes de renderizar
- [ ] Usar env vars para dados sensíveis
- [ ] HTTPS em produção
- [ ] Proteger rotas sensíveis
- [ ] Rate limiting em APIs
- [ ] CORS configurado
- [ ] Evitar injeção XSS

---

## 🚀 Deployment

### Vercel (Recomendado)

```bash
# Fazer login
vercel login

# Deploy
vercel deploy --prod
```

### Outras Plataformas

```bash
# Build
npm run build

# Deploy em Netlify, Railway, etc
```

---

## 📱 Testes Responsivos

Testar em:
- [ ] iPhone SE (375px)
- [ ] iPhone 12/13 (390px)
- [ ] iPad (768px)
- [ ] Desktop (1920px)
- [ ] Tablet paisagem (1024px)

---

## 🎭 Testes de UX

- [ ] Todos botões funcionam
- [ ] Animações suaves (60fps)
- [ ] Sem flashes de conteúdo
- [ ] Formulários validam
- [ ] Mensagens de erro claras
- [ ] Feedback em loading
- [ ] Touch em mobile funciona
- [ ] Acessibilidade básica

---

## 📊 Métricas de Qualidade

```
Performance:
- FCP (First Contentful Paint): < 1.8s
- LCP (Largest Contentful Paint): < 2.5s
- CLS (Cumulative Layout Shift): < 0.1
- FID (First Input Delay): < 100ms

Acessibilidade:
- Lighthouse: > 90
- Contraste: AA+ mínimo
- Labels em inputs
- Alt em imagens

SEO:
- Meta tags
- Open Graph
- Sitemap
```

---

## 🐛 Debugging

### Console Logging
```typescript
console.log("Desenvolvimento"); // Remover antes de deploy
```

### React DevTools
- Verificar re-renders
- Inspecionar props
- Profile performance

### Network Tab
- Verificar carregamento de recursos
- Cache de imagens
- Tamanho de bundles

---

## 📚 Recursos Úteis

- [Next.js Docs](https://nextjs.org/docs)
- [React Best Practices](https://react.dev)
- [Tailwind CSS](https://tailwindcss.com)
- [Framer Motion](https://www.framer.com/motion)
- [Web Accessibility](https://www.w3.org/WAI)
- [Performance Web](https://web.dev/performance)

---

## ❓ FAQ

**P: Como adicionar nova página?**
A: Criar arquivo em `app/nova-pagina/page.tsx`

**P: Como modificar cores?**
A: Editar `tailwind.config.ts`

**P: Como usar localStorage?**
A: Usar Zustand com persist middleware

**P: Como adicionar Sentry?**
A: Instalar `@sentry/nextjs` e configurar

**P: Como fazer deploy?**
A: Conectar repo ao Vercel (recomendado)

---

✅ **Seguindo estas boas práticas, seu projeto será profissional e escalável!**
