<template>
  <div class="bg-gray-50 antialiased">
    <Header />
    <main class="flex-auto">
      <Hero />
      <PrimaryFeatures />
      <SecondaryFeatures />
      <CallToAction />
      <Reviews />
      <Pricing />
      <Faqs />
    </main>
    <Footer />
  </div>
</template>

<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Hero from './components/Hero.vue'
import PrimaryFeatures from './components/PrimaryFeatures.vue'
import SecondaryFeatures from './components/SecondaryFeatures.vue'
import CallToAction from './components/CallToAction.vue'
import Reviews from './components/Reviews.vue'
import Pricing from './components/Pricing.vue'
import Faqs from './components/Faqs.vue'
</script>
