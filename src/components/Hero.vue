<script setup>
import { onMounted } from 'vue';
import * as anime from 'animejs'

onMounted(() => {
  // Animación para el título
  anime({
    targets: '.hero-title',
    opacity: [0, 1],
    translateY: [50, 0],
    duration: 1200,
    easing: 'easeOutExpo',
    delay: 300
  });

  // Animación para la descripción
  anime({
    targets: '.hero-description',
    opacity: [0, 1],
    translateY: [30, 0],
    duration: 1200,
    easing: 'easeOutExpo',
    delay: 600
  });

  // Animación para el botón
  anime({
    targets: '.hero-button',
    opacity: [0, 1],
    translateY: [20, 0],
    duration: 1000,
    easing: 'easeOutExpo',
    delay: 900
  });

  // Animación para decoración
  anime({
    targets: '.hero-decoration',
    opacity: [0, 0.8],
    duration: 2000,
    easing: 'easeInOutQuad',
    delay: 200
  });
});
</script>

<template>
  <section class="relative py-20 md:py-32 overflow-hidden">
    <!-- Fondo con patrón dorado -->
    <div class="absolute inset-0 bg-black opacity-80 z-0"></div>
    <div class="hero-decoration absolute inset-0 bg-[url('/pattern-gold.svg')] bg-repeat opacity-0 z-0"></div>
    
    <div class="container mx-auto px-6 relative z-10">
      <div class="max-w-3xl mx-auto text-center">
        <h1 class="hero-title opacity-0 text-4xl md:text-6xl font-serif font-bold mb-6 text-white">
          <span class="text-gold-400">Velas Aromáticas</span> Terapéuticas <span class="text-gold-400">Orgánicas</span>
        </h1>
        <p class="hero-description opacity-0 text-lg md:text-xl text-gray-300 mb-8">
          Descubre el poder de la aromaterapia con nuestras velas artesanales elaboradas con ingredientes 100% naturales y orgánicos. Transforma tu espacio en un santuario de paz y bienestar.
        </p>
        <div class="flex justify-center">
          <a href="#products" class="hero-button opacity-0 bg-gold-400 hover:bg-gold-500 text-black font-bold py-3 px-8 rounded-full transition-all duration-300 inline-block">
            Descubrir Colección
          </a>
        </div>
      </div>
    </div>

    <!-- Elementos decorativos -->
    <div class="absolute -bottom-16 left-0 w-64 h-64 rounded-full bg-gold-400 opacity-10 blur-3xl"></div>
    <div class="absolute -top-32 right-0 w-96 h-96 rounded-full bg-gold-400 opacity-10 blur-3xl"></div>
  </section>
</template>

<style scoped>
.text-gold-400 {
  color: #D4AF37;
}
.bg-gold-400 {
  background-color: #D4AF37;
}
.bg-gold-500 {
  background-color: #B8860B;
}
.hover\:bg-gold-500:hover {
  background-color: #B8860B;
}
</style>