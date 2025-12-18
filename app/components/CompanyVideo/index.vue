<template>
  <div>
    <h4 class="text-3xl font-light"> {{$t('TITLES.watchVideoLine1')}}</h4>
    <h5 class="text-secondary  text-2xl md:text-4xl">{{$t('TITLES.watchVideoLine2')}}</h5>
    <p class="py-5 ">
      {{$t('LABELS.GENERAL_DESC')}} </p>
    <div class="video-wrapper">
   <!--    <iframe
        class="video"
        src="https://www.youtube.com/embed/e9P0gyAH_QE?si=FzvhiIx6B3GWnTrA"
        title="Company Video"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      /> -->
    </div>
  </div>
</template>

<script setup lang="ts">
    const {t} = useI18n();
</script>
<style scoped>
.video-wrapper {
  aspect-ratio: 16 / 9;
  width: 100%;
}
.video {
  width: 100%;
  height: 100%;
  border-radius: 12px;
}
</style>
