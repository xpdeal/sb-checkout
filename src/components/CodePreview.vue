<script setup lang="ts">
const code = `const payflow = require('payflow');

const payment = await payflow.payments.create({
  amount: 2000,
  currency: 'usd',
  payment_method: 'card',
  confirm: true,
});`
</script>

<template>
  <div class="bg-gray-900 py-16 sm:py-20 lg:py-24">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid md:grid-cols-2 gap-8 lg:gap-12 items-center">
        <div class="text-center md:text-left">
          <h2 class="text-2xl sm:text-3xl font-bold text-white mb-4 sm:mb-6">
            Built for developers
          </h2>
          <p class="text-base sm:text-lg text-gray-400 mb-6 sm:mb-8">
            Our APIs are carefully designed to be intuitive and easy to implement, with detailed documentation and SDKs for all major languages.
          </p>
          <button class="text-white bg-primary-600 hover:bg-primary-700 px-6 py-3 rounded-full inline-flex items-center text-sm sm:text-base">
            Read the docs
          </button>
        </div>
        <div class="bg-gray-800 rounded-xl p-4 sm:p-6 font-mono text-xs sm:text-sm text-gray-300 overflow-x-auto">
          <pre class="whitespace-pre-wrap sm:whitespace-pre"><code>{{ code }}</code></pre>
        </div>
      </div>
    </div>
  </div>
</template>