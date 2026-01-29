<template>
  <section
    id="secondary-features"
    aria-label="Features for building a portfolio"
    class="py-20 sm:py-32"
  >
    <Container>
      <div class="mx-auto max-w-2xl sm:text-center">
        <h2 class="text-3xl font-medium tracking-tight text-gray-900">
          Now is the time to build your portfolio.
        </h2>
        <p class="mt-2 text-lg text-gray-600">
          With typical market returns, you have to start young to secure your
          future. With Pocket, it's never too late to build your nest egg.
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
    name: 'Invest any amount',
    description: 'Whether it is $1 or $1,000,000, we can put your money to work for you.',
    icon: DeviceArrowIcon
  },
  {
    name: 'Build a balanced portfolio',
    description: 'Invest in different industries to find the most opportunities to win huge.',
    icon: DeviceArrowIcon
  },
  {
    name: 'Trade in real-time',
    description: 'Get insider tips on big stock moves and act on them within seconds.',
    icon: DeviceArrowIcon
  },
  {
    name: 'Profit from your network',
    description: 'Invite new insiders to get tips faster and beat even other Pocket users.',
    icon: DeviceArrowIcon
  },
  {
    name: 'Encrypted and anonymized',
    description: 'Cutting-edge security technology that even the NSA does not know about keeps you hidden.',
    icon: DeviceArrowIcon
  },
  {
    name: 'Portfolio tracking',
    description: 'Watch your investments grow exponentially, leaving other investors in the dust.',
    icon: DeviceArrowIcon
  }
]
</script>
