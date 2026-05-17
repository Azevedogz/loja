/**
 * EXEMPLOS DE COMO USAR COMPONENTES E STORES
 * ============================================
 * 
 * Este arquivo mostra exemplos práticos de como usar
 * os componentes e stores disponíveis no projeto.
 */

// ============================================
// 1. USANDO STORE DO CARRINHO
// ============================================

import { useCart } from "@/store/cart";
import { Product } from "@/types";

// Em um componente:
export function ExemploCarrinho() {
  const { items, addToCart, removeFromCart, getTotalPrice, clearCart } = useCart();

  const produto: Product = {
    id: "1",
    name: "Produto Exemplo",
    price: 99.90,
    rating: 4.5,
    reviews: 100,
    image: "https://...",
    category: "Eletrônicos",
    description: "Descrição",
    inStock: true,
  };

  const handleAddToCart = () => {
    addToCart(produto, 1, "Preto", "M");
    // quantity=1, selectedColor="Preto", selectedSize="M"
  };

  const total = getTotalPrice();

  return (
    <div>
      <button onClick={handleAddToCart}>Adicionar ao Carrinho</button>
      <p>Total: R$ {total.toFixed(2)}</p>
      <p>Itens: {items.length}</p>
    </div>
  );
}

// ============================================
// 2. USANDO STORE DE FAVORITOS (WISHLIST)
// ============================================

import { useWishlist } from "@/store/wishlist";

export function ExemploWishlist() {
  const { items, addToWishlist, removeFromWishlist, isInWishlist } = useWishlist();

  const produto: Product = { /* ... */ };
  const inWishlist = isInWishlist(produto.id);

  const toggleWishlist = () => {
    if (inWishlist) {
      removeFromWishlist(produto.id);
    } else {
      addToWishlist(produto);
    }
  };

  return (
    <button onClick={toggleWishlist}>
      {inWishlist ? "❤️ Remover dos Favoritos" : "🤍 Adicionar aos Favoritos"}
    </button>
  );
}

// ============================================
// 3. USANDO COMPONENTE PRODUCT CARD
// ============================================

import { ProductCard } from "@/components/common/ProductCard";

export function ExemploProductCard() {
  const produto: Product = { /* ... */ };

  return (
    <div>
      <ProductCard product={produto} index={0} />
    </div>
  );
}

// ============================================
// 4. USANDO IMAGE GALLERY
// ============================================

import { ImageGallery } from "@/components/product/ImageGallery";

export function ExemploImageGallery() {
  const imagens = [
    "https://images.unsplash.com/...",
    "https://images.unsplash.com/...",
    "https://images.unsplash.com/...",
  ];

  return (
    <ImageGallery images={imagens} productName="Meu Produto" />
  );
}

// ============================================
// 5. USANDO VARIANT SELECTOR
// ============================================

import { VariantSelector } from "@/components/product/VariantSelector";
import { useState } from "react";

export function ExemploVariantSelector() {
  const [selectedColor, setSelectedColor] = useState("Preto");

  return (
    <div>
      <VariantSelector
        label="Cores Disponíveis"
        options={["Preto", "Branco", "Azul"]}
        selectedValue={selectedColor}
        onSelect={setSelectedColor}
        type="color"
      />

      <p>Cor Selecionada: {selectedColor}</p>
    </div>
  );
}

// ============================================
// 6. USANDO QUANTITY SELECTOR
// ============================================

import { QuantitySelector } from "@/components/product/QuantitySelector";

export function ExemploQuantitySelector() {
  const [quantity, setQuantity] = useState(1);

  return (
    <QuantitySelector
      quantity={quantity}
      onQuantityChange={setQuantity}
      max={10}
    />
  );
}

// ============================================
// 7. USANDO RATING SECTION
// ============================================

import { RatingSection } from "@/components/product/RatingSection";

export function ExemploRatingSection() {
  return (
    <RatingSection
      rating={4.8}
      reviewCount={2543}
    />
  );
}

// ============================================
// 8. USANDO PRODUCT CAROUSEL
// ============================================

import { ProductCarousel } from "@/components/home/ProductCarousel";

export function ExemploProductCarousel() {
  const produtos = [
    { id: "1", /* ... */ },
    { id: "2", /* ... */ },
    // ...
  ];

  return (
    <ProductCarousel
      title="Best Sellers"
      products={produtos}
      href="/best-sellers"
    />
  );
}

// ============================================
// 9. USANDO CATEGORY SECTION
// ============================================

import { CategorySection } from "@/components/home/CategorySection";

export function ExemploCategorySection() {
  return <CategorySection />;
}

// ============================================
// 10. USANDO BANNER
// ============================================

import { Banner } from "@/components/home/Banner";

export function ExemploBanner() {
  return <Banner />;
}

// ============================================
// 11. USANDO CART ITEM
// ============================================

import { CartItem } from "@/components/cart/CartItem";

export function ExemploCartItem() {
  const item = {
    id: "1",
    name: "Produto",
    price: 99.90,
    quantity: 2,
    image: "https://...",
    // ... outros campos
  };

  return <CartItem item={item} />;
}

// ============================================
// 12. USANDO CART SUMMARY
// ============================================

import { CartSummary } from "@/components/cart/CartSummary";

