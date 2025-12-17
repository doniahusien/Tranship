<template>
  <section class="py-16 bg-white">
    <div class="container mx-auto px-4">
      <Swiper
        :modules="[Autoplay, FreeMode]"
        :slides-per-view="2"
        :space-between="16"
        :breakpoints="{
          640: { slidesPerView: 3 },
          768: { slidesPerView: 4 },
          1024: { slidesPerView: 6 },
        }"
        :autoplay="{
          delay: 2000,
          disableOnInteraction: false,
        }"
        :spped="1800"
        loop
        free-mode
        grab-cursor
        :dir="isRTL ? 'rtl' : 'ltr'"
      >
        <SwiperSlide
          v-for="brand in brands"
          :key="brand.name"
          class="flex items-center justify-center"
        >
          <div
            class="flex items-center justify-center border rounded-xl p-4
                   border-gray-200 text-black hover:shadow-sm transition w-full"
          >
            <Icon :name="brand.icon" class=" size-12 md:size-16" />
          </div>
        </SwiperSlide>
      </Swiper>
    </div>
  </section>
</template>
<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, FreeMode } from "swiper/modules";
import "swiper/css";
import "swiper/css/free-mode";

const { locale } = useI18n();
const isRTL = computed(() => locale.value === "ar");

const brands = [
    {name:"unknown",icon:"cib:helm"},
    {name:"ax",icon:"cib:last-fm"},
  { name: "Google", icon: "cib:amd" },
  { name: "Microsoft", icon: "cib:wiiu" },
  { name: "Amazon", icon: "cib:coreui" },
  { name: "Apple", icon: "cib:digg" },
  { name: "Netflix", icon: "cib:fedex" },
  { name: "Meta", icon: "cib:intel" },
];
</script>
