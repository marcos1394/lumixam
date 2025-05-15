<script setup>
import { onMounted } from 'vue';
import * as anime from 'animejs' // ✅

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        anime({
          targets: '.about-image',
          opacity: [0, 1],
          translateX: [-50, 0],
          duration: 1000,
          easing: 'easeOutExpo'
        });
        
        anime({
          targets: '.about-content',
          opacity: [0, 1],
          translateX: [50, 0],
          duration: 1000,
          delay: 300,
          easing: 'easeOutExpo'
        });
        
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.2 });
  
  observer.observe(document.querySelector('.about-section'));
});
</script>

<template>
  <section class="about-section py-20 bg-black relative overflow-hidden">
    <!-- Elementos decorativos de fondo -->
    <div class="absolute top-0 left-0 w-full h-20 bg-gradient-to-b from-gray-950 to-black"></div>
    <div class="absolute -left-16 top-40 w-32 h-32 rounded-full bg-gold-400 opacity-20 blur-xl"></div>
    <div class="absolute right-0 bottom-0 w-64 h-64 rounded-full bg-gold-400 opacity-10 blur-3xl"></div>
    
    <div class="container mx-auto px-6">
      <div class="flex flex-col lg:flex-row items-center gap-12">
        <div class="about-image opacity-0 lg:w-1/2">
          <div class="relative">
            <div class="absolute inset-0 border-2 border-gold-400 rounded-lg transform translate-x-4 translate-y-4"></div>
            <img src="../assets/about-workshop.jpg" alt="Nuestro taller artesanal" class="w-full h-auto rounded-lg relative z-10 shadow-xl" />
          </div>
        </div>
        
        <div class="about-content opacity-0 lg:w-1/2">
          <h4 class="text-gold-400 uppercase tracking-wider font-medium mb-2">Nuestra historia</h4>
          <h2 class="text-3xl md:text-4xl font-serif font-bold mb-6">Artesanía con <span class="text-gold-400">propósito</span></h2>
          
          <p class="text-gray-300 mb-6">
            En Luminous Essence, creamos cada vela con dedicación y respeto por la naturaleza. Desde 2018, nos hemos comprometido a elaborar productos 100% orgánicos, sustentables y libres de químicos nocivos.
          </p>
          
          <p class="text-gray-300 mb-8">
            Nuestra misión es transformar espacios ordinarios en santuarios de bienestar, conectando a las personas con los beneficios terapéuticos de los aromas naturales mientras cuidamos de nuestro planeta.
          </p>
          
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8">
            <div class="flex items-start">
              <div class="bg-gold-400 p-2 rounded-full mr-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-black" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
              </div>
              <div>
                <h4 class="font-bold text-white mb-1">Ingredientes orgánicos</h4>
                <p class="text-gray-400 text-sm">Cera de soya, aceites esenciales y colorantes naturales</p>
              </div>
            </div>
            
            <div class="flex items-start">
              <div class="bg-gold-400 p-2 rounded-full mr-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-black" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
              </div>
              <div>
                <h4 class="font-bold text-white mb-1">Hecho a mano</h4>
                <p class="text-gray-400 text-sm">Cada vela es creada artesanalmente con cuidado y atención</p>
              </div>
            </div>
            
            <div class="flex items-start">
              <div class="bg-gold-400 p-2 rounded-full mr-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-black" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
              </div>
              <div>
                <h4 class="font-bold text-white mb-1">Eco-amigable</h4>
                <p class="text-gray-400 text-sm">Envases reciclables y empaques biodegradables</p>
              </div>
            </div>
            
            <div class="flex items-start">
              <div class="bg-gold-400 p-2 rounded-full mr-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-black" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
              </div>
              <div>
                <h4 class="font-bold text-white mb-1">Libre de crueldad</h4>
                <p class="text-gray-400 text-sm">Nunca probamos en animales</p>
              </div>
            </div>
          </div>
          
          <a href="/sobre-nosotros" class="inline-flex items-center text-gold-400 hover:text-white transition-colors">
            <span class="font-medium">Conoce más sobre nuestra historia</span>
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
            </svg>
          </a>
        </div>
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
.hover\:text-gold-400:hover {
  color: #D4AF37;
}
</style>