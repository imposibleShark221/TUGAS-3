<template>
  <div id="app">
    <Navbar />
    
    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-content">
        <h1>Selamat Datang di Toko Online Kami</h1>
        <p>Temukan produk terbaik dengan harga terjangkau</p>
        <button class="cta-button">Belanja Sekarang</button>
      </div>
    </section>

    <Carousel />
    
    <!-- Features Section -->
    <section class="features">
      <div class="container">
        <h2 class="section-title">Mengapa Memilih Kami?</h2>
        <div class="features-grid">
          <div class="feature-card">
            <div class="feature-icon">🚚</div>
            <h3>Pengiriman Cepat</h3>
            <p>Gratis ongkir untuk pembelian di atas Rp 500.000 dengan pengiriman 1-2 hari kerja</p>
          </div>
          <div class="feature-card">
            <div class="feature-icon">🛡️</div>
            <h3>Garansi 100%</h3>
            <p>Produk original dengan garansi resmi dan jaminan uang kembali 30 hari</p>
          </div>
          <div class="feature-card">
            <div class="feature-icon">💬</div>
            <h3>Layanan 24/7</h3>
            <p>Customer service siap membantu Anda kapan saja melalui chat, email, atau telepon</p>
          </div>
          <div class="feature-card">
            <div class="feature-icon">💳</div>
            <h3>Pembayaran Aman</h3>
            <p>Berbagai metode pembayaran yang aman dan terpercaya untuk kenyamanan Anda</p>
          </div>
        </div>
      </div>
    </section>
    
    <ProductCards />
    
    <!-- Newsletter Section -->
    <section class="newsletter-section">
      <div class="container">
        <div class="newsletter-content">
          <h2>Dapatkan Update Terbaru</h2>
          <p>Berlangganan newsletter kami untuk mendapatkan informasi produk terbaru, penawaran eksklusif, dan tips belanja cerdas.</p>
          <div class="newsletter-form">
            <input 
              type="email" 
              placeholder="Masukkan email Anda"
              v-model="newsletterEmail"
              class="newsletter-input"
            >
            <button @click="subscribeNewsletter" class="newsletter-btn">
              <span>Berlangganan</span>
              <span class="btn-arrow">→</span>
            </button>
          </div>
          <p class="newsletter-note">* Kami tidak akan mengirim spam. Anda dapat berhenti berlangganan kapan saja.</p>
        </div>
      </div>
    </section>
    
    <Footer />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Carousel from './components/Carousel.vue'
import ProductCards from './components/ProductCards.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Navbar,
    Carousel,
    ProductCards,
    Footer
  },
  data() {
    return {
      newsletterEmail: ''
    }
  },
  methods: {
    subscribeNewsletter() {
      if (this.newsletterEmail && this.validateEmail(this.newsletterEmail)) {
        // Here you would typically send the email to your backend
        console.log('Newsletter subscription:', this.newsletterEmail);
        alert('Terima kasih! Anda telah berlangganan newsletter kami.');
        this.newsletterEmail = '';
      } else {
        alert('Silakan masukkan email yang valid.');
      }
    },
    validateEmail(email) {
      const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return re.test(email);
    }
  }
}
</script>

<style>
@import './assets/styles/global.css';

/* Hero Section */
.hero {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 120px 0 80px;
  text-align: center;
}

.hero-content h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.hero-content p {
  font-size: 1.3rem;
  margin-bottom: 2.5rem;
  opacity: 0.9;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.9);
  animation: fadeInUp 1s ease-out 0.2s both;
}

.cta-button {
  background: #3498db;
  color: white;
  padding: 12px 30px;
  border: none;
  border-radius: 25px;
  font-size: 1.1rem;
  cursor: pointer;
  transition: background 0.3s;
}

.cta-button:hover {
  background: #2980b9;
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero-content h1 {
    font-size: 2rem;
  }
}
</style>