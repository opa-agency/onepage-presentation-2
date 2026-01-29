<template>
  <section
    id="get-free-shares-today"
    class="relative overflow-hidden bg-gray-900 py-20 sm:py-28"
  >
    <div class="absolute top-1/2 left-20 -translate-y-1/2 sm:left-1/2 sm:-translate-x-1/2">
      <CircleBackground color="#fff" class="animate-spin-slower" />
    </div>
    <Container class="relative">
      <div class="mx-auto max-w-md sm:text-center">
        <h2 class="text-3xl font-medium tracking-tight text-white sm:text-4xl">
          Get your first tips today
        </h2>
        <p class="mt-4 text-lg text-gray-300">
          It takes 30 seconds to sign up. Download the app and create an
          account today and we'll send you a tip guaranteed to double your
          first investment.
        </p>
        <div class="mt-8 flex justify-center">
          <AppStoreLink color="white" />
        </div>
      </div>
    </Container>
  </section>
</template>

<script setup>
import AppStoreLink from './AppStoreLink.vue'
import CircleBackground from './CircleBackground.vue'
import Container from './Container.vue'
</script>
