<template>
  <div
    v-editable="blok"
  >
    
      {{ blok.variation }}
    
  </div>
</template>

<script setup>
defineProps({ blok: Object });
</script>
