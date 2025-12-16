<template>
  <div
    class="relative"
  >
    <Swiper
      :modules="[Navigation, Autoplay]"
      :slides-per-view="1"
      :loop="true"
      :autoplay="{ delay: 8000 }"
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
        :style="{'text-align': item.key,'align-items':item.key }"
          class="absolute space-y-5 inset-0 max-w-7xl mx-auto text-white flex flex-col justify-center  z-10 px-5"
        >
          <div
            v-html="item.title"
            class=" md:text-2xl max-w-100  lg:text-3xl"
          ></div>

          <div
            v-html="item.desc"
            class="text-base max-w-2xl mb-6 opacity-90"
          ></div>
          <div class="flex gap-2">
          <NuxtLink
            class=" font-semibold  px-5 py-3.5 rounded-lg bg-secondary text-white hover:bg-black transition-colors duration-500 ease-in-out"
            href="#"
            >OUR SERVICES</NuxtLink
          >
          <NuxtLink
            class=" font-semibold  px-5 py-3.5 rounded-lg bg-secondary text-white hover:bg-black transition-colors duration-500 ease-in-out"
            href="#"
            >GET A QUOTE</NuxtLink
          >
          </div>
        </div>
      </SwiperSlide>
    </Swiper>
   

    <div class="absolute bottom-1/2  start-2  z-30">
      <button
        ref="prevEl"
        class="opacity-0 hover:opacity-100 size-14 cursor-pointer flex items-center justify-center hover:bg-black/20 text-white rounded-full backdrop-blur-md   transition-opacity duration-500 ease-in-out"
      >
        <Icon name="lucide:chevron-left" class="size-10" />
      </button>
    </div>

     <div class="absolute bottom-1/2 end-2 z-30">
      <button
        ref="nextEl"
        class="opacity-0 hover:opacity-100 size-14 cursor-pointer flex items-center justify-center  hover:bg-black/40 text-white rounded-full backdrop-blur-md    transition-opacity duration-500 ease-in-out"
      >
        <Icon name="lucide:chevron-right" class="size-10" />
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, Autoplay } from "swiper/modules";

import "swiper/css";
import "swiper/css/navigation";

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

const sliders= ref([{
  key:"start",
  image:"/images/banner1.jpeg",
 title: "WORLD WIDE TRANSPORT SERVICE",
desc:"Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto."

},
{
  key:"center",
  image:"/images/banner2.jpeg",
   title: "WORLD WIDE TRANSPORT SERVICE",
desc:"Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto."

},
{
  key:"end",
  image:"/images/banner3.jpeg",
   title: "WORLD WIDE TRANSPORT SERVICE",
desc:"Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto."

}
])

</script>

<style scoped>
.swiper,
.swiper-wrapper,
.swiper-slide,
.swiper-slide img {
  transform: translateZ(0);
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  will-change: transform;
}

.swiper-slide img {
  pointer-events: none;
}

.animate-fade-in {
  animation: fadeIn 1.2s ease-out forwards;
}
.animate-fade-in-delay {
  animation: fadeIn 1.4s ease-out forwards;
}
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
