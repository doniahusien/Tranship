<script setup lang="ts">
const isSticky = ref(false);
const openMenu = ref<string | null>(null);

const open = (name: string) => (openMenu.value = name);
const close = () => (openMenu.value = null);
const toggle = ref(false);

const { locale, t } = useI18n();
const switchLocalePath = useSwitchLocalePath();
const targetLocale = computed(() => (locale.value === "ar" ? "en" : "ar"));
const switchPath = computed(() => switchLocalePath(targetLocale.value));

const isRTL = computed(() => locale.value === "ar");
const localePath = useLocalePath();
const route = useRoute();

const handleScroll = () => {
  isSticky.value = window.scrollY > 50;
};

onMounted(() => window.addEventListener("scroll", handleScroll));
onUnmounted(() => window.removeEventListener("scroll", handleScroll));

const links = [
  {
    type: "link",
    path: "/",
    name: "HOME",
  },
  {
    type: "link",
    path: "/about",
    name: "ABOUT_US",
  },
  {
    type: "menu",
    path: "/ourservices",
    name: "OUR_SERVICES",
    img: false,
    items: [
      { name: "LAND_TRANSPORT", path: "/services/land-transport" },
      { name: "WAREHOUSING", path: "/services/warehousing" },
      { name: "FAST_DELIVERY", path: "/services/fast-delivery" },
      { name: "WORLDWIDE_TRANSPORT", path: "/services/worldwide-transport" },
      { name: "SEA_FREIGHT", path: "/services/sea-freight" },
      { name: "RELIABLE", path: "/services/reliable" },
    ],
  },
  {
    type: "link",
    path: "/blog",
    name: "BLOG",
  },
  {
    type: "menu",
    path: "/services/extend",
    name: "PAGES",
    img: true,
    items: [
      { name: "ABOUT", path: "/about" },
      { name: "PROJECT_LIST", path: "/projects" },
      { name: "GALLERY", path: "/gallery" },
      { name: "ABOUT_EXTEND", path: "/about/extend" },
      { name: "SERVICE_LIST_EXTEND", path: "/services/extend" },
      { name: "GALLERY_EXTEND", path: "/gallery/extend" },
      { name: "TEAM", path: "/team" },
      { name: "SERVICE_SINGLE", path: "/services/:slug" },
      { name: "PHOTO_GALLERY", path: "/photo-gallery" },
      { name: "FAQS", path: "/faqs" },
      { name: "SERVICE_SINGLE_EXTEND", path: "/services/:slug/extend" },
      { name: "PHOTO_GALLERY_ALL", path: "/photo-gallery/all" },
      { name: "FAQS_EXTEND", path: "/faqs/extend" },
      { name: "SERVICE_LIST", path: "/services" },
      { name: "ERROR_404", path: "/404" },
      { name: "PRODUCT_LIST", path: "/products" },
      { name: "PRODUCT_SINGLE", path: "/products/:slug" },
      { name: "PROJECT_LIST_EXTEND", path: "/projects/extend" },
      { name: "PROJECT_SINGLE", path: "/projects/:slug" },
      { name: "MEGA_NEW", path: "/mega-new" },
      { name: "TYPOGRAPHY", path: "/typography" },
    ],
  },
  {
    type: "link",
    name: "CONTACT",
    path: "/contact",
  },
];
</script>

