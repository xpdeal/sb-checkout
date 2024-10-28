<script setup lang="ts">
import { ArrowRightIcon } from '@heroicons/vue/24/outline'
</script>

<template>
  <div class="relative overflow-hidden bg-white">
    <!-- Gradient Background -->
    <div class="absolute inset-0 bg-gradient-to-br from-primary-50 via-white to-primary-50/30"></div>
    
    <!-- Content -->
    <div class="relative pt-24 lg:pt-32 pb-16 lg:pb-24">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center">
          <h1 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-bold text-gray-900 tracking-tight mb-6 lg:mb-8">
            <span class="block mb-2">Financial infrastructure</span>
            <span class="bg-gradient-to-r from-primary-600 to-primary-400 bg-clip-text text-transparent">
              for the internet
            </span>
          </h1>
          <p class="text-lg sm:text-xl text-gray-600 mb-8 lg:mb-12 max-w-2xl mx-auto px-4 sm:px-0">
            Millions of businesses of all sizes use PayFlow's software and APIs to accept payments, send payouts, and manage their businesses online.
          </p>
          <div class="flex flex-col sm:flex-row justify-center gap-3 sm:gap-4 items-center px-4 sm:px-0">
            <button class="w-full sm:w-auto bg-primary-600 text-white px-6 sm:px-8 py-3 rounded-full hover:bg-primary-700 transition-colors inline-flex items-center justify-center text-sm sm:text-base">
              Start now
              <ArrowRightIcon class="w-4 h-4 sm:w-5 sm:h-5 ml-2" />
            </button>
            <button class="w-full sm:w-auto text-primary-600 px-6 sm:px-8 py-3 rounded-full hover:bg-primary-50 transition-colors text-sm sm:text-base">
              Contact sales
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Brands -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pb-16 lg:pb-24">
      <p class="text-center text-sm sm:text-base text-gray-600 mb-6 sm:mb-8">Trusted by leading companies worldwide</p>
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4 sm:gap-8 items-center justify-items-center opacity-50">
        <div class="h-6 sm:h-8 bg-gray-400 w-24 sm:w-32 rounded"></div>
        <div class="h-6 sm:h-8 bg-gray-400 w-24 sm:w-32 rounded"></div>
        <div class="h-6 sm:h-8 bg-gray-400 w-24 sm:w-32 rounded"></div>
        <div class="h-6 sm:h-8 bg-gray-400 w-24 sm:w-32 rounded"></div>
      </div>
    </div>
  </div>
</template>