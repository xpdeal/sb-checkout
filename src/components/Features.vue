<script setup lang="ts">
import { CreditCardIcon, CodeBracketIcon, ShieldCheckIcon, GlobeAltIcon } from '@heroicons/vue/24/outline'

const features = [
  {
    title: 'Global Scale',
    description: 'Accept payments in 135+ currencies with local acquiring optimized for key markets.',
    icon: GlobeAltIcon,
    gradient: 'from-blue-500 to-cyan-400'
  },
  {
    title: 'Developer First',
    description: 'Powerful and well-documented APIs to integrate payments into any application.',
    icon: CodeBracketIcon,
    gradient: 'from-purple-500 to-pink-400'
  },
  {
    title: 'Enterprise Grade',
    description: 'Advanced security and compliance features to protect your business and customers.',
    icon: ShieldCheckIcon,
    gradient: 'from-green-500 to-emerald-400'
  },
  {
    title: 'Unified Platform',
    description: 'A single integration for all your payment needs - online, in-person, and mobile.',
    icon: CreditCardIcon,
    gradient: 'from-orange-500 to-amber-400'
  }
]
</script>

<template>
  <div class="py-16 sm:py-20 lg:py-24 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-12 lg:mb-16">
        <h2 class="text-2xl sm:text-3xl font-bold text-gray-900 px-4">
          The platform for modern commerce
        </h2>
        <p class="mt-3 sm:mt-4 text-lg sm:text-xl text-gray-600 px-4">
          A complete payments and financial management solution
        </p>
      </div>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 sm:gap-6 lg:gap-8">
        <div 
          v-for="feature in features" 
          :key="feature.title" 
          class="p-4 sm:p-6 rounded-2xl bg-gradient-to-br from-gray-50 to-white border border-gray-100 hover:border-gray-200 transition-all duration-300 hover:shadow-lg"
        >
          <div :class="`inline-flex p-2 sm:p-3 rounded-xl bg-gradient-to-br ${feature.gradient}`">
            <component :is="feature.icon" class="w-5 h-5 sm:w-6 sm:h-6 text-white" />
          </div>
          <h3 class="text-lg sm:text-xl font-semibold text-gray-900 mt-3 sm:mt-4 mb-2">
            {{ feature.title }}
          </h3>
          <p class="text-sm sm:text-base text-gray-600">
            {{ feature.description }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>