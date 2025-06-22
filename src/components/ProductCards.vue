<template>
  <section class="products-section">
    <div class="container">
      <h2>Produk Terbaru</h2>
      <div class="filter-tabs">
        <button 
          v-for="category in categories" 
          :key="category"
          :class="{ active: activeCategory === category }"
          @click="filterProducts(category)"
          class="filter-btn"
        >
          {{ category }}
        </button>
      </div>
      <div class="cards-container">
        <div 
          class="card" 
          v-for="product in filteredProducts" 
          :key="product.id"
          @click="selectProduct(product)"
        >
          <div class="card-image-container">
            <img :src="product.image" :alt="product.name" class="card-image">
            <div class="card-overlay">
              <button class="quick-view-btn">Quick View</button>
            </div>
            <div class="card-badge" v-if="product.badge">{{ product.badge }}</div>
          </div>
          <div class="card-content">
            <div class="card-category">{{ product.category }}</div>
            <h3 class="card-title">{{ product.name }}</h3>
            <p class="card-description">{{ product.description }}</p>
            <div class="card-rating">
              <span class="stars">
                <span v-for="i in 5" :key="i" :class="{ filled: i <= product.rating }">★</span>
              </span>
              <span class="rating-text">({{ product.reviews }} reviews)</span>
            </div>
            <div class="card-footer">
              <div class="card-price">
                <span class="current-price">{{ formatPrice(product.price) }}</span>
                <span v-if="product.originalPrice" class="original-price">{{ formatPrice(product.originalPrice) }}</span>
              </div>
              <button class="card-button" @click.stop="addToCart(product)">
                <span class="btn-text">Add to Cart</span>
                <span class="btn-icon">🛒</span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ProductCards',
  data() {
    return {
      activeCategory: 'All',
      categories: ['All', 'Electronics', 'Fashion', 'Home', 'Sports'],
      products: [
        {
          id: 1,
          name: 'iPhone 15 Pro Max',
          category: 'Electronics',
          description: 'Smartphone flagship dengan kamera pro dan performa maksimal untuk produktivitas tinggi.',
          price: 18500000,
          originalPrice: 20000000,
          rating: 5,
          reviews: 128,
          badge: 'Best Seller',
          image: 'https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?w=300&h=200&fit=crop'
        },
        {
          id: 2,
          name: 'MacBook Pro M3',
          category: 'Electronics',
          description: 'Laptop profesional dengan chip M3 untuk performa editing video dan coding yang superior.',
          price: 32000000,
          rating: 5,
          reviews: 89,
          badge: 'New',
          image: 'https://images.unsplash.com/photo-1496181133206-80ce9b88a853?w=300&h=200&fit=crop'
        },
        {
          id: 3,
          name: 'Sony WH-1000XM5',
          category: 'Electronics',
          description: 'Headphone wireless premium dengan noise cancellation terbaik di kelasnya.',
          price: 4200000,
          originalPrice: 4800000,
          rating: 4,
          reviews: 256,
          image: 'https://images.unsplash.com/photo-1505740420928-5e560c06d30e?w=300&h=200&fit=crop'
        },
        {
          id: 4,
          name: 'Apple Watch Ultra 2',
          category: 'Electronics',
          description: 'Smartwatch untuk petualangan dengan GPS presisi dan daya tahan baterai hingga 36 jam.',
          price: 12500000,
          rating: 5,
          reviews: 167,
          badge: 'Premium',
          image: 'https://images.unsplash.com/photo-1523275335684-37898b6baf30?w=300&h=200&fit=crop'
        },
        {
          id: 5,
          name: 'Canon EOS R5',
          category: 'Electronics',
          description: 'Kamera mirrorless professional untuk fotografi dan videografi 8K berkualitas cinema.',
          price: 58000000,
          rating: 5,
          reviews: 43,
          badge: 'Pro',
          image: 'https://images.unsplash.com/photo-1606983340126-99ab4feaa64a?w=300&h=200&fit=crop'
        },
        {
          id: 6,
          name: 'Adidas Ultraboost 23',
          category: 'Sports',
          description: 'Sepatu lari dengan teknologi Boost untuk kenyamanan maksimal dan performa optimal.',
          price: 2800000,
          rating: 4,
          reviews: 312,
          image: 'https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=300&h=200&fit=crop'
        },
        {
          id: 7,
          name: 'Zara Blazer Collection',
          category: 'Fashion',
          description: 'Blazer premium dengan cutting modern untuk tampilan profesional dan stylish.',
          price: 1250000,
          originalPrice: 1500000,
          rating: 4,
          reviews: 89,
          badge: 'Sale',
          image: 'https://images.unsplash.com/photo-1594633312681-425c7b97ccd1?w=300&h=200&fit=crop'
        },
        {
          id: 8,
          name: 'Dyson V15 Detect',
          category: 'Home',
          description: 'Vacuum cleaner cordless dengan teknologi laser untuk deteksi debu mikroskopis.',
          price: 8500000,
          rating: 5,
          reviews: 156,
          badge: 'Popular',
          image: 'https://images.unsplash.com/photo-1581578731548-c64695cc6952?w=300&h=200&fit=crop'
        }
      ]
    }
  },
  computed: {
    filteredProducts() {
      if (this.activeCategory === 'All') {
        return this.products;
      }
      return this.products.filter(product => product.category === this.activeCategory);
    }
  },
  methods: {
    filterProducts(category) {
      this.activeCategory = category;
    },
    formatPrice(price) {
      return new Intl.NumberFormat('id-ID', {
        style: 'currency',
        currency: 'IDR',
        minimumFractionDigits: 0
      }).format(price);
    },
    addToCart(product) {
      // Emit event or call store action
      console.log('Added to cart:', product.name);
      // You can emit an event to parent component or use Vuex/Pinia
      this.$emit('add-to-cart', product);
    },
    selectProduct(product) {
      console.log('Selected product:', product.name);
      // Navigate to product detail or emit event
      this.$emit('select-product', product);
    }
  }
}
</script>

