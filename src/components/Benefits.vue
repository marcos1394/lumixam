<script setup>
import { ref, onMounted } from 'vue';
import * as anime from 'animejs' // ✅

const benefits = ref([
  {
    id: 1,
    title: 'Reduce el estrés y la ansiedad',
    description: 'Los aromas naturales como la lavanda y la manzanilla activan receptores en el cerebro que ayudan a reducir el estrés y promover la relajación.',
    icon: 'M14.828 14.828a4 4 0 01-5.656 0M9 10h.01M15 10h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z'
  },
  {
    id: 2,
    title: 'Mejora la calidad del sueño',
    description: 'Ciertos aromas como lavanda y bergamota han demostrado científicamente mejorar la calidad del sueño y reducir el insomnio.',
    icon: 'M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z'
  },
  {
    id: 3,
    title: 'Estimula la concentración',
    description: 'Aromas como romero, menta y limón pueden mejorar la capacidad cognitiva, la concentración y el rendimiento mental.',
    icon: 'M12 18h.01M8 21h8a2 2 0 002-2V5a2 2 0 00-2-2H8a2 2 0 00-2 2v14a2 2 0 002 2z'
  },
  {
    id: 4,
    title: 'Purifica el ambiente',
    description: 'Nuestras velas de eucalipto, árbol de té y limón ayudan a purificar el aire y eliminar bacterias del ambiente.',
    icon: 'M3 15a4 4 0 004 4h9a5 5 0 10-.1-9.999 5.002 5.002 0 10-9.78 2.096A4.001 4.001 0 003 15z'
  },
  {
    id: 5,
    title: 'Crea atmósferas únicas',
    description: 'Transforma cualquier espacio en un santuario de calma, un templo de meditación o un refugio sensorial.',
    icon: 'M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z'
  },
  {
    id: 6,
    title: 'Mejora el estado de ánimo',
    description: 'Los aceites cítricos como naranja y pomelo aumentan los niveles de serotonina, ayudando a mejorar el estado de ánimo.',
    icon: 'M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z'
  }
]);

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        anime({
          targets: '.benefits-title',
          opacity: [0, 1],
          translateY: [20, 0],
          duration: 800,
          easing: 'easeOutExpo'
        });
        
        anime({
          targets: '.benefit-card',
          opacity: [0, 1],
          translateY: [40, 0],
          duration: 800,
          delay: anime.stagger(100, {start: 300}),
          easing: 'easeOutExpo'
        });
        
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });
  
  observer.observe(document.querySelector('.benefits-section'));
});
</script>

<template>
    <section class="benefits-section py-20 bg-gradient-to-b from-black to-gray-900 relative">
      <!-- Elementos decorativos -->
      <div class="absolute top-0 w-full h-px bg-gradient-to-r from-transparent via-gold-400 to-transparent opacity-30"></div>
      <div class="absolute -right-40 top-20 w-80 h-80 rounded-full bg-gold-400 opacity-5 blur-3xl"></div>
      <div class="absolute -left-20 bottom-40 w-60 h-60 rounded-full bg-gold-400 opacity-10 blur-3xl"></div>
      
      <div class="container mx-auto px-6">
        <div class="text-center max-w-3xl mx-auto mb-16">
          <h2 class="benefits-title opacity-0 text-3xl md:text-4xl font-serif font-bold mb-6">
            Los <span class="text-gold-400">Beneficios</span> de la Aromaterapia
          </h2>
          <p class="text-gray-400">
            La aromaterapia ha sido utilizada durante miles de años por diversas culturas para mejorar la salud física y mental. Descubre cómo nuestras velas pueden transformar tu bienestar.
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="benefit in benefits" :key="benefit.id" class="benefit-card opacity-0 bg-gray-900 border border-gray-800 hover:border-gold-400 rounded-lg p-8 transition-all duration-300 hover:transform hover:translate-y-[-5px] hover:shadow-lg">
            <div class="bg-black p-4 rounded-full inline-flex items-center justify-center mb-6 border border-gold-400">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-gold-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" :d="benefit.icon" />
              </svg>
            </div>
            <h3 class="text-xl font-serif font-semibold mb-4">{{ benefit.title }}</h3>
            <p class="text-gray-400">{{ benefit.description }}</p>
          </div>
        </div>
        
        <div class="mt-16 text-center">
          <a href="/blog/beneficios-aromaterapia" class="text-gold-400 hover:text-white inline-flex items-center transition-colors">
            <span class="font-medium">Explora más beneficios en nuestro blog</span>
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
            </svg>
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
  .hover\:border-gold-400:hover {
    border-color: #D4AF37;
  }
  .hover\:text-gold-400:hover {
    color: #D4AF37;
  }
  .via-gold-400 {
    --tw-gradient-via-color: #D4AF37;
  }
  </style>