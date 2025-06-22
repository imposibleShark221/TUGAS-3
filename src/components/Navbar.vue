<template>
  <nav class="navbar">
    <div class="nav-container">
      <div class="nav-brand">
        <h2>🛍️ Toko Online</h2>
      </div>
      <ul class="nav-menu" :class="{ active: isMenuOpen }">
        <li><a href="#home" @click="closeMenu">Home</a></li>
        <li><a href="#products" @click="closeMenu">Products</a></li>
        <li><a href="#about" @click="closeMenu">About</a></li>
        <li><a href="#contact" @click="closeMenu">Contact</a></li>
      </ul>
      <div class="nav-actions">
        <div class="cart-icon" @click="toggleCart">
          🛒
          <span v-if="cartCount > 0" class="cart-badge">{{ cartCount }}</span>
        </div>
        <div class="nav-toggle" @click="toggleMenu">
          <span class="bar"></span>
          <span class="bar"></span>
          <span class="bar"></span>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      isMenuOpen: false,
      cartCount: 0
    }
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
    closeMenu() {
      this.isMenuOpen = false;
    },
    toggleCart() {
      // Emit event to parent or handle cart toggle
      this.$emit('toggle-cart');
    }
  }
}
</script>

<style scoped>
.navbar {
  background: rgba(44, 62, 80, 0.95);
  backdrop-filter: blur(10px);
  color: white;
  padding: 1rem 0;
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 1000;
  box-shadow: 0 2px 20px rgba(0,0,0,0.1);
  transition: all 0.3s ease;
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 2rem;
}

.nav-brand h2 {
  color: #3498db;
  font-size: 1.5rem;
  font-weight: 700;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.nav-menu {
  display: flex;
  list-style: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
}

.nav-menu a {
  color: white;
  text-decoration: none;
  transition: all 0.3s ease;
  padding: 0.5rem 1rem;
  border-radius: 25px;
  font-weight: 500;
  position: relative;
}

.nav-menu a:hover {
  color: #3498db;
  background: rgba(52, 152, 219, 0.1);
  transform: translateY(-2px);
}

.nav-menu a::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  width: 0;
  height: 2px;
  background: #3498db;
  transition: all 0.3s ease;
  transform: translateX(-50%);
}

.nav-menu a:hover::after {
  width: 80%;
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.cart-icon {
  position: relative;
  font-size: 1.5rem;
  cursor: pointer;
  padding: 0.5rem;
  border-radius: 50%;
  transition: all 0.3s ease;
  background: rgba(52, 152, 219, 0.1);
}

.cart-icon:hover {
  background: rgba(52, 152, 219, 0.2);
  transform: scale(1.1);
}

.cart-badge {
  position: absolute;
  top: -5px;
  right: -5px;
  background: #e74c3c;
  color: white;
  font-size: 0.7rem;
  padding: 2px 6px;
  border-radius: 50%;
  min-width: 18px;
  text-align: center;
  font-weight: 600;
}

.nav-toggle {
  display: none;
  flex-direction: column;
  cursor: pointer;
  padding: 0.5rem;
}

.nav-toggle .bar {
  width: 25px;
  height: 3px;
  background-color: white;
  margin: 3px 0;
  transition: 0.3s;
  border-radius: 2px;
}

/* Mobile Responsive */
@media (max-width: 768px) {
  .nav-menu {
    position: fixed;
    left: -100%;
    top: 70px;
    flex-direction: column;
    background: rgba(44, 62, 80, 0.98);
    backdrop-filter: blur(10px);
    width: 100%;
    text-align: center;
    transition: 0.3s;
    box-shadow: 0 10px 27px rgba(0,0,0,0.1);
    padding: 2rem 0;
  }

  .nav-menu.active {
    left: 0;
  }

  .nav-menu li {
    margin: 1rem 0;
  }

  .nav-menu a {
    padding: 1rem 2rem;
    display: block;
    font-size: 1.1rem;
  }

  .nav-toggle {
    display: flex;
  }

  .nav-toggle.active .bar:nth-child(2) {
    opacity: 0;
  }

  .nav-toggle.active .bar:nth-child(1) {
    transform: translateY(8px) rotate(45deg);
  }

  .nav-toggle.active .bar:nth-child(3) {
    transform: translateY(-8px) rotate(-45deg);
  }
}
</style>