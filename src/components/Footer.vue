<template>
  <footer class="footer">
    <div class="footer-container">
      <div class="footer-section">
        <div class="footer-brand">
          <h3>Toko Online</h3>
          <p>Platform belanja online terpercaya dengan produk berkualitas tinggi dan layanan pelanggan terbaik.</p>
        </div>
        <div class="footer-newsletter">
          <h4>Newsletter</h4>
          <p>Dapatkan update produk terbaru dan penawaran khusus</p>
          <div class="newsletter-form">
            <input 
              type="email" 
              placeholder="Masukkan email Anda"
              v-model="newsletterEmail"
              class="newsletter-input"
            >
            <button @click="subscribeNewsletter" class="newsletter-btn">Subscribe</button>
          </div>
        </div>
      </div>
      
      <div class="footer-section">
        <h4>Tautan Cepat</h4>
        <ul class="footer-links">
          <li><a href="#home">Home</a></li>
          <li><a href="#products">Products</a></li>
          <li><a href="#categories">Categories</a></li>
          <li><a href="#about">About Us</a></li>
          <li><a href="#contact">Contact</a></li>
          <li><a href="#faq">FAQ</a></li>
        </ul>
      </div>
      
      <div class="footer-section">
        <h4>Kategori</h4>
        <ul class="footer-links">
          <li><a href="#electronics">Electronics</a></li>
          <li><a href="#fashion">Fashion</a></li>
          <li><a href="#home">Home & Living</a></li>
          <li><a href="#sports">Sports</a></li>
          <li><a href="#books">Books</a></li>
          <li><a href="#beauty">Beauty</a></li>
        </ul>
      </div>
      
      <div class="footer-section">
        <h4>Layanan Pelanggan</h4>
        <ul class="footer-links">
          <li><a href="#shipping">Shipping Info</a></li>
          <li><a href="#returns">Returns</a></li>
          <li><a href="#warranty">Warranty</a></li>
          <li><a href="#privacy">Privacy Policy</a></li>
          <li><a href="#terms">Terms of Service</a></li>
          <li><a href="#support">Customer Support</a></li>
        </ul>
      </div>
      
      <div class="footer-section">
        <h4>Kontak Kami</h4>
        <div class="contact-info">
          <div class="contact-item">
            <span class="contact-icon">📍</span>
            <span>Jl. Sudirman No. 123, Pekanbaru 28288</span>
          </div>
          <div class="contact-item">
            <span class="contact-icon">📞</span>
            <span>+62 xxx xxxx xxxx</span>
          </div>
          <div class="contact-item">
            <span class="contact-icon">📧</span>
            <span>arikristian@tokoonline.com</span>
          </div>
          <div class="contact-item">
            <span class="contact-icon">🕐</span>
            <span>Senin - Jumat: 09:00 - 18:00</span>
          </div>
        </div>
        
        <div class="social-section">
          <h4>Ikuti Kami</h4>
          <div class="social-links">
            <a href="#" class="social-link facebook" title="Facebook">
              <span>📘</span>
            </a>
            <a href="#" class="social-link instagram" title="Instagram">
              <span>📷</span>
            </a>
            <a href="#" class="social-link twitter" title="Twitter">
              <span>🐦</span>
            </a>
            <a href="#" class="social-link youtube" title="YouTube">
              <span>📺</span>
            </a>
            <a href="#" class="social-link whatsapp" title="WhatsApp">
              <span>💬</span>
            </a>
          </div>
        </div>
      </div>
    </div>
    
    <div class="footer-bottom">
      <div class="footer-bottom-content">
        <p>&copy; 2025 Toko Online. All rights reserved.</p>
        <div class="payment-methods">
          <span>Metode Pembayaran:</span>
          <div class="payment-icons">
            <span class="payment-icon">💳</span>
            <span class="payment-icon">🏧</span>
            <span class="payment-icon">📱</span>
            <span class="payment-icon">💰</span>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  data() {
    return {
      newsletterEmail: ''
    }
  },
  methods: {
    subscribeNewsletter() {
      if (this.newsletterEmail) {
        console.log('Newsletter subscription:', this.newsletterEmail);
        // Here you would typically send the email to your backend
        alert('Terima kasih! Anda telah berlangganan newsletter kami.');
        this.newsletterEmail = '';
      } else {
        alert('Silakan masukkan email yang valid.');
      }
    }
  }
}
</script>

<style scoped>
.footer {
  background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
  color: white;
  padding: 4rem 0 0;
  margin-top: 4rem;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr 1.5fr;
  gap: 3rem;
  padding: 0 2rem;
}

