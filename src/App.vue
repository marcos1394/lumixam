<script setup>
import Navbar from './components/Navbar.vue';
import Hero from './components/Hero.vue';
import FeaturedProducts from './components/FeaturedProducts.vue';
import AboutUs from './components/AboutUs.vue';
import Benefits from './components/Benefits.vue';
import Testimonials from './components/Testimonials.vue';
import NewsletterSignup from './components/NewsletterSignup.vue';
import Footer from './components/Footer.vue';
</script>

<template>
  <div class="min-h-screen bg-black text-white">
    <Navbar />
    <Hero />
    <FeaturedProducts />
    <AboutUs />
    <Benefits />
    <Testimonials />
    <NewsletterSignup />
    <Footer />
  </div>
</template>