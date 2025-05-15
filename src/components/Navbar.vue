<script setup>
import { ref } from 'vue';

const isMenuOpen = ref(false);
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<template>
  <nav class="bg-black border-b border-gold-400 px-6 py-4">
    <div class="container mx-auto flex justify-between items-center">
      <div class="flex items-center">
        <img src="/logo.svg" alt="Luminous Essence" class="h-10 mr-3" />
        <span class="text-gold-400 font-serif text-2xl font-bold">Luminous Essence</span>
      </div>

      <!-- Desktop Menu -->
      <div class="hidden md:flex space-x-8">
        <a href="#" class="text-white hover:text-gold-400 transition-colors">Inicio</a>
        <a href="#" class="text-white hover:text-gold-400 transition-colors">Productos</a>
        <a href="#" class="text-white hover:text-gold-400 transition-colors">Beneficios</a>
        <a href="#" class="text-white hover:text-gold-400 transition-colors">Sobre Nosotros</a>
        <a href="#" class="text-white hover:text-gold-400 transition-colors">Contacto</a>
      </div>

      <!-- Shopping Cart Icon -->
      <div class="hidden md:flex items-center">
        <button class="relative text-white hover:text-gold-400 transition-colors">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
          </svg>
          <span class="absolute -top-2 -right-2 bg-gold-400 text-black rounded-full h-5 w-5 flex items-center justify-center text-xs font-bold">0</span>
        </button>
      </div>

      <!-- Mobile Menu Button -->
      <div class="md:hidden">
        <button @click="toggleMenu" class="text-white focus:outline-none">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>
    </div>

    <!-- Mobile Menu -->
    <div v-if="isMenuOpen" class="md:hidden pt-4 pb-2 border-t border-gold-400 mt-4">
      <div class="flex flex-col space-y-3">
        <a href="#" class="text-white hover:text-gold-400 transition-colors px-4">Inicio</a>
        <a href="#" class="text-white hover:text-gold-400 transition-colors px-4">Productos</a>
        <a href="#" class="text-white hover:text-gold-400 transition-colors px-4">Beneficios</a>
        <a href="#" class="text-white hover:text-gold-400 transition-colors px-4">Sobre Nosotros</a>
        <a href="#" class="text-white hover:text-gold-400 transition-colors px-4">Contacto</a>
        <div class="px-4 pt-2 flex items-center">
          <button class="relative text-white hover:text-gold-400 transition-colors">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
            </svg>
            <span class="absolute -top-2 -right-2 bg-gold-400 text-black rounded-full h-5 w-5 flex items-center justify-center text-xs font-bold">0</span>
          </button>
          <span class="ml-2 text-white">Carrito</span>
        </div>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.text-gold-400 {
  color: #D4AF37;
}
.border-gold-400 {
  border-color: #D4AF37;
}
.bg-gold-400 {
  background-color: #D4AF37;
}
.hover\:text-gold-400:hover {
  color: #D4AF37;
}
</style>