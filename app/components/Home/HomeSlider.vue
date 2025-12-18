<template>
  <div class="relative">
    <Swiper
      :modules="[Navigation, Autoplay, EffectFade]"
      effect="fade"
      :fadeEffect="{ crossFade: true }"
      :slides-per-view="1"
      :loop="true"
      :speed="1200"
      :autoplay="{ delay: 5000 }"
      :navigation="navigationOptions"
      @swiper="onSwiperInit"
      style="height: calc(100vh - 105px)"
    >
      <SwiperSlide
        v-for="item in sliders"
        :key="item.key"
        class="bg-cover bg-no-repeat"
        :style="{ backgroundImage: `url('${item.image}')` }"
      >
        <div class="overlay"></div>
        <div
          :style="{ 'text-align': item.key, 'align-items': item.key }"
          class="absolute space-y-5 inset-0 max-w-7xl mx-auto text-white flex flex-col justify-center z-10 px-5 opacity-0 translate-y-6 slide-content"
        >
          <div
            v-html="item.title"
            class="text-base md:text-2xl max-w-100 lg:text-3xl"
          ></div>

          <div v-html="item.desc" class="text-base max-w-2xl mb-6 opacity-90"></div>
          <div class="flex gap-2">
            <NuxtLink
              aria-label="our services"
              class="text-sm md:text-base font-semibold px-3 md:px-5 py-3.5 rounded-lg bg-secondary text-white hover:bg-black transition-colors duration-500 ease-in-out"
              :to="localePath('/')"
              >{{ $t("TITLES.OUR_SERVICES") }}</NuxtLink
            >
            <NuxtLink
              aria-label="get quote"
              class="text-sm md:text-base font-semibold px-3 md:px-5 py-3.5 rounded-lg bg-secondary text-white hover:bg-black transition-colors duration-500 ease-in-out"
              :to="localePath('/')"
              >{{ $t("TITLES.GET_QUOTE") }}</NuxtLink
            >
          </div>
        </div>
      </SwiperSlide>
    </Swiper>

    <div class="absolute bottom-1/2 start-2 z-30">
      <button
      aria-label="prev"

        ref="prev"
        class="opacity-0 hover:opacity-100 size-14 cursor-pointer flex items-center justify-center hover:bg-black/20 text-white rounded-full backdrop-blur-md transition-opacity duration-500 ease-in-out"
      >
        <Icon name="lucide:chevron-left" class="size-10" />
      </button>
    </div>

    <div class="absolute bottom-1/2 end-2 z-30">
      <button
      aria-label="next"
        ref="nextEl"
        class="opacity-0 hover:opacity-100 size-14 cursor-pointer flex items-center justify-center hover:bg-black/40 text-white rounded-full backdrop-blur-md transition-opacity duration-500 ease-in-out"
      >
        <Icon name="lucide:chevron-right" class="size-10" />
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, Autoplay, EffectFade } from "swiper/modules";
import "swiper/css/effect-fade";
import "swiper/css";
import "swiper/css/navigation";

const { t } = useI18n();
const localePath = useLocalePath();
const prevEl = ref(null);
const nextEl = ref(null);

const navigationOptions = ref({
  prevEl: null,
  nextEl: null,
});

const onSwiperInit = (swiper) => {
  swiper.params.navigation.prevEl = prevEl.value;
  swiper.params.navigation.nextEl = nextEl.value;

  swiper.navigation.init();
  swiper.navigation.update();
};

const sliders = ref([
  {
    key: "start",
    image: "/images/banner1.webp",
    title: t("TITLES.SLIDER"),
    desc: t("LABELS.SLIDER_DESC"),
  },
  {
    key: "center",
    image: "/images/banner2.webp",
    title: t("TITLES.SLIDER"),
    desc: t("LABELS.SLIDER_DESC"),
  },
  {
    key: "end",
    image: "/images/banner3.webp",
    title: t("TITLES.SLIDER"),
    desc: t("LABELS.SLIDER_DESC"),
  },
]);
</script>
<style scoped>
.slide-content {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 1s ease, transform 1s ease;
}

.swiper-slide-active .slide-content {
  opacity: 1;
  transform: translateY(0);
}
</style>
