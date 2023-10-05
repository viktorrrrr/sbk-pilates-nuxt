<style>
.css-fix {
  white-space: pre-wrap;
  }
</style>


<template>
  <div v-editable="blok">
    <img
      v-if="blok.image?.filename"
      :src="blok.image.filename + '/m/1600x0'"
      :alt="blok.image.alt"
      class="w-full h-[360px] lg:h-[450px] object-cover"
    />
    <div class="container mx-auto mb-12">
      
      <h1 class="text-6xl text-[#50b0ae] font-bold mt-12 mb-4">{{ blok.title }}</h1>
    
    <div class="columns-2 gap-8 space-y-8 py-20" >
      <div class="break-inside-avoid-column">
      <div class=" items-center rounded-md bg-teal-600 w-40 text-center py-1 text-xs font-medium 
      text-white ring-1 bg-gradient-to-r from-teal-500" >置设</div>
      <div>
        弹簧设置：{{ blok.apparatus_from }} <span v-show="has">- {{ blok.apparatus_to }}</span>
        
    </div>
    </div>
    <div class="break-inside-avoid-column">
      <div class=" items-center rounded-md bg-teal-600 w-40 text-center py-1 text-xs font-medium 
      text-white ring-1 bg-gradient-to-r from-teal-500" >起始位置</div>
      <div class="css-fix">
        {{ blok.starting_position }} 
    </div>
    </div>
  <div>
    <img class="w-300 object-cover rounded-lg" src="https://images.unsplash.com/photo-1454496522488-7a8e488e8606?ixlib=rb-1.2.1&amp;ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&amp;auto=format&amp;fit=crop&amp;w=300&amp;q=80">
  </div>
</div>
<div class="columns-2 gap-8 space-y-8">
  <div class="break-inside-avoid-column">
      <div class=" items-center rounded-md bg-teal-600 w-40 text-center py-1 text-xs font-medium 
      text-white ring-1 bg-gradient-to-r from-teal-500" >练习</div>
      <div>
        <StoryblokComponent
      v-for="blok in blok.steps"
      :key="blok._uid"
      :blok="blok"
    />
    </div>
    </div>

    <div class="break-inside-avoid-column">
      <div class=" items-center rounded-md bg-teal-600 w-40 text-center py-1 text-xs font-medium 
      text-white ring-1 bg-gradient-to-r from-teal-500" >变式</div>
      <div>
        <StoryblokComponent
      v-for="blok in blok.steps"
      :key="blok._uid"
      :blok="blok"
    />
    </div>
    </div>


    <div class="break-inside-avoid-column">
      <div class=" items-center rounded-md bg-teal-600 w-40 text-center py-1 text-xs font-medium 
      text-white ring-1 bg-gradient-to-r from-teal-500 " >注意</div>
      <div class="css-fix">
        {{ blok.focus }} 
    </div>
    </div>

    <div class="break-inside-avoid-column">
      <div class=" items-center rounded-md bg-teal-600 w-40 text-center py-1 text-xs font-medium 
      text-white ring-1 bg-gradient-to-r from-teal-500" >动作好处</div>
      <div class="css-fix">
        {{ blok.movement_benefits }} 
    </div>
    </div>

    <div>
      <div class=" items-center rounded-md bg-teal-600 w-40 text-center py-1 text-xs font-medium 
      text-white ring-1 bg-gradient-to-r from-teal-500" >Caution</div>
      <div class="css-fix">
        {{ blok.caution }} 
    </div>
    </div>
    <div v-html="resolvedRichText"></div>
    </div>
      <h2 class="text-2xl text-[#1d243d] font-bold mb-3">
        {{ blok.subtitle }}
      </h2>
      <div v-html="resolvedRichText" class="prose"></div>
    </div>
  </div>
</template>
 
<script setup>
const props = defineProps({ blok: Object })


const resolvedRichText = computed(() => renderRichText(props.blok.content))


</script>

