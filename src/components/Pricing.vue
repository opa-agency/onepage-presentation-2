<template>
  <section
    id="pricing"
    aria-labelledby="pricing-title"
    class="border-t border-gray-200 bg-gray-100 py-20 sm:py-32"
  >
    <Container>
      <div class="mx-auto max-w-2xl text-center">
        <h2
          id="pricing-title"
          class="text-3xl font-medium tracking-tight text-gray-900"
        >
          Flat pricing, no management fees.
        </h2>
        <p class="mt-2 text-lg text-gray-600">
          Whether you're one person trying to get ahead or a big firm trying
          to take over the world, we've got a plan for you.
        </p>
      </div>

      <div class="mt-8 flex justify-center">
        <div class="relative grid grid-cols-2 rounded-lg border border-gray-300">
          <button
            v-for="period in ['Monthly', 'Annually']"
            :key="period"
            :class="[
              'cursor-pointer border border-gray-300 px-3 py-2 text-sm text-gray-700 transition-colors hover:border-gray-400',
              period === 'Monthly' ? 'rounded-l-lg' : '-ml-px rounded-r-lg'
            ]"
            @click="activePeriod = period"
          >
            {{ period }}
          </button>
          <div
            aria-hidden="true"
            :class="[
              'pointer-events-none absolute inset-0 z-10 grid grid-cols-2 overflow-hidden rounded-lg bg-cyan-500 transition-all duration-300',
              activePeriod === 'Monthly' ? 'clip-path-[inset(0_50%_0_0)]' : 'clip-path-[inset(0_0_0_calc(50%-1px))]'
            ]"
            :style="{
              clipPath: activePeriod === 'Monthly' ? 'inset(0 50% 0 0)' : 'inset(0 0 0 calc(50% - 1px))'
            }"
          >
            <div
              v-for="period in ['Monthly', 'Annually']"
              :key="period"
              :class="[
                'py-2 text-center text-sm font-semibold text-white',
                period === 'Annually' && '-ml-px'
              ]"
            >
              {{ period }}
            </div>
          </div>
        </div>
      </div>

      <div class="mx-auto mt-16 grid max-w-2xl grid-cols-1 items-start gap-x-8 gap-y-10 sm:mt-20 lg:max-w-none lg:grid-cols-3">
        <section
          v-for="plan in plans"
          :key="plan.name"
          :class="[
            'flex flex-col overflow-hidden rounded-3xl p-6 shadow-lg shadow-gray-900/5',
            plan.featured ? 'order-first bg-gray-900 lg:order-0' : 'bg-white'
          ]"
        >
          <h3 :class="['flex items-center text-sm font-semibold', plan.featured ? 'text-white' : 'text-gray-900']">
            <Logo mark :class="['h-6 w-6 flex-none', plan.logomarkClassName]" />
            <span class="ml-4">{{ plan.name }}</span>
          </h3>
          <p :class="['relative mt-5 flex text-3xl tracking-tight', plan.featured ? 'text-white' : 'text-gray-900']">
            {{ plan.price[activePeriod] }}
          </p>
          <p :class="['mt-3 text-sm', plan.featured ? 'text-gray-300' : 'text-gray-700']">
            {{ plan.description }}
          </p>
          <div class="order-last mt-6">
            <ul
              role="list"
              :class="[
                '-my-2 divide-y text-sm',
                plan.featured ? 'divide-gray-800 text-gray-300' : 'divide-gray-200 text-gray-700'
              ]"
            >
              <li v-for="feature in plan.features" :key="feature" class="flex py-2">
                <svg viewBox="0 0 24 24" aria-hidden="true" :class="['h-6 w-6 flex-none', plan.featured ? 'text-white' : 'text-cyan-500']">
                  <path
                    d="M9.307 12.248a.75.75 0 1 0-1.114 1.004l1.114-1.004ZM11 15.25l-.557.502a.75.75 0 0 0 1.15-.043L11 15.25Zm4.844-5.041a.75.75 0 0 0-1.188-.918l1.188.918Zm-7.651 3.043 2.25 2.5 1.114-1.004-2.25-2.5-1.114 1.004Zm3.4 2.457 4.25-5.5-1.187-.918-4.25 5.5 1.188.918Z"
                    fill="currentColor"
                  />
                  <circle cx="12" cy="12" r="8.25" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
                </svg>
                <span class="ml-4">{{ feature }}</span>
              </li>
            </ul>
          </div>
          <Button :href="plan.button.href" :color="plan.featured ? 'cyan' : 'gray'" class="mt-6">
            {{ plan.button.label }}
          </Button>
        </section>
      </div>
    </Container>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import Container from './Container.vue'
import Button from './Button.vue'
import Logo from './Logo.vue'

const activePeriod = ref('Monthly')

const plans = [
  {
    name: 'Starter',
    featured: false,
    price: { Monthly: '$0', Annually: '$0' },
    description: 'You\'re new to investing but want to do it right. Get started for free.',
    button: { label: 'Get started for free', href: '/register' },
    features: [
      'Commission-free trading',
      'Multi-layered encryption',
      'One tip every day',
      'Invest up to $1,500 each month'
    ],
    logomarkClassName: 'fill-gray-300'
  },
  {
    name: 'Investor',
    featured: false,
    price: { Monthly: '$7', Annually: '$70' },
    description: 'You\'ve been investing for a while. Invest more and grow your wealth faster.',
    button: { label: 'Subscribe', href: '/register' },
    features: [
      'Commission-free trading',
      'Multi-layered encryption',
      'One tip every hour',
      'Invest up to $15,000 each month',
      'Basic transaction anonymization'
    ],
    logomarkClassName: 'fill-gray-500'
  },
  {
    name: 'VIP',
    featured: true,
    price: { Monthly: '$199', Annually: '$1,990' },
    description: 'You\'ve got a huge amount of assets but it\'s not enough. To the moon.',
    button: { label: 'Subscribe', href: '/register' },
    features: [
      'Commission-free trading',
      'Multi-layered encryption',
      'Real-time tip notifications',
      'No investment limits',
      'Advanced transaction anonymization',
      'Automated tax-loss harvesting'
    ],
    logomarkClassName: 'fill-cyan-500'
  }
]
</script>
