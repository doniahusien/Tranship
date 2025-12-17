<template>
  <div>
    <h2 class="text-3xl font-light">{{$t('TITLES.OUR_HAPPY')}}</h2>
    <h3 class="text-secondary text-2xl md:text-4xl">{{$t('TITLES.CLIENT')}}</h3>
    <p class="py-5">
     
     {{$t('LABELS.GENERAL_DESC')}} </p>
    <TestimonialsSwiper />
  </div>
</template>

<script setup lang="ts">
  const {t} = useI18n();

</script>

<style scoped></style>
