<template>
  <section
    id="features"
    aria-label="Features for investing all your money"
    class="bg-gray-900 py-20 sm:py-32"
  >
    <Container>
      <div class="mx-auto max-w-2xl lg:mx-0 lg:max-w-3xl">
        <h2 class="text-3xl font-medium tracking-tight text-white">
          Every feature you need to win. Try it for yourself.
        </h2>
        <p class="mt-2 text-lg text-gray-400">
          Pocket was built for investors like you who play by their own rules and
          aren't going to let SEC regulations get in the way of their dreams. If
          other investing tools are afraid to build it, Pocket has it.
        </p>
      </div>
    </Container>
    <div class="mt-16 md:hidden">
      <div class="-mb-4 flex snap-x snap-mandatory -space-x-4 overflow-x-auto overscroll-x-contain scroll-smooth pb-4 sm:-space-x-6" style="scrollbar-width: none">
        <div v-for="(feature, index) in features" :key="index" class="w-full flex-none snap-center px-4 sm:px-6">
          <div class="relative transform overflow-hidden rounded-2xl bg-gray-800 px-5 py-6">
            <div class="absolute -right-4 -top-4">
              <CircleBackground color="#13B5C8" class="h-40 w-40 animate-spin-slower" />
            </div>
            <PhoneFrame class="relative mx-auto w-full max-w-[366px]">
              <component :is="feature.screen" />
            </PhoneFrame>
            <div class="absolute inset-x-0 bottom-0 bg-gray-800/95 p-6 backdrop-blur sm:p-10">
              <component :is="feature.icon" class="h-8 w-8" />
              <h3 class="mt-6 text-sm font-semibold text-white sm:text-lg">
                {{ feature.name }}
              </h3>
              <p class="mt-2 text-sm text-gray-400">
                {{ feature.description }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <Container class="hidden md:mt-20 md:block">
      <div class="grid grid-cols-12 items-center gap-8 lg:gap-16 xl:gap-24">
        <div class="relative col-span-6">
          <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2">
            <CircleBackground color="#13B5C8" class="animate-spin-slower" />
          </div>
          <PhoneFrame class="z-10 mx-auto w-full max-w-[366px]">
            <component :is="features[selectedIndex].screen" />
          </PhoneFrame>
        </div>
        <div class="relative z-10 order-last col-span-6 space-y-6">
          <div
            v-for="(feature, featureIndex) in features"
            :key="feature.name"
            class="relative rounded-2xl transition-colors hover:bg-gray-800/30 cursor-pointer"
            @click="selectedIndex = featureIndex"
          >
            <div
              v-if="featureIndex === selectedIndex"
              class="absolute inset-0 bg-gray-800 rounded-2xl"
            />
            <div class="relative z-10 p-8">
              <component :is="feature.icon" class="h-8 w-8" />
              <h3 class="mt-6 text-lg font-semibold text-white">
                {{ feature.name }}
              </h3>
              <p class="mt-2 text-sm text-gray-400">
                {{ feature.description }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </Container>
  </section>
</template>

<script setup>
import { ref, defineComponent, h } from 'vue'
import Container from './Container.vue'
import CircleBackground from './CircleBackground.vue'
import PhoneFrame from './PhoneFrame.vue'
import AppScreen from './AppScreen.vue'
import AppScreenHeader from './AppScreenHeader.vue'
import AppScreenTitle from './AppScreenTitle.vue'
import AppScreenSubtitle from './AppScreenSubtitle.vue'
import AppScreenBody from './AppScreenBody.vue'

const selectedIndex = ref(0)

// Icon components
const DeviceUserIcon = defineComponent({
  setup(props) {
    return () => h('svg', { viewBox: '0 0 32 32', 'aria-hidden': 'true', ...props }, [
      h('circle', { cx: 16, cy: 16, r: 16, fill: '#A3A3A3', 'fill-opacity': 0.2 }),
      h('path', {
        'fill-rule': 'evenodd',
        'clip-rule': 'evenodd',
        d: 'M16 23a3 3 0 100-6 3 3 0 000 6zm-1 2a4 4 0 00-4 4v1a2 2 0 002 2h6a2 2 0 002-2v-1a4 4 0 00-4-4h-2z',
        fill: '#737373'
      }),
      h('path', {
        'fill-rule': 'evenodd',
        'clip-rule': 'evenodd',
        d: 'M5 4a4 4 0 014-4h14a4 4 0 014 4v24a4.002 4.002 0 01-3.01 3.877c-.535.136-.99-.325-.99-.877s.474-.98.959-1.244A2 2 0 0025 28V4a2 2 0 00-2-2h-1.382a1 1 0 00-.894.553l-.448.894a1 1 0 01-.894.553h-6.764a1 1 0 01-.894-.553l-.448-.894A1 1 0 0010.382 2H9a2 2 0 00-2 2v24a2 2 0 001.041 1.756C8.525 30.02 9 30.448 9 31s-.455 1.013-.99.877A4.002 4.002 0 015 28V4z',
        fill: '#A3A3A3'
      })
    ])
  }
})

const DeviceNotificationIcon = defineComponent({
  setup(props) {
    return () => h('svg', { viewBox: '0 0 32 32', 'aria-hidden': 'true', ...props }, [
      h('circle', { cx: 16, cy: 16, r: 16, fill: '#A3A3A3', 'fill-opacity': 0.2 }),
      h('path', {
        'fill-rule': 'evenodd',
        'clip-rule': 'evenodd',
        d: 'M9 0a4 4 0 00-4 4v24a4 4 0 004 4h14a4 4 0 004-4V4a4 4 0 00-4-4H9zm0 2a2 2 0 00-2 2v24a2 2 0 002 2h14a2 2 0 002-2V4a2 2 0 00-2-2h-1.382a1 1 0 00-.894.553l-.448.894a1 1 0 01-.894.553h-6.764a1 1 0 01-.894-.553l-.448-.894A1 1 0 0010.382 2H9z',
        fill: '#A3A3A3'
      }),
      h('path', {
        d: 'M9 8a2 2 0 012-2h10a2 2 0 012 2v2a2 2 0 01-2 2H11a2 2 0 01-2-2V8z',
        fill: '#737373'
      })
    ])
  }
})

const DeviceTouchIcon = defineComponent({
  setup(props) {
    const id = Math.random().toString(36).substr(2, 9)
    return () => h('svg', { viewBox: '0 0 32 32', fill: 'none', 'aria-hidden': 'true', ...props }, [
      h('defs', {}, [
        h('linearGradient', { id: `${id}-gradient`, x1: 14, y1: 14.5, x2: 7, y2: 17, gradientUnits: 'userSpaceOnUse' }, [
          h('stop', { 'stop-color': '#737373' }),
          h('stop', { offset: 1, 'stop-color': '#D4D4D4', 'stop-opacity': 0 })
        ])
      ]),
      h('circle', { cx: 16, cy: 16, r: 16, fill: '#A3A3A3', 'fill-opacity': 0.2 }),
      h('path', {
        'fill-rule': 'evenodd',
        'clip-rule': 'evenodd',
        d: 'M5 4a4 4 0 014-4h14a4 4 0 014 4v13h-2V4a2 2 0 00-2-2h-1.382a1 1 0 00-.894.553l-.448.894a1 1 0 01-.894.553h-6.764a1 1 0 01-.894-.553l-.448-.894A1 1 0 0010.382 2H9a2 2 0 00-2 2v24a2 2 0 002 2h4v2H9a4 4 0 01-4-4V4z',
        fill: '#A3A3A3'
      }),
      h('path', {
        d: 'M7 22c0-4.694 3.5-8 8-8',
        stroke: `url(#${id}-gradient)`,
        'stroke-width': 2,
        'stroke-linecap': 'round',
        'stroke-linejoin': 'round'
      }),
      h('path', {
        d: 'M21 20l.217-5.513a1.431 1.431 0 00-2.85-.226L17.5 21.5l-1.51-1.51a2.107 2.107 0 00-2.98 0 .024.024 0 00-.005.024l3.083 9.25A4 4 0 0019.883 32H25a4 4 0 004-4v-5a3 3 0 00-3-3h-5z',
        fill: '#A3A3A3'
      })
    ])
  }
})

// Screen components
const InviteScreen = defineComponent({
  setup() {
    return () => h(AppScreen, { class: 'w-full' }, () => [
      h(AppScreenHeader, {}, () => [
        h(AppScreenTitle, {}, () => 'Invite people'),
        h(AppScreenSubtitle, {}, () => [
          'Get tips ',
          h('span', { class: 'text-white' }, '5s sooner'),
          ' for every invite.'
        ])
      ]),
      h(AppScreenBody, {}, () => h('div', { class: 'px-4 py-6' }, [
        h('div', { class: 'space-y-6' }, [
          h('div', {}, [
            h('div', { class: 'text-sm text-gray-500' }, 'Full name'),
            h('div', { class: 'mt-2 border-b border-gray-200 pb-2 text-sm text-gray-900' }, 'Albert H. Wiggin')
          ]),
          h('div', {}, [
            h('div', { class: 'text-sm text-gray-500' }, 'Email address'),
            h('div', { class: 'mt-2 border-b border-gray-200 pb-2 text-sm text-gray-900' }, 'awiggin@chase.com')
          ])
        ]),
        h('div', { class: 'mt-6 rounded-lg bg-cyan-500 px-3 py-2 text-center text-sm font-semibold text-white' }, 'Invite person')
      ]))
    ])
  }
})

const StocksScreen = defineComponent({
  setup() {
    return () => h(AppScreen, { class: 'w-full' }, () => [
      h(AppScreenHeader, {}, () => [
        h(AppScreenTitle, {}, () => 'Stocks'),
        h(AppScreenSubtitle, {}, () => 'March 9, 2022')
      ]),
      h(AppScreenBody, {}, () => h('div', { class: 'divide-y divide-gray-100 text-sm' }, [
        h('div', { class: 'flex items-center gap-4 px-4 py-3' }, [
          h('div', { class: 'flex-none rounded-full bg-red-500 h-10 w-10' }),
          h('div', { class: 'flex-auto text-gray-900' }, 'Laravel'),
          h('div', { class: 'flex-none text-right' }, [
            h('div', { class: 'font-medium text-gray-900' }, '4,098.01'),
            h('div', { class: 'text-xs/5 text-cyan-500' }, '+4.98%')
          ])
        ])
      ]))
    ])
  }
})

const InvestScreen = defineComponent({
  setup() {
    return () => h(AppScreen, { class: 'w-full' }, () => [
      h(AppScreenHeader, {}, () => [
        h(AppScreenTitle, {}, () => 'Buy $LA'),
        h(AppScreenSubtitle, {}, () => [
          h('span', { class: 'text-white' }, '$34.28'),
          ' per share'
        ])
      ]),
      h(AppScreenBody, {}, () => h('div', { class: 'px-4 py-6' }, [
        h('div', { class: 'space-y-4' }, [
          h('div', { class: 'flex justify-between border-b border-gray-100 pb-4' }, [
            h('div', { class: 'text-sm text-gray-500' }, 'Number of shares'),
            h('div', { class: 'text-sm font-semibold text-gray-900' }, '100')
          ]),
          h('div', { class: 'rounded-lg bg-cyan-500 px-3 py-2 text-center text-sm font-semibold text-white' }, 'Buy shares')
        ])
      ]))
    ])
  }
})

const features = [
  {
    name: 'Invite friends for better returns',
    description: 'For every friend you invite to Pocket, you get insider notifications 5 seconds sooner. And it\'s 10 seconds if you invite an insider.',
    icon: DeviceUserIcon,
    screen: InviteScreen
  },
  {
    name: 'Notifications on stock dips',
    description: 'Get a push notification every time we find out something that\'s going to lower the share price on your holdings so you can sell before the information hits the public markets.',
    icon: DeviceNotificationIcon,
    screen: StocksScreen
  },
  {
    name: 'Invest what you want',
    description: 'We hide your stock purchases behind thousands of anonymous trading accounts, so suspicious activity can never be traced back to you.',
    icon: DeviceTouchIcon,
    screen: InvestScreen
  }
]
</script>
