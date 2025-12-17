<script setup>
const isSticky = ref(false);
const showMega = ref(false);
const showservices = ref(false);
const toggle = ref(false);
const mega = ref([
  "About Us",
  "Project List",
  "Gallery",
  "About Us - Extend",
  "Service List - Extend",
  "Gallery - Extend",
  "Our Team",
  "Service Single",
  "Photo Gallery",
  "Faqs",
  "Service Single - Extend",
  "Photo Gallery - All",
  "Faqs - Extend",
  "Service List",
  "Error 404",

  "Product Lists",
  "Product Single",
  "Project List - Extend",
  "Project Single",
  "Mega Menu New",
  "Typography",
]);
const handleScroll = () => {
  if (window.scrollY > 50) {
    isSticky.value = true;
  } else {
    isSticky.value = false;
  }
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>
<template>
  <nav
    :class="[
      'bg-white fixed p-4 w-full  shadow-md transition-all duration-300 z-50',
      isSticky ? 'fixed ' : 'relative top-12 md:top-14',
    ]"
  >
    <div class="max-w-7xl mx-auto flex items-center justify-between px-6">
      <NuxtImg src="/logo2x.png" class="object-contain w-32 md:w-48" alt="logo" />
      <ul class="hidden md:flex items-center gap-8 text-base font-light">
        <li><NuxtLink class="hover:text-secondary" to="/">Home</NuxtLink></li>
        <li><NuxtLink class="hover:text-secondary" to="/">About Us</NuxtLink></li>
        <li
          class="relative"
          @mouseenter="showservices = true"
          @mouseleave="showservices = false"
        >
          <button class="hover:text-secondary">Our Services <span>▾</span></button>
          <div
            v-if="showservices"
            @mouseenter="showservices = true"
            class="absolute top-full w-66 text-base py-2 px-6 text-white"
          >
            <ul class="space-y-3 bg-secondary mt-5 p-5">
              <li><NuxtLink to="#">Land Transport</NuxtLink></li>
              <li><NuxtLink to="#">WareHousing</NuxtLink></li>
              <li><NuxtLink to="#">Fast Delivery</NuxtLink></li>
              <li><NuxtLink to="#">WorldWide Transport</NuxtLink></li>
              <li><NuxtLink to="#">Sea Freight</NuxtLink></li>
              <li><NuxtLink to="#">Relaible</NuxtLink></li>
            </ul>
          </div>
        </li>
        <li><NuxtLink class="hover:text-secondary" to="#">Blog</NuxtLink></li>

        <li class="relative" @mouseenter="showMega = true" @mouseleave="showMega = false">
          <button class="hover:text-secondary flex items-center gap-1">
            Pages
            <span>▾</span>
          </button>

          <div
            v-show="showMega"
            @mouseenter="showMega = true"
            class="absolute top-full -translate-x-2/3 min-w-7xl mx-auto text-base py-2 text-white"
          >
            <div class="grid grid-cols-4 w-full bg-secondary mt-5 gap-5">
              <div class="col-span-1">
                <NuxtImg src="/images/menubg.jpeg" alt="menu" class="w-full h-full" />
              </div>
              <ul class="col-span-3 py-10 grid grid-cols-3 gap-4 text-sm font-medium">
                <li v-for="item in mega">
                  <Icon name="weui:arrow-outlined" class="text-white align-middle" />
                  <span class="align-middle ml-1 uppercase">{{ item }}</span>
                </li>
              </ul>
            </div>
          </div>
        </li>

        <li><NuxtLink class="hover:text-red-500" to="#">Contact</NuxtLink></li>
        <li>
          <NuxtLink
            class="border font-semibold border-red-500 px-4 py-4 rounded-lg text-red-500"
            to="#"
            >GET A QUOTE</NuxtLink
          >
        </li>
      </ul>

      <button
        @click="toggle = !toggle"
        class="flex md:hidden px-2 items-center rounded-md hover:bg-gray-100 border border-gray-200"
      >
        <Icon name="basil:menu-solid" class="text-black/30 size-8" />
      </button>
      <div
        v-if="toggle == true"
        class="bg-white absolute top-full h-86 left-0 py-5 overflow-y-auto menu w-full text-center"
      >
        <ul class="space-y-6 text-sm">
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary" to="#">Home</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary" to="#">About Us</NuxtLink>
          </li>
              <li class="border-b p-2 border-gray-100"> 
            Our Services
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary font-light" to="#">Land Transport</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary font-light" to="#">Fast Delivery</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary font-light" to="#">WorldWide Transport</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary font-light" to="#">WareHousing</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary font-light" to="#">Sea Freight</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100 font-light">
            <NuxtLink class="hover:text-secondary" to="#">Relaible</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary"  to="#">Blog</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100"> 
            Pages
          </li>

          <li class="border-b p-2 border-gray-100" v-for="item in mega">
            <NuxtLink to="#" class="align-middle ml-1 uppercase font-light">{{ item }}</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-red-500" to="#">Contact</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink
              class="border font-semibold border-red-500 px-4 py-4 rounded-lg text-red-500"
              to="#"
              >GET A QUOTE</NuxtLink
            >
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
