<template>
  <template v-for="([label, href], index) in links" :key="label">
    <a
      :href="href"
      class="relative -mx-3 -my-2 rounded-lg px-3 py-2 text-sm text-gray-700 transition-colors delay-150 hover:text-gray-900 hover:delay-0"
      @mouseenter="handleMouseEnter(index)"
      @mouseleave="handleMouseLeave"
    >
      <Transition
        enter-active-class="transition duration-150"
        leave-active-class="transition duration-150"
        enter-from-class="opacity-0"
        enter-to-class="opacity-1"
        leave-from-class="opacity-1"
        leave-to-class="opacity-0"
      >
        <span
          v-if="hoveredIndex === index"
          class="absolute inset-0 rounded-lg bg-gray-100"
        />
      </Transition>
      <span class="relative z-10">{{ label }}</span>
    </a>
  </template>
</template>

<script setup>
import { ref } from 'vue'

const links = [
  ['Funcționalități', '/#features'],
  ['Recenzii', '/#reviews'],
  ['Prețuri', '/#pricing'],
  ['Întrebări frecvente', '/#faqs'],
]

const hoveredIndex = ref(null)
let timeoutRef = null

const handleMouseEnter = (index) => {
  if (timeoutRef) {
    clearTimeout(timeoutRef)
  }
  hoveredIndex.value = index
}

const handleMouseLeave = () => {
  timeoutRef = setTimeout(() => {
    hoveredIndex.value = null
  }, 200)
}
</script>
