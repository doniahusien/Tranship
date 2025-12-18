<template>
  <footer class="bg-footer text-white mt-auto">
    <div
      class="container mx-auto px-6 py-16 grid gap-12 md:grid-cols-2 lg:grid-cols-4"
    >
      <div>
        <h3 class="text-white text-lg font-semibold mb-6">
          {{ $t("FOOTER.aboutUs") }}
        </h3>
        <p class="text-sm leading-relaxed">{{ $t("FOOTER.aboutDesc") }}</p>

        <button
          aria-label="read more"
          class="mt-4 text-sm text-text hover:underline"
        >
          {{ $t("FOOTER.readMore") }}
        </button>

        <form @submit.prevent="handleNewsletterSubmit" class="mt-6">
          <div class="relative">
            <input
              type="email"
              :placeholder="$t('FOOTER.newsletterPlaceholder')"
              class="w-full bg-dark text-sm px-4 py-4 rounded-l focus:outline-none focus:ring-2 focus:ring-accent min-h-12"
              required
            />
            <button
              type="submit"
              aria-label="Send newsletter subscription"
              class="absolute inset-y-0 end-0 flex items-center justify-center w-14 min-w-14 bg-accent hover:bg-accent-dark rounded-r"
            >
              <svg
                class="h-6 w-6 text-white"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M14 5l7 7m0 0l-7 7m7-7H3"
                />
              </svg>
            </button>
          </div>
        </form>
      </div>

      <div>
        <h3 class="text-white text-lg font-semibold mb-6">
          {{ $t("FOOTER.navigation") }}
        </h3>
        <ul class="space-y-3 text-sm">
          <li>
            <NuxtLink :to="localePath('/')">{{
              $t("FOOTER.navLinks.home")
            }}</NuxtLink>
          </li>
          <li>
            <NuxtLink :to="localePath('/')">{{
              $t("FOOTER.navLinks.about")
            }}</NuxtLink>
          </li>
          <li>
            <NuxtLink :to="localePath('/')">{{
              $t("FOOTER.navLinks.blog")
            }}</NuxtLink>
          </li>
          <li>
            <NuxtLink :to="localePath('/')">{{
              $t("FOOTER.navLinks.services")
            }}</NuxtLink>
          </li>
          <li>
            <NuxtLink :to="localePath('/')">{{
              $t("FOOTER.navLinks.contact")
            }}</NuxtLink>
          </li>
          <li>
            <NuxtLink :to="localePath('/')">{{
              $t("FOOTER.navLinks.sitemap")
            }}</NuxtLink>
          </li>
        </ul>
      </div>

      <div>
        <h3 class="text-white text-lg font-semibold mb-6">
          {{ $t("FOOTER.ourServices") }}
        </h3>
        <ul class="space-y-3 text-sm">
          <li v-for="service in servicesList" :key="service">
            <NuxtLink :to="localePath('/')">
              {{ service }}
            </NuxtLink>
          </li>
        </ul>
      </div>

      <div>
        <h3 class="text-white text-lg font-semibold mb-6">
          {{ $t("FOOTER.contactUs") }}
        </h3>
        <ul class="space-y-5 text-sm">
          <li class="flex gap-3">
            <Icon name="material-symbols:map-outline-rounded" class="size-7" />
            <span>{{ $t("FOOTER.address") }}</span>
          </li>
          <li class="flex gap-3">
            <Icon name="fluent:call-20-filled" class="size-7" />
            <span>{{ $t("FOOTER.phone") }}</span>
          </li>
          <li class="flex gap-3">
            <Icon name="ic:round-email" class="size-7" />
            <span>{{ $t("FOOTER.email") }}</span>
          </li>
        </ul>
      </div>
    </div>

    <div class="py-6 bg-dark-footer">
      <div
        class="container mx-auto px-6 flex flex-col md:flex-row justify-between items-center gap-4 text-sm"
      >
        <p>{{ $t("FOOTER.copyright") }}</p>

        <ul class="flex justify-between md:justify-start gap-3">
          <li>
            <NuxtLink :to="localePath('/')">
              <Icon name="ri:facebook-fill" class="size-4" />
              <span class="sr-only">{{ $t("FOOTER.social.facebook") }}</span>
            </NuxtLink>
          </li>
          <li>
            <NuxtLink :to="localePath('/')">
              <Icon name="mdi:twitter" class="size-4" />
              <span class="sr-only">{{ $t("FOOTER.social.twitter") }}</span>
            </NuxtLink>
          </li>
          <li>
            <NuxtLink :to="localePath('/')">
              <Icon name="basil:linkedin-solid" class="size-4" />
              <span class="sr-only">{{ $t("FOOTER.social.linkedin") }}</span>
            </NuxtLink>
          </li>
          <li>
            <NuxtLink :to="localePath('/')">
              <Icon name="mdi:google-plus" class="size-4" />
              <span class="sr-only">{{ $t("FOOTER.social.googlePlus") }}</span>
            </NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<script setup>
const { t, locale } = useI18n();
const localePath = useLocalePath();
const allServices = reactive({
  ar: [
    "النقل البري",
    "التخزين",
    "التوصيل السريع",
    "النقل العالمي",
    "الشحن البحري",
    "موثوق",
  ],
  en: [
    "Land Transport",
    "Storage",
    "Express Delivery",
    "Global Shipping",
    "Sea Freight",
    "Reliable",
  ],
});

const servicesList = computed(() => allServices[locale.value] || []);
</script>