export function ExemploCartSummary() {
  return (
    <CartSummary
      subtotal={299.90}
      shipping={15.90}
      discount={0}
    />
  );
}

// ============================================
// 13. USANDO TOAST NOTIFICATIONS
// ============================================

import { Toast, useToast } from "@/components/common/Toast";

export function ExemploToast() {
  const { toasts, addToast, removeToast } = useToast();

  return (
    <div>
      <Toast toasts={toasts} onRemove={removeToast} />

      <button onClick={() => addToast("Produto adicionado!", "success")}>
        Sucesso
      </button>

      <button onClick={() => addToast("Erro ao processar", "error")}>
        Erro
      </button>

      <button onClick={() => addToast("Informação", "info")}>
        Info
      </button>

      <button onClick={() => addToast("Atenção!", "warning")}>
        Aviso
      </button>
    </div>
  );
}

// ============================================
// 14. USANDO FORMATO DE MOEDA
// ============================================

import { formatCurrency } from "@/lib/utils";

export function ExemploFormatCurrency() {
  const preco = 1299.90;

  return (
    <p>Preço: {formatCurrency(preco)}</p>
    // Output: Preço: R$ 1.299,90
  );
}

// ============================================
// 15. USANDO CN (CLASS NAME MERGER)
// ============================================

import { cn } from "@/lib/utils";

export function ExemploCN() {
  const baseClasses = "px-4 py-2 rounded-lg";
  const conditionalClasses = "bg-primary-500";

  return (
    <button className={cn(baseClasses, conditionalClasses)}>
      Botão
    </button>
  );
}

// ============================================
// 16. EXEMPLO COMPLETO: PÁGINA DE PRODUTO
// ============================================

export function ExemploPaginaProduto() {
  const [quantity, setQuantity] = useState(1);
  const [selectedColor, setSelectedColor] = useState("Preto");
  const [selectedSize, setSelectedSize] = useState("M");
  const { addToCart } = useCart();
  const { addToWishlist, isInWishlist, removeFromWishlist } = useWishlist();

  const produto: Product = {
    id: "1",
    name: "Fone Premium",
    price: 299.90,
    originalPrice: 499.90,
    rating: 4.8,
    reviews: 2543,
    image: "https://...",
    images: ["https://...", "https://..."],
    category: "Eletrônicos",
    description: "Descrição do fone",
    badge: "Best Seller",
    colors: ["Preto", "Prata", "Ouro"],
    sizes: ["M", "G"],
    inStock: true,
    discount: 40,
  };

  const handleAddToCart = () => {
    addToCart(produto, quantity, selectedColor, selectedSize);
    // Toast: "Adicionado ao carrinho"
  };

  const handleToggleWishlist = () => {
    if (isInWishlist(produto.id)) {
      removeFromWishlist(produto.id);
    } else {
      addToWishlist(produto);
    }
  };

  return (
    <main>
      <div className="grid md:grid-cols-2 gap-8">
        {/* Galeria */}
        <ImageGallery
          images={produto.images || [produto.image]}
          productName={produto.name}
        />

        {/* Info */}
        <div>
          <h1 className="text-4xl font-bold">{produto.name}</h1>
          <p className="text-xl mt-4">{formatCurrency(produto.price)}</p>

          <VariantSelector
            label="Cores"
            options={produto.colors || []}
            selectedValue={selectedColor}
            onSelect={setSelectedColor}
            type="color"
          />

          <VariantSelector
            label="Tamanhos"
            options={produto.sizes || []}
            selectedValue={selectedSize}
            onSelect={setSelectedSize}
            type="size"
          />

          <QuantitySelector
            quantity={quantity}
            onQuantityChange={setQuantity}
          />

          <button onClick={handleAddToCart} className="btn-primary w-full">
            Comprar
          </button>

          <button onClick={handleToggleWishlist} className="btn-secondary w-full">
            {isInWishlist(produto.id) ? "❤️" : "🤍"} Favoritar
          </button>

          <RatingSection rating={produto.rating} reviewCount={produto.reviews} />
        </div>
      </div>
    </main>
  );
}

// ============================================
// 17. EXEMPLO COMPLETO: PÁGINA DE CARRINHO
// ============================================

export function ExemploPaginaCarrinho() {
  const { items, getTotalPrice } = useCart();

  return (
    <main>
      <h1>Seu Carrinho</h1>

      <div className="grid md:grid-cols-3 gap-8">
        {/* Items */}
        <div className="md:col-span-2 space-y-4">
          {items.map((item) => (
            <CartItem key={item.id} item={item} />
          ))}
        </div>

        {/* Summary */}
        <CartSummary subtotal={getTotalPrice()} />
      </div>
    </main>
  );
}

/**
 * DICAS GERAIS
 * ============
 * 
 * 1. Sempre use "use client" em componentes que usam hooks
 * 2. Importe types do @/types
 * 3. Use formatCurrency para valores em reais
 * 4. Zustand stores são globais e persistem entre componentes
 * 5. Framer Motion components usam motion.div, motion.button, etc
 * 6. TailwindCSS tem classes prontas para tudo
 * 7. Lucide icons: <IconName className="w-5 h-5" />
 * 8. Next.js Link: <Link href="/page"><button>...</button></Link>
 */
