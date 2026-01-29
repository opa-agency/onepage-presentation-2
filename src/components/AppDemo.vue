<template>
  <AppScreen>
    <AppScreenBody>
      <div class="p-4">
        <div class="flex gap-2">
          <div class="text-xs/6 text-gray-500">Tailwind Labs, Inc.</div>
          <div class="text-sm text-gray-900">$CSS</div>
          <svg viewBox="0 0 24 24" class="ml-auto h-6 w-6" fill="none">
            <path
              d="M5 12a7 7 0 1 1 14 0 7 7 0 0 1-14 0ZM12 9v6M15 12H9"
              stroke="#171717"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </div>
        <div class="mt-3 border-t border-gray-200 pt-5">
          <div class="flex items-baseline gap-2">
            <div class="text-2xl tracking-tight text-gray-900 tabular-nums">
              752.56
            </div>
            <div class="text-sm text-gray-900">USD</div>
            <div class="ml-auto text-sm tracking-tight tabular-nums text-cyan-500">
              +12.28%
            </div>
          </div>
          <div class="mt-6 flex gap-4 text-xs text-gray-500">
            <div>1D</div>
            <div>5D</div>
            <div class="font-semibold text-cyan-600">1M</div>
            <div>6M</div>
            <div>1Y</div>
            <div>5Y</div>
          </div>
          <div class="mt-3 rounded-lg bg-gray-50 ring-1 ring-black/5 ring-inset">
            <svg viewBox="0 0 286 208" class="overflow-visible">
              <defs>
                <linearGradient id="grad" x1="0" x2="0" y1="0" y2="1">
                  <stop offset="0%" stop-color="#13B5C8" />
                  <stop offset="100%" stop-color="#13B5C8" stop-opacity="0" />
                </linearGradient>
              </defs>
              <path
                d="M 16 176 L 24 156 L 32 164 L 40 132 L 48 144 L 56 128 L 64 120 L 72 108 L 80 136 L 88 92 L 96 100 L 104 108 L 112 100 L 120 88 L 128 72 L 136 80 L 144 88 L 152 84 L 160 96 L 168 108 L 176 112 L 184 100 L 192 92 L 200 96 L 208 88 L 216 92 L 224 84 L 232 92 L 240 80 L 248 88 L 256 96 L 264 108 L 270 112"
                fill="none"
                stroke="#06b6d4"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
          </div>
          <div class="mt-4 rounded-lg bg-cyan-500 px-4 py-2 text-center text-sm font-semibold text-white">
            Trade
          </div>
          <div class="mt-3 divide-y divide-gray-100 text-sm">
            <div class="flex justify-between py-1">
              <div class="text-gray-500">Open</div>
              <div class="font-medium text-gray-900">6,387.55</div>
            </div>
            <div class="flex justify-between py-1">
              <div class="text-gray-500">Closed</div>
              <div class="font-medium text-gray-900">6,487.09</div>
            </div>
            <div class="flex justify-between py-1">
              <div class="text-gray-500">Low</div>
              <div class="font-medium text-gray-900">6,322.01</div>
            </div>
          </div>
        </div>
      </div>
    </AppScreenBody>
  </AppScreen>
</template>

<script setup>
import AppScreen from './AppScreen.vue'
import AppScreenBody from './AppScreenBody.vue'
</script>
