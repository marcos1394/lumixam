<script setup>
import { ref } from 'vue'
import { Icon } from '@iconify/vue' // ✅ correcto

const year = new Date().getFullYear()

const footerLinks = ref([
  {
    title: 'Productos',
    links: [
      { text: 'Velas aromáticas', url: '/productos/velas' },
      { text: 'Difusores', url: '/productos/difusores' },
      { text: 'Aceites esenciales', url: '/productos/aceites' },
      { text: 'Kits de regalo', url: '/productos/kits' },
      { text: 'Nuevos lanzamientos', url: '/productos/nuevos' }
    ]
  },
  {
    title: 'Información',
    links: [
      { text: 'Sobre nosotros', url: '/sobre-nosotros' },
      { text: 'Beneficios', url: '/beneficios' },
      { text: 'Blog', url: '/blog' },
      { text: 'Preguntas frecuentes', url: '/faq' },
      { text: 'Contacto', url: '/contacto' }
    ]
  },
  {
    title: 'Legal',
    links: [
      { text: 'Términos y condiciones', url: '/terminos' },
      { text: 'Política de privacidad', url: '/privacidad' },
      { text: 'Política de envíos', url: '/envios' },
      { text: 'Política de devoluciones', url: '/devoluciones' },
      { text: 'Cookies', url: '/cookies' }
    ]
  }
])

const socialLinks = ref([
  { icon: 'mdi:instagram', url: 'https://instagram.com/luminousessence', label: 'Instagram' },
  { icon: 'mdi:facebook', url: 'https://facebook.com/luminousessence', label: 'Facebook' },
  { icon: 'mdi:pinterest', url: 'https://pinterest.com/luminousessence', label: 'Pinterest' },
  { icon: 'mdi:tiktok', url: 'https://tiktok.com/@luminousessence', label: 'TikTok' }
])

const email = ref('')
const subscribeNewsletter = () => {
  if (email.value) {
    alert('¡Gracias por suscribirte a nuestro newsletter!')
    email.value = ''
  }
}
</script>

<template>
  <footer class="bg-black border-t border-gray-800 pt-16 pb-8">
    <div class="container mx-auto px-6">
      <div class="grid grid-cols-1 md:grid-cols-5 gap-12">
        <!-- Logo y descripción -->
        <div class="md:col-span-2">
          <div class="flex items-center mb-6">
            <img src="/logo.svg" alt="Luminous Essence" class="h-10 mr-3" />
            <span class="text-gold-400 font-serif text-2xl font-bold">Lumixam Essence</span>
          </div>
          <p class="text-gray-400 mb-8">
            Velas aromáticas artesanales elaboradas con ingredientes orgánicos y sustentables para transformar tu espacio en un santuario de paz y bienestar.
          </p>

          <!-- Redes sociales -->
          <div class="mb-8">
            <h3 class="text-white font-medium mb-4">Síguenos</h3>
            <div class="flex space-x-4">
              <a
                v-for="social in socialLinks"
                :key="social.label"
                :href="social.url"
                :aria-label="social.label"
                class="text-gray-400 hover:text-gold-400 transition-colors duration-300"
                target="_blank"
                rel="noopener noreferrer"
              >
                <Icon :icon="social.icon" class="w-6 h-6" />
              </a>
            </div>
          </div>

          <!-- Información de contacto -->
          <div>
            <h3 class="text-white font-medium mb-4">Contáctanos</h3>
            <div class="text-gray-400">
              <p class="mb-2">Email: info@luminousessence.com</p>
              <p class="mb-2">Teléfono: +52 55 1234 5678</p>
              <p>Dirección: Av. Reforma 123, Col. Juárez, CDMX, México</p>
            </div>
          </div>
        </div>

        <!-- Links del footer -->
        <div
          v-for="category in footerLinks"
          :key="category.title"
          class="md:col-span-1"
        >
          <h3 class="text-white font-medium mb-6">{{ category.title }}</h3>
          <ul>
            <li
              v-for="link in category.links"
              :key="link.text"
              class="mb-3"
            >
              <a
                :href="link.url"
                class="text-gray-400 hover:text-gold-400 transition-colors duration-300"
              >
                {{ link.text }}
              </a>
            </li>
          </ul>
        </div>

        <!-- Newsletter -->
        <div class="md:col-span-1">
          <h3 class="text-white font-medium mb-6">Recibe nuestras novedades</h3>
          <p class="text-gray-400 mb-4">
            Suscríbete para recibir noticias sobre nuevos productos, ofertas especiales y consejos aromáticos.
          </p>
          <form @submit.prevent="subscribeNewsletter" class="space-y-3">
            <input
              v-model="email"
              type="email"
              placeholder="Tu correo electrónico"
              class="w-full bg-gray-900 border border-gray-700 text-gray-300 px-4 py-2 rounded focus:outline-none focus:border-gold-400"
              required
            />
            <button
              type="submit"
              class="w-full bg-gold-400 hover:bg-gold-500 text-black font-medium py-2 px-4 rounded transition-colors duration-300"
            >
              Suscribirse
            </button>
          </form>
        </div>
      </div>

      <!-- Separador -->
      <div class="border-t border-gray-800 my-8"></div>

      <!-- Copyright y métodos de pago -->
      <div class="flex flex-col md:flex-row justify-between items-center">
        <div class="text-gray-500 text-sm mb-4 md:mb-0">
          © {{ year }} Lumixam Essence. Todos los derechos reservados.
        </div>
        <div class="flex space-x-4 text-gray-400">
          <Icon icon="logos:visa" class="w-8 h-8 hover:text-gold-400 transition-colors" />
          <Icon icon="logos:mastercard" class="w-8 h-8 hover:text-gold-400 transition-colors" />
          <Icon icon="logos:paypal" class="w-8 h-8 hover:text-gold-400 transition-colors" />
          <Icon icon="mdi:credit-card-outline" class="w-8 h-8 hover:text-gold-400 transition-colors" />
        </div>
      </div>
    </div>
  </footer>
</template>
