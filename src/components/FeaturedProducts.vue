<script setup>
import { ref, onMounted } from 'vue';
import * as anime from 'animejs'

const products = ref([
  {
    id: 1,
    name: 'Lavanda Relajante',
    description: 'Perfecta para aliviar el estrés y mejorar el sueño',
    price: 299,
    image: '/product-lavender.jpg',
    category: 'Relajación'
  },
  {
    id: 2,
    name: 'Canela & Naranja',
    description: 'Estimula la concentración y el buen humor',
    price: 329,
    image: '/product-cinnamon.jpg',
    category: 'Energizante'
  },
  {
    id: 3,
    name: 'Eucalipto Purificante',
    description: 'Limpia el ambiente y mejora la respiración',
    price: 279,
    image: '/product-eucalyptus.jpg',
    category: 'Purificación'
  },
  {
    id: 4,
    name: 'Sándalo & Jazmín',
    description: 'Crea un ambiente relajante y sensual',
    price: 349,
    image: '/product-sandalwood.jpg',
    category: 'Armonía'
  }
]);

onMounted(() => {
  anime({
    targets: '.section-title',
    opacity: [0, 1],
    translateY: [20, 0],
    duration: 800,
    easing: 'easeOutExpo',
    delay: 300
  });
  
  anime({
    targets: '.product-card',
    opacity: [0, 1],
    translateY: [30, 0],
    duration: 800,
    delay: anime.stagger(150, {start: 500}),
    easing: 'easeOutExpo'
  });
});
</script>

<template>
  <section id="products" class="py-16 bg-gray-950">
    <div class="container mx-auto px-6">
      <h2 class="section-title text-3xl md:text-4xl font-serif font-bold mb-2 text-center">
        <span class="text-gold-400">Nuestras</span> Velas Destacadas
      </h2>
      <p class="text-gray-400 mb-12 text-center max-w-2xl mx-auto">
        Cada vela es elaborada artesanalmente con cera de soya, aceites esenciales puros y mechas de algodón orgánico para una experiencia aromática excepcional.
      </p>
      
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
        <div v-for="product in products" :key="product.id" class="product-card bg-black border border-gray-800 rounded-lg overflow-hidden transition-transform duration-300 hover:transform hover:scale-105 hover:border-gold-400">
          <div class="h-64 overflow-hidden">
            <img :src="product.image" :alt="product.name" class="w-full h-full object-cover transition-transform duration-500 hover:scale-110" />
          </div>
          <div class="p-6">
            <span class="text-xs text-gold-400 font-medium uppercase tracking-wider">{{ product.category }}</span>
            <h3 class="font-serif text-xl font-semibold mt-2 mb-2">{{ product.name }}</h3>
            <p class="text-gray-400 text-sm mb-4">{{ product.description }}</p>
            <div class="flex justify-between items-center">
              <span class="text-gold-400 font-bold">${{ product.price.toFixed(2) }}</span>
              <button class="bg-black border border-gold-400 text-gold-400 hover:bg-gold-400 hover:text-black transition-colors duration-300 py-2 px-4 rounded-full text-sm font-medium">
                Añadir al carrito
              </button>
            </div>
          </div>
        </div>
      </div>
      
      <div class="text-center mt-12">
        <a href="/productos" class="bg-transparent border-2 border-gold-400 text-gold-400 hover:bg-gold-400 hover:text-black transition-colors duration-300 font-bold py-3 px-8 rounded-full inline-block">
          Ver toda la colección
        </a>
      </div>
    </div>
  </section>
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
.hover\:bg-gold-400:hover {
  background-color: #D4AF37;
}
.hover\:text-gold-400:hover {
  color: #D4AF37;
}
.hover\:border-gold-400:hover {
  border-color: #D4AF37;
}
</style>