<template>
  <nav
    :class="[
      'bg-white fixed w-full shadow-md transition-all duration-400 z-50 p-4',
      isSticky ? 'top-0' : 'relative top-12 md:top-14',
    ]"
  >
    <div class="max-w-7xl mx-auto flex items-center justify-between md:px-6">
      <NuxtImg
        src="/logo2x.png"
        class="object-contain w-30 md:w-26 lg:w-45"
        alt="logo"
      />

      <ul
        class="hidden md:flex items-center gap-3 lg:gap-5 text-sm lg:text-base font-light"
      >
        <li v-for="item in links" :key="item.name" class="relative">
          <NuxtLink
            v-if="item.type === 'link'"
            :to="localePath(item.path)"
            class="hover:text-secondary transition-colors duration-300"
            active-class="text-secondary font-semibold"
          >
            {{ $t(`TITLES.${item.name}`) }}
          </NuxtLink>

          <button
            aria-label="menu"
            v-else
            class="hover:text-secondary flex items-center gap-1"
            @mouseenter="open(item.name)"
            @mouseleave="close"
          >
            {{ $t(`TITLES.${item.name}`) }} <span>▾</span>
          </button>

          <Transition
            enter-active-class="transition ease-out duration-300"
            enter-from-class="opacity-0 translate-y-2"
            enter-to-class="opacity-100 translate-y-0"
            leave-active-class="transition ease-in duration-200"
            leave-from-class="opacity-100 translate-y-0"
            leave-to-class="opacity-0 translate-y-2"
          >
            <li
              v-if="openMenu === item.name && !item.img"
              class="absolute top-full mt-4 w-64 bg-secondary p-5"
              @mouseenter="open(item.name)"
              @mouseleave="close"
            >
              <ul class="space-y-3">
                <li v-for="sub in item.items" :key="sub">
                  <NuxtLink
                    :to="localePath(sub.path)"
                    active-class="text-secondary font-semibold"
                    class="text-white hover:text-gray-200 transition"
                  >
                    {{ $t(`TITLES.${sub.name}`) }}
                  </NuxtLink>
                </li>
              </ul>
            </li>
          </Transition>

          <Transition
            enter-active-class="transition ease-out duration-300"
            enter-from-class="opacity-0 translate-y-2"
            enter-to-class="opacity-100 translate-y-0"
            leave-active-class="transition ease-in duration-200"
            leave-from-class="opacity-100 translate-y-0"
            leave-to-class="opacity-0 translate-y-2"
          >
            <li
              v-if="openMenu === item.name && item.img"
              @mouseenter="open(item.name)"
              @mouseleave="close"
              :class="[isRTL ? 'translate-x-1/2' : '-translate-x-1/2']"
              class="absolute top-full min-w-3xl lg:min-w-5xl mx-auto text-base py-2 text-white"
            >
              <div
                class="grid md:grid-cols-3 lg:grid-cols-4 w-full bg-secondary mt-5 gap-5"
              >
                <div class="col-span-1">
                  <NuxtImg
                    src="/images/bannerGeneral.webp"
                    alt="menu"
                    class="w-full h-full"
                  />
                </div>

                <ul
                  class="col-span-2 lg:col-span-3 py-10 grid grid-cols-2 lg:grid-cols-3 gap-4 text-sm font-medium"
                >
                  <li v-for="sub in item.items" :key="sub">
                    <Icon
                      :name="
                        isRTL
                          ? 'simple-line-icons:arrow-left'
                          : 'weui:arrow-outlined'
                      "
                      class="text-white align-middle"
                    />

                    <NuxtLink
                      :to="localePath(sub.path)"
                      class="align-middle ms-1 uppercase font-light"
                      active-class="text-secondary font-semibold"
                    >
                      {{ $t(`TITLES.${sub.name}`) }}
                    </NuxtLink>
                  </li>
                </ul>
              </div>
            </li>
          </Transition>
        </li>
        <li>
          <NuxtLink
            :to="localePath('/')"
            class="border w-fit font-semibold border-secondary p-2 lg:p-3 rounded-lg text-secondary hover:bg-secondary hover:text-white transition-colors duration-500 ease-in-out"
          >
            {{ $t("TITLES.GET_QUOTE") }}
          </NuxtLink>
        </li>
      </ul>
      <NuxtLink
        :to="switchPath"
        class="flex items-center text-secondary ms-auto md:ms-0"
      >
        <Icon name="fluent:globe-48-filled" class="size-5" />
        <span>{{ $t(`locale.${locale}`) }}</span>
      </NuxtLink>
      <button
        aria-label="toggle menu"
        @click="toggle = !toggle"
        class="flex md:hidden px-2 ms-2 items-center rounded-md hover:bg-gray-100 border border-gray-200"
      >
        <Icon name="basil:menu-solid" class="text-black/30 size-8" />
      </button>

      <div
        v-if="toggle == true"
        class="bg-white absolute top-full h-86 start-0 py-5 overflow-y-auto menu w-full text-center"
      >
        <ul class="space-y-6 text-sm">
          <template v-for="item in links" :key="item.name">
            <li class="border-b p-2 border-gray-100">
              <NuxtLink
                :to="localePath(item.path)"
                active-class="text-secondary font-semibold"
                class="hover:text-secondary transition-colors duration-300"
              >
                {{ $t(`TITLES.${item.name}`) }}
              </NuxtLink>
            </li>

            <li
              v-if="item.type === 'menu'"
              v-for="sub in item.items"
              :key="sub"
              class="border-b p-2 border-gray-100"
            >
              <NuxtLink
                :to="localePath(sub.path)"
                active-class="text-secondary font-semibold"
                class="hover:text-secondary font-light transition-colors duration-300"
              >
                {{ $t(`TITLES.${sub.name}`) }}
              </NuxtLink>
            </li>
          </template>

          <li class="border-b p-2 border-gray-100">
            <NuxtLink
              :to="localePath('/')"
              class="border font-semibold border-secondary p-2 md:p-4 rounded-lg text-secondary"
            >
              {{ $t("TITLES.GET_QUOTE") }}
            </NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
