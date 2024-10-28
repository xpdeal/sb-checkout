<script setup lang="ts">
import { ref } from 'vue'
import { ArrowPathIcon, CreditCardIcon, UserIcon, ShoppingCartIcon, CheckCircleIcon } from '@heroicons/vue/24/outline'

interface Step {
  id: string
  title: string
  description: string
  icon: any
}

const steps = ref<Step[]>([
  {
    id: 'cart',
    title: 'Cart Review',
    description: 'Customer reviews items and proceeds to checkout',
    icon: ShoppingCartIcon
  },
  {
    id: 'customer',
    title: 'Customer Info',
    description: 'Collect customer details and shipping info',
    icon: UserIcon
  },
  {
    id: 'payment',
    title: 'Payment',
    description: 'Secure payment processing with multiple options',
    icon: CreditCardIcon
  },
  {
    id: 'confirmation',
    title: 'Confirmation',
    description: 'Order confirmation and receipt generation',
    icon: CheckCircleIcon
  }
])

const draggingStep = ref<Step | null>(null)
const dragOverStep = ref<string | null>(null)

const handleDragStart = (step: Step) => {
  draggingStep.value = step
}

const handleDragOver = (e: DragEvent, stepId: string) => {
  e.preventDefault()
  if (dragOverStep.value !== stepId) {
    dragOverStep.value = stepId
  }
}

const handleDrop = (targetId: string) => {
  if (!draggingStep.value) return
  
  const fromIndex = steps.value.findIndex(s => s.id === draggingStep.value?.id)
  const toIndex = steps.value.findIndex(s => s.id === targetId)
  
  const [movedStep] = steps.value.splice(fromIndex, 1)
  steps.value.splice(toIndex, 0, movedStep)
  
  draggingStep.value = null
  dragOverStep.value = null
}

const handleDragEnd = () => {
  draggingStep.value = null
  dragOverStep.value = null
}
</script>

<template>
  <div class="py-16 sm:py-20 lg:py-24 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-12 lg:mb-16">
        <h2 class="text-2xl sm:text-3xl font-bold text-gray-900">
          Customize Your Payment Flow
        </h2>
        <p class="mt-3 sm:mt-4 text-lg sm:text-xl text-gray-600">
          Drag and drop to rearrange steps and create your perfect checkout experience
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 sm:gap-6">
        <div
          v-for="step in steps"
          :key="step.id"
          :draggable="true"
          @dragstart="handleDragStart(step)"
          @dragover="(e) => handleDragOver(e, step.id)"
          @drop="handleDrop(step.id)"
          @dragend="handleDragEnd"
          :class="[
            'p-4 sm:p-6 rounded-xl bg-white border-2 transition-all duration-300 cursor-move',
            dragOverStep === step.id ? 'border-primary-400 shadow-lg scale-105' : 'border-gray-100',
            draggingStep?.id === step.id ? 'opacity-50' : 'opacity-100'
          ]"
        >
          <div class="flex items-start space-x-4">
            <div class="flex-shrink-0">
              <div :class="`p-2 sm:p-3 rounded-lg bg-primary-100 text-primary-600`">
                <component :is="step.icon" class="w-5 h-5 sm:w-6 sm:h-6" />
              </div>
            </div>
            <div>
              <h3 class="text-lg font-semibold text-gray-900 mb-1">
                {{ step.title }}
              </h3>
              <p class="text-sm text-gray-600">
                {{ step.description }}
              </p>
            </div>
          </div>

          <div class="mt-4 pt-4 border-t border-gray-100">
            <div class="flex items-center justify-between text-sm text-gray-500">
              <span class="flex items-center">
                <ArrowPathIcon class="w-4 h-4 mr-1" />
                Drag to reorder
              </span>
              <span class="text-primary-600">Step {{ steps.indexOf(step) + 1 }}</span>
            </div>
          </div>
        </div>
      </div>

      <div class="mt-8 text-center">
        <p class="text-sm text-gray-500">
          Customize the flow to match your business needs
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
[draggable] {
  user-select: none;
}
</style>