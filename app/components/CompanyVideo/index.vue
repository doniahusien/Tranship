<template>
  <div>
    <h4 class="text-3xl font-light">Watch the video and take</h4>
    <h5 class="text-secondary text-4xl">some idea about our company</h5>
    <p class="py-5 ">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
      incididunt ut labore et dolore magna aliqua. Ut enim ad minim.
    </p>
    <div class="video-wrapper">
      <iframe
        class="video"
        src="https://www.youtube.com/embed/e9P0gyAH_QE?si=FzvhiIx6B3GWnTrA"
        title="Company Video"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      />
    </div>
  </div>
</template>

<script setup lang="ts"></script>
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
