<template>
  <footer class="border-t border-gray-200">
    <Container>
      <div class="flex flex-col items-start justify-between gap-y-12 pt-16 pb-6 lg:flex-row lg:items-center lg:py-16">
        <div>
          <div class="flex items-center text-gray-900">
            <Logo mark class="h-10 w-10 flex-none fill-cyan-500" />
            <div class="ml-4">
              <p class="text-base font-semibold">Pocket</p>
              <p class="mt-1 text-sm">Invest at the perfect time.</p>
            </div>
          </div>
          <nav class="mt-11 flex gap-8">
            <NavLinks />
          </nav>
        </div>
        <div class="group relative -mx-4 flex items-center self-stretch p-4 transition-colors hover:bg-gray-100 sm:self-auto sm:rounded-2xl lg:mx-0 lg:self-auto lg:p-6">
          <div class="relative flex h-24 w-24 flex-none items-center justify-center">
            <svg viewBox="0 0 96 96" fill="none" aria-hidden="true" class="absolute inset-0 h-full w-full stroke-gray-300 transition-colors group-hover:stroke-cyan-500" stroke-width="2" stroke-linecap="round">
              <path
                d="M1 17V9a8 8 0 0 1 8-8h8M95 17V9a8 8 0 0 0-8-8h-8M1 79v8a8 8 0 0 0 8 8h8M95 79v8a8 8 0 0 1-8 8h-8"
              />
            </svg>
          </div>
          <div class="ml-8 lg:w-64">
            <p class="text-base font-semibold text-gray-900">
              <a href="#">
                <span class="absolute inset-0 sm:rounded-2xl" />
                Download the app
              </a>
            </p>
            <p class="mt-1 text-sm text-gray-700">
              Scan the QR code to download the app from the App Store.
            </p>
          </div>
        </div>
      </div>
      <div class="flex flex-col items-center border-t border-gray-200 pt-8 pb-12 md:flex-row-reverse md:justify-between md:pt-6">
        <form class="flex w-full justify-center md:w-auto">
          <input
            type="email"
            aria-label="Email address"
            placeholder="Email address"
            autocomplete="email"
            required
            class="w-60 min-w-0 shrink block appearance-none rounded-lg border border-gray-200 bg-white py-[calc(theme(spacing.2)-1px)] px-[calc(theme(spacing.3)-1px)] text-gray-900 placeholder:text-gray-400 focus:border-cyan-500 focus:outline-hidden focus:ring-cyan-500 sm:text-sm"
          />
          <Button type="submit" color="cyan" class="ml-4 flex-none">
            <span class="hidden lg:inline">Join our newsletter</span>
            <span class="lg:hidden">Join newsletter</span>
          </Button>
        </form>
        <p class="mt-6 text-sm text-gray-500 md:mt-0">
          &copy; Copyright {{ new Date().getFullYear() }}. All rights reserved.
        </p>
      </div>
    </Container>
  </footer>
</template>

<script setup>
import Container from './Container.vue'
import Logo from './Logo.vue'
import NavLinks from './NavLinks.vue'
import Button from './Button.vue'
</script>
