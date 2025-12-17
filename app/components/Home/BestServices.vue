<template>
  <GeneralSection image="/images/bannerGeneral.jpeg">
    <div class=" container mx-auto flex flex-col items-center gap-10">
      <h2 class="text-white font-light leading-relaxed uppercase text-xl md:text-2xl lg:text-4xl max-w-5xl text-center ">
      {{$t('LABELS.BEST_SERVICES')}}
      </h2>

      <NuxtLink
        class="font-semibold w-fit px-3 md:px-5 py-3.5 rounded-lg bg-secondary text-white hover:bg-white hover:text-secondary transition-colors duration-500 ease-in-out"
        :to="localePath('/get-quote')"
        >           {{$t('TITLES.GET_QUOTE')}}</NuxtLink
      >
    </div>
  </GeneralSection>
</template>
<script setup>
const {t}= useI18n();
const localePath= useLocalePath();

</script>