<style scoped>
.products-section {
  padding: 80px 0;
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
  min-height: 100vh;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.products-section h2 {
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2.5rem;
  color: #2c3e50;
  font-weight: 700;
}

.filter-tabs {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 3rem;
  flex-wrap: wrap;
}

.filter-btn {
  background: white;
  border: 2px solid #e9ecef;
  padding: 10px 20px;
  border-radius: 25px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-weight: 600;
  color: #6c757d;
}

.filter-btn:hover {
  border-color: #3498db;
  color: #3498db;
  transform: translateY(-2px);
}

.filter-btn.active {
  background: #3498db;
  border-color: #3498db;
  color: white;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(52, 152, 219, 0.3);
}

.cards-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}

.card {
  background: white;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0,0,0,0.1);
  transition: all 0.3s ease;
  cursor: pointer;
  position: relative;
}

.card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(0,0,0,0.15);
}

.card-image-container {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.card-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.card:hover .card-image {
  transform: scale(1.1);
}

.card-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0,0,0,0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.card:hover .card-overlay {
  opacity: 1;
}

.quick-view-btn {
  background: white;
  color: #333;
  padding: 10px 20px;
  border-radius: 25px;
  font-weight: 600;
  transition: all 0.3s ease;
}

.quick-view-btn:hover {
  background: #3498db;
  color: white;
  transform: scale(1.05);
}

.card-badge {
  position: absolute;
  top: 10px;
  right: 10px;
  background: #e74c3c;
  color: white;
  padding: 5px 10px;
  border-radius: 15px;
  font-size: 0.8rem;
  font-weight: 600;
}

.card-content {
  padding: 1.5rem;
}

.card-category {
  color: #3498db;
  font-size: 0.9rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.card-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: #2c3e50;
  margin-bottom: 0.5rem;
  line-height: 1.3;
}

.card-description {
  color: #6c757d;
  font-size: 0.9rem;
  line-height: 1.5;
  margin-bottom: 1rem;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.card-rating {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.stars {
  display: flex;
  gap: 2px;
}

.stars span {
  color: #ddd;
  font-size: 1rem;
}

.stars span.filled {
  color: #f39c12;
}

.rating-text {
  color: #6c757d;
  font-size: 0.8rem;
}

.card-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}

.card-price {
  display: flex;
  flex-direction: column;
}

.current-price {
  font-size: 1.3rem;
  font-weight: 700;
  color: #2c3e50;
}

.original-price {
  font-size: 0.9rem;
  color: #6c757d;
  text-decoration: line-through;
}

.card-button {
  background: linear-gradient(135deg, #3498db 0%, #2980b9 100%);
  color: white;
  padding: 10px 20px;
  border-radius: 25px;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  transition: all 0.3s ease;
  min-width: 120px;
  justify-content: center;
}

.card-button:hover {
  background: linear-gradient(135deg, #2980b9 0%, #1f5f8b 100%);
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(52, 152, 219, 0.4);
}

.btn-icon {
  font-size: 1.1rem;
}

/* Responsive Design */
@media (max-width: 768px) {
  .container {
    padding: 0 1rem;
  }
  
  .products-section h2 {
    font-size: 2rem;
  }
  
  .filter-tabs {
    gap: 0.5rem;
  }
  
  .filter-btn {
    padding: 8px 16px;
    font-size: 0.9rem;
  }
  
  .cards-container {
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1.5rem;
  }
  
  .card-content {
    padding: 1rem;
  }
  
  .card-footer {
    flex-direction: column;
    align-items: stretch;
    gap: 0.5rem;
  }
  
  .card-button {
    width: 100%;
  }
}

@media (max-width: 480px) {
  .cards-container {
    grid-template-columns: 1fr;
  }
  
  .filter-tabs {
    flex-direction: column;
    align-items: center;
  }
}
</style> 