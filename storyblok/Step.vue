<template>
  <div
    v-editable="blok"
  >
    
      {{ blok.step_text }}
    
  </div>
</template>

<script setup>
defineProps({ blok: Object });
</script>
