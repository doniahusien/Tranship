<template>
  <Swiper
    :modules="[Navigation, Autoplay]"
    :slides-per-view="1"
    :loop="true"
    :speed="1800"
    :autoplay="{ delay: 8000 }"
    class="pb-24"
  >
    <SwiperSlide
      v-for="(item, index) in testimonials"
      :key="index"
      class="flex justify-center items-center space-x-5"
    >
      <div class="relative w-full max-w-xl">
        <div
          class="bg-white border border-gray-200 rounded-xl px-8 pt-10 pb-16  relative"
        >
          <p class=" text-text-gray font-light text-sm leading-relaxed">
            <Icon name="bi:quote" class="size-6 mx-auto mb-2" />
            {{ item.text }}
          </p>
          <div class="absolute -bottom-10 left-1/2 -translate-x-1/2">
            <NuxtImg
              :src="item.image"
              class="size-20 rounded-md border-2 border-secondary object-cover"
            />
          </div>
        </div>
        
        <div class="mt-12 text-center">
          <h4 class="font-semibold">{{ item.name }}</h4>
          <span class="text-xs font-light">{{ item.role }}</span>
        </div>
      </div>
    </SwiperSlide>
  </Swiper>
</template>


<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Navigation, Autoplay } from 'swiper/modules'

import 'swiper/css'
import 'swiper/css/navigation'

const testimonials = [
  {
    text: 'Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo.',
    name: 'John Doe',
    role: 'CEO, Company Name',
    image: '/images/food1.png',
  },
  {
    text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit sed do eiusmod.',
    name: 'Jane Smith',
    role: 'Manager, Company Name',
    image: '/images/food1.png',
  },
]
</script>
