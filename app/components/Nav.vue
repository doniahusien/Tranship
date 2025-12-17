<script setup lang="ts">
const isSticky = ref(false);
const showMega = ref(false);
const showservices = ref(false);
const toggle = ref(false);

const { locale, t } = useI18n();
const switchLocalePath = useSwitchLocalePath();
const targetLocale = computed(() => (locale.value === "ar" ? "en" : "ar"));
const switchPath = computed(() => switchLocalePath(targetLocale.value));

const isRTL = computed(() => locale.value === "ar");
const localePath = useLocalePath();
const route = useRoute();

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
  isSticky.value = window.scrollY > 50;
};

onMounted(() => window.addEventListener("scroll", handleScroll));
onUnmounted(() => window.removeEventListener("scroll", handleScroll));

const isActive = (path: string) =>
  route.path === localePath(path) ? "text-secondary font-semibold" : "";
</script>

<template>
  <nav
    :class="[
      'bg-white fixed w-full shadow-md transition-all duration-300 z-50 p-4',
      isSticky ? 'top-0' : 'relative top-12 md:top-14',
    ]"
  >
    <div class="max-w-7xl mx-auto flex items-center justify-between md:px-6">
      <NuxtImg src="/logo2x.png" class="object-contain w-30 md:w-40 lg:w-48" alt="logo" />

      <ul class="hidden md:flex items-center gap-3 lg:gap-8 text-sm lg:text-base font-light">
        <li>
          <NuxtLink
            :to="localePath('/')"
            :class="[
              isActive('/'),
              'hover:text-secondary transition-colors duration-300',
            ]"
          >
            {{ $t("TITLES.HOME") }}
          </NuxtLink>
        </li>
        <li>
          <NuxtLink
            :to="localePath('/about')"
            :class="[
              isActive('/about'),
              'hover:text-secondary transition-colors duration-300',
            ]"
          >
            {{ $t("TITLES.ABOUT_US") }}
          </NuxtLink>
        </li>

        <li
          class="relative"
          @mouseenter="showservices = true"
          @mouseleave="showservices = false"
        >
          <button class="hover:text-secondary">
            {{ $t("TITLES.OUR_SERVICES") }} <span>▾</span>
          </button>

          <Transition
            enter-active-class="transition ease-out duration-300"
            enter-from-class="opacity-0 translate-y-2"
            enter-to-class="opacity-100 translate-y-0"
            leave-active-class="transition ease-in duration-200"
            leave-from-class="opacity-100 translate-y-0"
            leave-to-class="opacity-0 translate-y-2"
          >
            <div
              v-if="showservices"
              class="absolute top-full w-66 text-base py-2 px-6 text-white"
            >
              <ul class="space-y-3 bg-secondary mt-5 p-5">
                <li
                  v-for="item in [
                    'LAND_TRANSPORT',
                    'WAREHOUSING',
                    'FAST_DELIVERY',
                    'WORLDWIDE_TRANSPORT',
                    'SEA_FREIGHT',
                    'RELIABLE',
                  ]"
                  :key="item"
                >
                  <NuxtLink
                    :to="localePath(`/services/${item}`)"
                    :class="[isActive(`/services/${item}`), 'text-white font-light']"
                  >
                    {{ $t(`TITLES.${item.toUpperCase()}`) }}
                  </NuxtLink>
                </li>
              </ul>
            </div>
          </Transition>
        </li>

        <li>
          <NuxtLink
            :to="localePath('/blog')"
            :class="[
              isActive('/blog'),
              'hover:text-secondary transition-colors duration-300',
            ]"
          >
            {{ $t("TITLES.BLOG") }}
          </NuxtLink>
        </li>

        <li class="relative" @mouseenter="showMega = true" @mouseleave="showMega = false">
          <button class="hover:text-secondary flex items-center gap-1">
            {{ $t("TITLES.PAGES") }} <span>▾</span>
          </button>
          <Transition
            enter-active-class="transition ease-out duration-500"
            enter-from-class="opacity-0 translate-y-2"
            enter-to-class="opacity-100 translate-y-0"
            leave-active-class="transition ease-in duration-400"
            leave-from-class="opacity-100 translate-y-0"
            leave-to-class="opacity-0 translate-y-2"
          >
            <div
              v-show="showMega"
              :class="[isRTL ? 'translate-x-2/3' : '-translate-x-2/3']"
              class="absolute top-full min-w-7xl mx-auto text-base py-2 text-white"
            >
              <div class="grid grid-cols-4 w-full bg-secondary mt-5 gap-5">
                <div class="col-span-1">
                  <NuxtImg src="/images/menubg.jpeg" alt="menu" class="w-full h-full" />
                </div>
                <ul class="col-span-3 py-10 grid grid-cols-3 gap-4 text-sm font-medium">
                  <li v-for="item in mega" :key="item">
                    <Icon
                      :name="
                        isRTL ? 'simple-line-icons:arrow-left' : 'weui:arrow-outlined'
                      "
                      class="text-white align-middle"
                    />
                    <NuxtLink
                      :to="localePath(`/pages/${item}`)"
                      :class="[
                        isActive(`/pages/${item}`),
                        'align-middle ml-1 uppercase font-light',
                      ]"
                    >
                      {{ $t(`TITLES.${item}`) }}
                    </NuxtLink>
                  </li>
                </ul>
              </div>
            </div>
          </Transition>
        </li>

        <li>
          <NuxtLink
            :to="localePath('/contact')"
            :class="[
              isActive('/contact'),
              'hover:text-secondary transition-colors duration-300',
            ]"
          >
            {{ $t("TITLES.CONTACT") }}
          </NuxtLink>
        </li>
        <li>
          <NuxtLink
            :to="localePath('/get-quote')"
            class="border font-semibold border-secondary p-2 md:p-4 rounded-lg text-secondary"
          >
            {{ $t("TITLES.GET_QUOTE") }}
          </NuxtLink>
        </li>

        <NuxtLink :to="switchPath" class="hidden lg:flex items-center text-secondary">
          <Icon name="fluent:globe-48-filled" class="size-5" />
          <span>{{ $t(`locale.${locale}`) }}</span>
        </NuxtLink>
      </ul>

      <button
        @click="toggle = !toggle"
        class="flex md:hidden px-2 items-center rounded-md hover:bg-gray-100 border border-gray-200"
      >
        <Icon name="basil:menu-solid" class="text-black/30 size-8" />
      </button>

      <div
        v-if="toggle"
        class="bg-white absolute top-full h-86 left-0 py-5 overflow-y-auto menu w-full text-center"
      >
        <ul class="space-y-6 text-sm">
          <li
            v-for="link in [
              { name: 'HOME', path: '/' },
              { name: 'ABOUT_US', path: '/about' },
              { name: 'BLOG', path: '/blog' },
              { name: 'CONTACT', path: '/contact' },
            ]"
            :key="link.path"
            class="border-b p-2 border-gray-100"
          >
            <NuxtLink
              :to="localePath(link.path)"
              :class="[
                isActive(link.path),
                'hover:text-secondary transition-colors duration-300',
              ]"
            >
              {{ $t(`TITLES.${link.name}`) }}
            </NuxtLink>
          </li>

          <li class="border-b p-2 border-gray-100">
            {{ $t("TITLES.OUR_SERVICES") }}
            <ul class="mt-2">
              <li
                v-for="item in [
                  'land-transport',
                  'warehousing',
                  'fast-delivery',
                  'worldwide-transport',
                  'sea-freight',
                  'reliable',
                ]"
                :key="item"
                class="border-b p-2 border-gray-100"
              >
                <NuxtLink
                  :to="localePath(`/services/${item}`)"
                  :class="[
                    isActive(`/services/${item}`),
                    'hover:text-secondary font-light transition-colors duration-300',
                  ]"
                >
                  {{ $t(`TITLES.${item.toUpperCase()}`) }}
                </NuxtLink>
              </li>
            </ul>
          </li>

          <li class="border-b p-2 border-gray-100">
            {{ $t("TITLES.PAGES") }}
            <ul class="mt-2">
              <li v-for="item in mega" :key="item" class="border-b p-2 border-gray-100">
                <NuxtLink
                  :to="localePath(`/pages/${item}`)"
                  :class="[
                    isActive(`/pages/${item}`),
                    'hover:text-secondary font-light transition-colors duration-300',
                  ]"
                >
                  {{ $t(`TITLES.${item}`) }}
                </NuxtLink>
              </li>
            </ul>
          </li>

          <li class="border-b p-2 border-gray-100">
            <NuxtLink
              :to="localePath('/get-quote')"
              class="border font-semibold border-secondary px-4 py-4 rounded-lg text-secondary"
            >
              {{ $t("TITLES.GET_QUOTE") }}
            </NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
