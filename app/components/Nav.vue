<script setup>
const isSticky = ref(false);
const showMega = ref(false);
const showservices = ref(false);
const toggle = ref(false);

const { locale, t, setLocale } = useI18n();
const switchLocalePath = useSwitchLocalePath();
const targetLocale = computed(() => (locale.value === "ar" ? "en" : "ar"));
const switchPath = computed(() => switchLocalePath(targetLocale.value));

const isRTL = computed(() => locale.value === 'ar')
const localePath= useLocalePath();
const mega = ref([
  "ABOUT",
  "PROJECT_LIST",
  "GALLERY",
  "ABOUT_EXTEND",
  "SERVICE_LIST_EXTEND",
  "GALLERY_EXTEND",
  "TEAM",
  "SERVICE_SINGLE",
  "PHOTO_GALLERY",
  "FAQS",
  "SERVICE_SINGLE_EXTEND",
  "PHOTO_GALLERY_ALL",
  "FAQS_EXTEND",
  "SERVICE_LIST",
  "ERROR_404",
  "PRODUCT_LIST",
  "PRODUCT_SINGLE",
  "PROJECT_LIST_EXTEND",
  "PROJECT_SINGLE",
  "MEGA_NEW",
  "TYPOGRAPHY",
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
    <div class="max-w-7xl mx-auto flex items-center justify-between md:px-6">
      <NuxtImg src="/logo2x.png" class="object-contain w-32 md:w-48" alt="logo" />
      <ul class="hidden md:flex items-center gap-8 text-base font-light">
        <li><NuxtLink class="hover:text-secondary" :to="localePath('/')">{{$t('TITLES.HOME')}}</NuxtLink></li>
        <li><NuxtLink class="hover:text-secondary" :to="localePath('/about')">{{$t('TITLES.ABOUT_US')}}</NuxtLink></li>
        <li
          class="relative"
          @mouseenter="showservices = true"
          @mouseleave="showservices = false"
        >
          <button class="hover:text-secondary">{{$t('TITLES.OUR_SERVICES')}} <span>▾</span></button>
          <div
            v-if="showservices"
            @mouseenter="showservices = true"
            class="absolute top-full w-66 text-base py-2 px-6 text-white"
          >
            <ul class="space-y-3 bg-secondary mt-5 p-5">
              <li><NuxtLink :to="localePath('/services/land-transport')">{{$t('TITLES.LAND_TRANSPORT')}}</NuxtLink></li>
              <li><NuxtLink :to="localePath('/services/warehousing')">{{$t('TITLES.WAREHOUSING')}}</NuxtLink></li>
              <li><NuxtLink :to="localePath('/services/fast-delivery')">{{$t('TITLES.FAST_DELIVERY')}}</NuxtLink></li>
              <li><NuxtLink :to="localePath('/services/worldwide-transport')">{{$t('TITLES.WORLDWIDE_TRANSPORT')}}</NuxtLink></li>
              <li><NuxtLink :to="localePath('/services/sea-freight')">{{$t('TITLES.SEA_FREIGHT')}}</NuxtLink></li>
              <li><NuxtLink :to="localePath('/services/reliable')">{{$t('TITLES.RELIABLE')}}</NuxtLink></li>
            </ul>
          </div>
        </li>
        <li><NuxtLink class="hover:text-secondary" :to="localePath('/blog')">{{$t('TITLES.BLOG')}}</NuxtLink></li>

        <li class="relative" @mouseenter="showMega = true" @mouseleave="showMega = false">
          <button class="hover:text-secondary flex items-center gap-1">
           {{$t('TITLES.PAGES')}}
            <span>▾</span>
          </button>

          <div
            v-show="showMega"
            @mouseenter="showMega = true"
            :class="[
  isRTL ? 'translate-x-2/3' : '-translate-x-2/3'
]"
            class="absolute top-full min-w-7xl mx-auto text-base py-2 text-white"
          >
            <div class="grid grid-cols-4 w-full bg-secondary mt-5 gap-5">
              <div class="col-span-1">
                <NuxtImg src="/images/menubg.jpeg" alt="menu" class="w-full h-full" />
              </div>
              <ul class="col-span-3 py-10 grid grid-cols-3 gap-4 text-sm font-medium">
                <li v-for="item in mega">
                  <Icon :name="isRTL ? 'simple-line-icons:arrow-left' : 'weui:arrow-outlined'" class="text-white align-middle" />
                  <NuxtLink :to="localePath(`/pages/${item}`)" class="align-middle ml-1 uppercase"> {{ $t(`TITLES.${item}`) }}</NuxtLink>
                </li>
              </ul>
            </div>
          </div>
        </li>

        <li><NuxtLink class="hover:text-red-500" :to="localePath('/contact')">{{$t('TITLES.CONTACT')}}</NuxtLink></li>
        <li>
          <NuxtLink
            class="border font-semibold border-red-500 px-4 py-4 rounded-lg text-secondary"
           :to="localePath('/get-quote')"
            >{{$t("TITLES.GET_QUOTE")}}</NuxtLink
          >
        </li>
            <NuxtLink :to="switchPath" class="hidden lg:flex items-center text-secondary">
            <Icon name="fluent:globe-48-filled" class="size-5" />
            <span> {{ $t(`locale.${locale}`) }}</span>
          </NuxtLink>
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
            <NuxtLink class="hover:text-secondary" :to="localePath('/')">{{$t('TITLES.HOME')}}</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary" :to="localePath('/about')">{{$t('TITLES.ABOUT_US')}}</NuxtLink>
          </li>
              <li class="border-b p-2 border-gray-100"> 
           {{$t('TITLES.OUR_SERVICES')}}
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary font-light" :to="localePath('/services/land-transport')">
                       {{$t('TITLES.LAND_TRANSPORT')}}
            </NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary font-light" :to="localePath('/services/fast-delivery')">           {{$t('TITLES.FAST_DELIVERY')}}</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary font-light" :to="localePath('/services/worldwide-transport')">           {{$t('TITLES.WORLDWIDE_TRANSPORT')}}</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary font-light" :to="localePath('/services/warehousing')">           {{$t('TITLES.WAREHOUSING')}}</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary font-light" :to="localePath('/services/sea-freight')">           {{$t('TITLES.SEA_FREIGHT')}}</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100 font-light">
            <NuxtLink class="hover:text-secondary" :to="localePath('/services/reliable')">           {{$t('TITLES.RELIABLE')}}</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary"  :to="localePath('/blog')">           {{$t('TITLES.BLOG')}}</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100"> 
           {{$t('TITLES.PAGES')}}          </li>

          <li class="border-b p-2 border-gray-100" v-for="item in mega">
            <NuxtLink :to="localePath(`/pages/${item}`)" class="align-middle ml-1 uppercase font-light"> {{ $t(`TITLES.${item}`) }}</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink class="hover:text-secondary" :to="localePath('/contact')">           {{$t('TITLES.CONTACT')}}</NuxtLink>
          </li>
          <li class="border-b p-2 border-gray-100">
            <NuxtLink
              class="border font-semibold border-secondary p-4 rounded-lg text-secondary"
              :to="localePath('/get-quote')"
              >           {{$t('TITLES.GET_QUOTE')}}</NuxtLink
            >
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
