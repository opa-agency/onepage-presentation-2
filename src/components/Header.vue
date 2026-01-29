<template>
  <header>
    <nav>
      <Container class="relative z-50 flex justify-between py-8">
        <div class="relative z-10 flex items-center gap-16">
          <a href="/" aria-label="Acasă">
            <Logo class="h-10 w-auto" />
          </a>
          <div class="hidden lg:flex lg:gap-10">
            <NavLinks />
          </div>
        </div>
        <div class="flex items-center gap-6">
          <Popover class="lg:hidden">
            <PopoverButton
              class="relative z-10 -m-2 inline-flex items-center rounded-lg stroke-gray-900 p-2 hover:bg-gray-200/50 hover:stroke-gray-600 active:stroke-gray-900"
              aria-label="Comută navigarea pe site"
            >
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true" class="h-6 w-6">
                <path
                  d="M5 6h14M5 18h14M5 12h14"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </PopoverButton>
            <PopoverPanel class="absolute inset-x-0 top-0 z-0 origin-top rounded-b-2xl bg-gray-50 px-6 pt-32 pb-6 shadow-2xl shadow-gray-900/20">
              <div class="space-y-4">
                <a 
                  href="/#features"
                  class="block text-base/7 tracking-tight text-gray-700"
                >
                  Funcționalități
                </a>
                <a 
                  href="/#reviews"
                  class="block text-base/7 tracking-tight text-gray-700"
                >
                  Recenzii
                </a>
                <a 
                  href="/#pricing"
                  class="block text-base/7 tracking-tight text-gray-700"
                >
                  Prețuri
                </a>
                <a 
                  href="/#faqs"
                  class="block text-base/7 tracking-tight text-gray-700"
                >
                  Întrebări frecvente
                </a>
              </div>
              <div class="mt-8 flex flex-col gap-4">
                <Button href="#">Descarcă aplicația</Button>
              </div>
            </PopoverPanel>
          </Popover>
          <div class="flex items-center gap-6 max-lg:hidden">
            <Button href="#">Descarcă</Button>
          </div>
        </div>
      </Container>
    </nav>
  </header>
</template>

<script setup>
import { Popover, PopoverButton, PopoverPanel } from '@headlessui/vue'
import Container from './Container.vue'
import Logo from './Logo.vue'
import NavLinks from './NavLinks.vue'
import Button from './Button.vue'
</script>
