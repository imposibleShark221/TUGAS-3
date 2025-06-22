<template>
  <section class="carousel-section">
    <h2>Produk Unggulan</h2>
    <div class="carousel">
      <div class="carousel-container">
        <div 
          class="carousel-slide" 
          v-for="(slide, index) in slides" 
          :key="index"
          :class="{ active: currentSlide === index }"
        >
          <img :src="slide.image" :alt="slide.title">
          <div class="slide-content">
            <h3>{{ slide.title }}</h3>
            <p>{{ slide.description }}</p>
            <button class="slide-button">Lihat Detail</button>
          </div>
        </div>
      </div>
      <button class="carousel-btn prev" @click="prevSlide">❮</button>
      <button class="carousel-btn next" @click="nextSlide">❯</button>
      <div class="carousel-indicators">
        <span 
          v-for="(slide, index) in slides" 
          :key="index"
          :class="{ active: currentSlide === index }"
          @click="goToSlide(index)"
        ></span>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Carousel',
  data() {
    return {
      currentSlide: 0,
      autoSlideInterval: null,
      slides: [
        {
          title: 'Smartphone Terbaru',
          description: 'Dapatkan smartphone dengan teknologi terdepan dan kamera berkualitas tinggi untuk pengalaman mobile yang luar biasa.',
          image: 'https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?w=500&h=300&fit=crop'
        },
        {
          title: 'Fashion Trendy',
          description: 'Koleksi fashion terkini untuk gaya hidup modern. Tampil percaya diri dengan pilihan busana yang stylish.',
          image: 'https://images.unsplash.com/photo-1445205170230-053b83016050?w=500&h=300&fit=crop'
        },
        {
          title: 'Elektronik Rumah',
          description: 'Peralatan elektronik untuk kenyamanan rumah Anda. Nikmati kemudahan hidup dengan teknologi modern.',
          image: 'https://images.unsplash.com/photo-1518837695005-2083093ee35b?w=500&h=300&fit=crop'
        },
        {
          title: 'Gadget & Aksesoris',
          description: 'Temukan berbagai gadget dan aksesoris terbaru untuk mendukung aktivitas digital Anda sehari-hari.',
          image: 'https://images.unsplash.com/photo-1468495244123-6c6c332eeece?w=500&h=300&fit=crop'
        }
      ]
    }
  },
  methods: {
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.slides.length;
    },
    prevSlide() {
      this.currentSlide = this.currentSlide === 0 ? this.slides.length - 1 : this.currentSlide - 1;
    },
    goToSlide(index) {
      this.currentSlide = index;
    },
    startAutoSlide() {
      this.autoSlideInterval = setInterval(() => {
        this.nextSlide();
      }, 5000);
    },
    stopAutoSlide() {
      if (this.autoSlideInterval) {
        clearInterval(this.autoSlideInterval);
      }
    }
  },
  mounted() {
    this.startAutoSlide();
  },
  beforeUnmount() {
    this.stopAutoSlide();
  }
}
</script>

<style scoped>
.carousel-section {
  padding: 80px 2rem;
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

.carousel-section h2 {
  margin-bottom: 3rem;
  font-size: 2.5rem;
  color: #2c3e50;
}

.carousel {
  position: relative;
  max-width: 900px;
  margin: 0 auto;
}

.carousel-container {
  position: relative;
  height: 450px;
  overflow: hidden;
  border-radius: 15px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.3);
}

.carousel-slide {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: opacity 0.6s ease-in-out;
  display: flex;
  align-items: center;
}

.carousel-slide.active {
  opacity: 1;
}

.carousel-slide img {
  width: 55%;
  height: 100%;
  object-fit: cover;
}

.slide-content {
  width: 45%;
  padding: 2.5rem;
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: left;
}

.slide-content h3 {
  font-size: 2rem;
  margin-bottom: 1rem;
  color: #2c3e50;
  font-weight: 700;
}

.slide-content p {
  font-size: 1rem;
  line-height: 1.6;
  color: #6c757d;
  margin-bottom: 1.5rem;
}

.slide-button {
  background: #3498db;
  color: white;
  border: none;
  padding: 12px 24px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1rem;
  font-weight: 600;
  transition: all 0.3s ease;
  align-self: flex-start;
}

.slide-button:hover {
  background: #2980b9;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(52, 152, 219, 0.4);
}

.carousel-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0,0,0,0.6);
  color: white;
  border: none;
  padding: 15px 20px;
  cursor: pointer;
  font-size: 20px;
  border-radius: 50%;
  transition: all 0.3s ease;
  z-index: 10;
}

.carousel-btn:hover {
  background: rgba(0,0,0,0.8);
  transform: translateY(-50%) scale(1.1);
}

.prev {
  left: 20px;
}

.next {
  right: 20px;
}

.carousel-indicators {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-top: 25px;
}

.carousel-indicators span {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: #bdc3c7;
  cursor: pointer;
  transition: all 0.3s ease;
}

.carousel-indicators span:hover {
  background: #95a5a6;
  transform: scale(1.2);
}

.carousel-indicators span.active {
  background: #3498db;
  transform: scale(1.3);
}

/* Mobile Responsive */
@media (max-width: 768px) {
  .carousel-section {
    padding: 60px 1rem;
  }

  .carousel-section h2 {
    font-size: 2rem;
    margin-bottom: 2rem;
  }

  .carousel-container {
    height: 500px;
  }

  .carousel-slide {
    flex-direction: column;
  }

  .carousel-slide img,
  .slide-content {
    width: 100%;
    height: 50%;
  }

  .slide-content {
    padding: 1.5rem;
    text-align: center;
  }

  .slide-content h3 {
    font-size: 1.5rem;
  }

  .slide-content p {
    font-size: 0.9rem;
  }

  .carousel-btn {
    padding: 10px 15px;
    font-size: 16px;
  }

  .prev {
    left: 10px;
  }

  .next {
    right: 10px;
  }
}

@media (max-width: 480px) {
  .carousel-container {
    height: 400px;
    border-radius: 10px;
  }

  .slide-content {
    padding: 1rem;
  }

  .slide-content h3 {
    font-size: 1.3rem;
  }

  .carousel-btn {
    padding: 8px 12px;
    font-size: 14px;
  }
}
</style>