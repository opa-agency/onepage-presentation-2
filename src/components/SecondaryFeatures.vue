<template>
  <section
    id="secondary-features"
    aria-label="Funcționalități pentru construirea unui portofoliu"
    class="py-20 sm:py-32"
  >
    <Container>
      <div class="mx-auto max-w-2xl sm:text-center">
        <h2 class="text-3xl font-medium tracking-tight text-gray-900">
          Acum este momentul să-ți construiești portofoliul.
        </h2>
        <p class="mt-2 text-lg text-gray-600">
          Cu profiturile tipice ale pieței, trebuie să începi tânăr pentru a-ți asigura
          viitorul. Cu Pocket, nu este niciodată prea târziu să-ți construiești economiile.
        </p>
      </div>
      <ul
        role="list"
        class="mx-auto mt-16 grid max-w-2xl grid-cols-1 gap-6 text-sm sm:mt-20 sm:grid-cols-2 md:gap-y-10 lg:max-w-none lg:grid-cols-3"
      >
        <li
          v-for="feature in features"
          :key="feature.name"
          class="rounded-2xl border border-gray-200 p-8"
        >
          <component :is="feature.icon" class="h-8 w-8" />
          <h3 class="mt-6 font-semibold text-gray-900">
            {{ feature.name }}
          </h3>
          <p class="mt-2 text-gray-700">{{ feature.description }}</p>
        </li>
      </ul>
    </Container>
  </section>
</template>

<script setup>
import { h, defineComponent } from 'vue'
import Container from './Container.vue'

const DeviceArrowIcon = defineComponent({
  setup(props, { attrs }) {
    return () => h('svg', { viewBox: '0 0 32 32', 'aria-hidden': 'true', ...attrs }, [
      h('path', {
        'fill-rule': 'evenodd',
        'clip-rule': 'evenodd',
        d: 'M9 0a4 4 0 00-4 4v24a4 4 0 004 4h14a4 4 0 004-4V4a4 4 0 00-4-4H9zm0 2a2 2 0 00-2 2v24a2 2 0 002 2h14a2 2 0 002-2V4a2 2 0 00-2-2h-1.382a1 1 0 00-.894.553l-.448.894a1 1 0 01-.894.553h-6.764a1 1 0 01-.894-.553l-.448-.894A1 1 0 0010.382 2H9z',
        fill: '#737373'
      }),
      h('path', {
        d: 'M12 25l8-8m0 0h-6m6 0v6',
        stroke: '#171717',
        'stroke-width': '2',
        'stroke-linecap': 'round'
      }),
      h('circle', { cx: '16', cy: '16', r: '16', fill: '#A3A3A3', 'fill-opacity': '0.2' })
    ])
  }
})

const features = [
  {
    name: 'Investește orice sumă',
    description: 'Fie că este 1$ sau 1.000.000$, putem pune banii tăi să lucreze pentru tine.',
    icon: DeviceArrowIcon
  },
  {
    name: 'Construiește un portofoliu echilibrat',
    description: 'Investește în diferite industrii pentru a găsi cele mai multe oportunități de a câștiga mare.',
    icon: DeviceArrowIcon
  },
  {
    name: 'Tranzacționează în timp real',
    description: 'Primește sfaturi din interior despre mișcările mari ale acțiunilor și acționează asupra lor în secunde.',
    icon: DeviceArrowIcon
  },
  {
    name: 'Profită din rețeaua ta',
    description: 'Invită noi insider pentru a primi sfaturi mai rapid și a întrece chiar și alți utilizatori Pocket.',
    icon: DeviceArrowIcon
  },
  {
    name: 'Criptat și anonimizat',
    description: 'Tehnologia de securitate de ultimă generație pe care nici măcar NSA nu o cunoaște te ține ascuns.',
    icon: DeviceArrowIcon
  },
  {
    name: 'Urmărirea portofoliului',
    description: 'Urmărește cum investițiile tale cresc exponențial, lăsând alți investitori în urmă.',
    icon: DeviceArrowIcon
  }
]
</script>
