<script setup lang="ts">
import { Bars3Icon, XMarkIcon, ChevronDownIcon } from '@heroicons/vue/24/outline'
import { ref } from 'vue'

const mobileMenuOpen = ref(false)
const activeSubmenu = ref('')

const menuItems = [
  { 
    name: 'Products',
    href: '#products',
    submenu: [
      {
        title: 'Payment Processing',
        description: 'Accept payments online, in-person, or on the go',
        href: '#payment-processing'
      },
      {
        title: 'Billing & Invoicing',
        description: 'Automated recurring billing and invoice management',
        href: '#billing'
      },
      {
        title: 'Fraud Prevention',
        description: 'Advanced fraud detection and prevention tools',
        href: '#fraud'
      }
    ]
  },
  { 
    name: 'Solutions',
    href: '#solutions',
    submenu: [
      {
        title: 'E-commerce',
        description: 'Complete platform for online stores',
        href: '#ecommerce'
      },
      {
        title: 'Marketplaces',
        description: 'Solutions for marketplace payment flows',
        href: '#marketplaces'
      },
      {
        title: 'SaaS',
        description: 'Subscription management for SaaS businesses',
        href: '#saas'
      }
    ]
  },
  { 
    name: 'Developers',
    href: '#developers',
    submenu: [
      {
        title: 'Documentation',
        description: 'Guides, references, and resources',
        href: '#docs'
      },
      {
        title: 'API Reference',
        description: 'Detailed API documentation',
        href: '#api'
      },
      {
        title: 'SDKs & Libraries',
        description: 'Official SDKs for major platforms',
        href: '#sdks'
      }
    ]
  },
  { 
    name: 'Resources',
    href: '#resources',
    submenu: [
      {
        title: 'Support Center',
        description: '24/7 help for all your needs',
        href: '#support'
      },
      {
        title: 'Blog',
        description: 'Latest updates and articles',
        href: '#blog'
      },
      {
        title: 'Case Studies',
        description: 'Success stories from our customers',
        href: '#cases'
      }
    ]
  },
  { 
    name: 'Pricing',
    href: '#pricing'
  },
]

const handleMouseEnter = (menuItem: string) => {
  activeSubmenu.value = menuItem
}

const handleMouseLeave = () => {
  activeSubmenu.value = ''
}
</script>