.footer-section h3,
.footer-section h4 {
  margin-bottom: 1.5rem;
  color: #3498db;
  font-weight: 700;
}

.footer-brand h3 {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.footer-brand p {
  line-height: 1.6;
  color: #bdc3c7;
  margin-bottom: 2rem;
}

.footer-newsletter h4 {
  font-size: 1.3rem;
}

.footer-newsletter p {
  color: #bdc3c7;
  margin-bottom: 1rem;
  font-size: 0.9rem;
}

.newsletter-form {
  display: flex;
  gap: 1rem;
  margin-top: 1rem;
}

.newsletter-input {
  flex: 1;
  padding: 12px;
  border: none;
  border-radius: 8px;
  font-size: 0.9rem;
  background: rgba(255,255,255,0.1);
  color: white;
  border: 1px solid rgba(255,255,255,0.2);
}

.newsletter-input::placeholder {
  color: rgba(255,255,255,0.6);
}

.newsletter-input:focus {
  outline: none;
  border-color: #3498db;
  background: rgba(255,255,255,0.15);
}

.newsletter-btn {
  background: #3498db;
  color: white;
  border: none;
  padding: 12px 20px;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s ease;
  white-space: nowrap;
}

.newsletter-btn:hover {
  background: #2980b9;
  transform: translateY(-2px);
}

.footer-links {
  list-style: none;
  padding: 0;
}

.footer-links li {
  margin-bottom: 0.8rem;
}

.footer-links a {
  color: #bdc3c7;
  text-decoration: none;
  transition: all 0.3s ease;
  display: block;
  padding: 0.2rem 0;
}

.footer-links a:hover {
  color: #3498db;
  padding-left: 0.5rem;
}

.contact-info {
  margin-bottom: 2rem;
}

.contact-item {
  display: flex;
  align-items: flex-start;
  gap: 0.8rem;
  margin-bottom: 1rem;
  color: #bdc3c7;
  font-size: 0.9rem;
  line-height: 1.4;
}

.contact-icon {
  font-size: 1.1rem;
  min-width: 20px;
}

.social-section h4 {
  margin-bottom: 1rem;
}

.social-links {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 45px;
  height: 45px;
  background: rgba(255,255,255,0.1);
  border-radius: 50%;
  text-decoration: none;
  transition: all 0.3s ease;
  font-size: 1.2rem;
}

.social-link:hover {
  background: #3498db;
  transform: translateY(-3px) scale(1.1);
  box-shadow: 0 5px 15px rgba(52, 152, 219, 0.4);
}

.footer-bottom {
  background: rgba(0,0,0,0.2);
  margin-top: 3rem;
  padding: 2rem 0;
}

.footer-bottom-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.footer-bottom-content p {
  color: #bdc3c7;
  font-size: 0.9rem;
}

.payment-methods {
  display: flex;
  align-items: center;
  gap: 1rem;
  color: #bdc3c7;
  font-size: 0.9rem;
}

.payment-icons {
  display: flex;
  gap: 0.5rem;
}

.payment-icon {
  font-size: 1.5rem;
  padding: 0.3rem;
  background: rgba(255,255,255,0.1);
  border-radius: 5px;
  transition: all 0.3s ease;
}

.payment-icon:hover {
  background: rgba(255,255,255,0.2);
  transform: scale(1.1);
}

/* Mobile Responsive */
@media (max-width: 1024px) {
  .footer-container {
    grid-template-columns: 1fr 1fr 1fr;
    gap: 2rem;
  }
  
  .footer-section:first-child {
    grid-column: 1 / -1;
  }
}

@media (max-width: 768px) {
  .footer {
    padding: 3rem 0 0;
  }
  
  .footer-container {
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
    padding: 0 1rem;
  }
  
  .footer-section:first-child {
    grid-column: 1 / -1;
  }
  
  .newsletter-form {
    flex-direction: column;
  }
  
  .newsletter-btn {
    align-self: flex-start;
  }
  
  .footer-bottom-content {
    flex-direction: column;
    text-align: center;
    gap: 1.5rem;
  }
  
  .payment-methods {
    flex-direction: column;
    gap: 0.5rem;
  }
}

@media (max-width: 480px) {
  .footer-container {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .footer-section:first-child {
    grid-column: auto;
  }
  
  .social-links {
    justify-content: center;
  }
  
  .contact-info {
    text-align: left;
  }
  
  .contact-item {
    justify-content: flex-start;
  }
}
</style>