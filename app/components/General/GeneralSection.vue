<template>
  <div
    class="relative h-96 bg-cover bg-center bg-no-repeat flex items-center bg-fixed"
    :style="{ backgroundImage: `url('${image}')` }"
  >
    <div class="overlay"></div>

    <div class="container relative mx-auto z-10">
      <slot/>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps({
  image: String
})
</script>

<style scoped>

</style>