<template>
  <nav class="fixed w-full bg-white/80 backdrop-blur-md z-50 border-b border-gray-100">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between h-14 sm:h-16">
        <div class="flex items-center">
          <span class="text-xl sm:text-2xl font-bold bg-gradient-to-r from-primary-600 to-primary-400 bg-clip-text text-transparent">
            PayFlow
          </span>
        </div>

        <!-- Desktop Menu -->
        <div class="hidden lg:flex lg:items-center lg:space-x-1 xl:space-x-2">
          <div
            v-for="item in menuItems"
            :key="item.name"
            @mouseenter="handleMouseEnter(item.name)"
            @mouseleave="handleMouseLeave"
            class="relative group"
          >
            <a
              :href="item.href"
              class="inline-flex items-center px-2 xl:px-3 py-2 text-sm font-medium text-gray-600 hover:text-gray-900 rounded-md hover:bg-gray-50 transition-colors"
            >
              {{ item.name }}
              <ChevronDownIcon
                v-if="item.submenu"
                class="ml-1 h-4 w-4 transition-transform duration-200"
                :class="{'rotate-180': activeSubmenu === item.name}"
              />
            </a>

            <!-- Submenu -->
            <div
              v-if="item.submenu"
              class="absolute left-0 w-[280px] sm:w-[320px] mt-1 bg-white rounded-xl shadow-lg border border-gray-100 opacity-0 translate-y-2 invisible group-hover:opacity-100 group-hover:translate-y-0 group-hover:visible transition-all duration-200"
            >
              <div class="p-2">
                <a
                  v-for="subItem in item.submenu"
                  :key="subItem.title"
                  :href="subItem.href"
                  class="block px-3 sm:px-4 py-2 sm:py-3 rounded-lg hover:bg-gray-50 transition-colors"
                >
                  <div class="font-medium text-gray-900">{{ subItem.title }}</div>
                  <div class="text-xs sm:text-sm text-gray-500">{{ subItem.description }}</div>
                </a>
              </div>
            </div>
          </div>

          <div class="flex items-center space-x-2 ml-2 xl:ml-4">
            <button class="px-3 py-2 text-sm font-medium text-gray-700 hover:text-gray-900 rounded-md hover:bg-gray-50 transition-colors">
              Sign in
            </button>
            <button class="px-3 xl:px-4 py-2 text-sm font-medium text-white bg-primary-600 hover:bg-primary-700 rounded-full transition-colors shadow-sm hover:shadow">
              Start now
            </button>
          </div>
        </div>

        <!-- Mobile menu button -->
        <div class="flex items-center lg:hidden">
          <button 
            @click="mobileMenuOpen = !mobileMenuOpen"
            class="text-gray-600 hover:text-gray-900 p-2 rounded-md hover:bg-gray-50 transition-colors"
          >
            <Bars3Icon v-if="!mobileMenuOpen" class="h-5 w-5 sm:h-6 sm:w-6" />
            <XMarkIcon v-else class="h-5 w-5 sm:h-6 sm:w-6" />
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile menu -->
    <div
      v-if="mobileMenuOpen"
      class="lg:hidden absolute w-full bg-white border-b border-gray-100 shadow-lg"
    >
      <div class="px-4 py-2 sm:py-3 space-y-1 max-h-[80vh] overflow-y-auto">
        <div
          v-for="item in menuItems"
          :key="item.name"
          class="space-y-1"
        >
          <button
            v-if="item.submenu"
            @click="activeSubmenu === item.name ? activeSubmenu = '' : activeSubmenu = item.name"
            class="w-full flex items-center justify-between px-3 py-2 text-sm sm:text-base font-medium text-gray-700 hover:text-gray-900 hover:bg-gray-50 rounded-md transition-colors"
          >
            {{ item.name }}
            <ChevronDownIcon
              class="h-4 w-4 sm:h-5 sm:w-5 transition-transform duration-200"
              :class="{'rotate-180': activeSubmenu === item.name}"
            />
          </button>
          <a
            v-else
            :href="item.href"
            class="block px-3 py-2 text-sm sm:text-base font-medium text-gray-700 hover:text-gray-900 hover:bg-gray-50 rounded-md transition-colors"
          >
            {{ item.name }}
          </a>

          <!-- Mobile Submenu -->
          <div
            v-if="item.submenu"
            v-show="activeSubmenu === item.name"
            class="mt-1 space-y-1 pl-4"
          >
            <a
              v-for="subItem in item.submenu"
              :key="subItem.title"
              :href="subItem.href"
              class="block px-3 py-2 rounded-md hover:bg-gray-50 transition-colors"
            >
              <div class="font-medium text-sm sm:text-base text-gray-900">{{ subItem.title }}</div>
              <div class="text-xs sm:text-sm text-gray-500">{{ subItem.description }}</div>
            </a>
          </div>
        </div>

        <div class="mt-4 space-y-2 pt-4 border-t border-gray-200">
          <button class="w-full text-left px-3 py-2 text-sm sm:text-base font-medium text-gray-700 hover:text-gray-900 hover:bg-gray-50 rounded-md transition-colors">
            Sign in
          </button>
          <button class="w-full px-3 py-2 text-sm sm:text-base font-medium text-white bg-primary-600 hover:bg-primary-700 rounded-full transition-colors shadow-sm hover:shadow">
            Start now
          </button>
        </div>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.group:hover .group-hover\:opacity-100 {
  transition-delay: 100ms;
}
</style>