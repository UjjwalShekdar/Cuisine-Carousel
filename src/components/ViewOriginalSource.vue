<template>
  <a 
      :href="href" 
      target="_blank" 
      class="px-3 py-2 rounded border-2 
              border-purple-600 bg-purple-500 bg-purple-600 
              text-white transition-colors">
  <slot></slot>
  </a>
  
</template>  

<script setup>
const props = defineProps({
  href: String,
})
</script>