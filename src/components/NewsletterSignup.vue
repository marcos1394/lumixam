<script setup>
import { ref, onMounted } from 'vue';
import * as anime from 'animejs' // ✅

const testimonials = ref([
  {
    id: 1,
    name: "María García",
    role: "Cliente habitual",
    image: "/testimonial-1.jpg",
    quote: "Las velas de Luminous Essence han transformado mi rutina de meditación. La fragancia de lavanda me ayuda a relajarme después de un largo día de trabajo."
  },
  {
    id: 2,
    name: "Carlos Mendoza",
    role: "Instructor de yoga",
    image: "/testimonial-2.jpg",
    quote: "Utilizo estas velas en todas mis clases. Mis alumnos siempre comentan sobre el ambiente relajante que crean y la calidad de los aromas naturales."
  },
  {
    id: 3,
    name: "Laura Torres",
    role: "Terapeuta holística",
    image: "/testimonial-3.jpg",
    quote: "Como terapeuta, valoro mucho trabajar con productos orgánicos y sustentables. Estas velas complementan perfectamente mi práctica profesional."
  }
]);

const currentTestimonial = ref(0);

const nextTestimonial = () => {
  if (currentTestimonial.value < testimonials.value.length - 1) {
    currentTestimonial.value++;
  } else {
    currentTestimonial.value = 0;
  }
  animateTestimonial();
};

const prevTestimonial = () => {
  if (currentTestimonial.value > 0) {
    currentTestimonial.value--;
  } else {
    currentTestimonial.value = testimonials.value.length - 1;
  }
  animateTestimonial();
};

const animateTestimonial = () => {
  anime({
    targets: '.testimonial-content',
    opacity: [0, 1],
    translateX: [20, 0],
    duration: 800,
    easing: 'easeOutExpo'
  });
};

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        anime({
          targets: '.testimonials-title',
          opacity: [0, 1],
          translateY: [20, 0],
          duration: 800,
          easing: 'easeOutExpo'
        });
        
        anime({
          targets: '.testimonial-card',
          opacity: [0, 1],
          translateY: [30, 0],
          duration: 1000,
          easing: 'easeOutExpo',
          delay: 300
        });
        
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.2 });
  
  observer.observe(document.querySelector('.testimonials-section'));
  
  // Auto rotate testimonials
  setInterval(nextTestimonial, 8000);
});
</script>

<template>
  <section class="testimonials-section py-20 bg-black relative overflow-hidden">
    <!-- Elementos decorativos -->
    <div class="absolute inset-0 bg-[url('/pattern-gold.svg')] bg-repeat opacity-5"></div>
    <div class="absolute -left-20 top-0 w-40 h-40 rounded-full bg-gold-400 opacity-10 blur-2xl"></div>
    <div class="absolute right-10 bottom-10 w-60 h-60 rounded-full bg-gold-400 opacity-5 blur-3xl"></div>
    
    <div class="container mx-auto px-6 relative z-10">
      <div class="text-center mb-12">
        <h2 class="testimonials-title opacity-0 text-3xl md:text-4xl font-serif font-bold mb-4">
          Lo que nuestros <span class="text-gold-400">clientes</span> dicen
        </h2>
        <div class="h-px w-24 bg-gold-400 mx-auto"></div>
      </div>
      
      <div class="testimonial-card opacity-0 max-w-4xl mx-auto bg-gray-900 rounded-xl shadow-xl overflow-hidden">
        <div class="flex flex-col md:flex-row">
          <div class="md:w-1/3 relative">
            <img :src="testimonials[currentTestimonial].image" :alt="testimonials[currentTestimonial].name" class="w-full h-full object-cover" />
            <div class="absolute inset-0 bg-gradient-to-t from-black via-transparent to-transparent md:bg-gradient-to-r"></div>
          </div>
          
          <div class="md:w-2/3 p-8 md:p-12">
            <div class="testimonial-content">
              <svg class="h-8 w-8 text-gold-400 mb-6" fill="currentColor" viewBox="0 0 32 32">
                <path d="M14 2l-4 4H2v8h8l4-4v-8zM30 2l-4 4H18v8h8l4-4v-8z"></path>
              </svg>
              
              <p class="text-lg text-gray-300 mb-6">{{ testimonials[currentTestimonial].quote }}</p>
              
              <div class="flex items-center">
                <div class="mr-4">
                  <div class="h-px w-12 bg-gold-400"></div>
                </div>
                <div>
                  <h4 class="font-bold text-white">{{ testimonials[currentTestimonial].name }}</h4>
                  <p class="text-gray-400 text-sm">{{ testimonials[currentTestimonial].role }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
        
        <div class="flex justify-between items-center px-6 py-4 bg-gray-950">
          <button @click="prevTestimonial" class="p-2 text-gray-400 hover:text-gold-400 transition-colors">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
            </svg>
          </button>
          
          <div class="flex space-x-2">
            <div v-for="(_, index) in testimonials" :key="index" 
                 :class="[
                   'h-2 w-2 rounded-full transition-all duration-300',
                   index === currentTestimonial ? 'bg-gold-400 w-6' : 'bg-gray-700'
                 ]">
            </div>
          </div>
          
          <button @click="nextTestimonial" class="p-2 text-gray-400 hover:text-gold-400 transition-colors">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.text-gold-400 {
  color: #D4AF37;
}
.bg-gold-400 {
  background-color: #D4AF37;
}
.hover\:text-gold-400:hover {
  color: #D4AF37;
}
</style>