<template>
  <footer class="bg-footer text-gray-300">
    <div class="container mx-auto px-6 py-16 grid gap-12 md:grid-cols-2 lg:grid-cols-4">
      <div>
        <h3 class="text-white text-lg font-semibold mb-6">{{ $t("FOOTER.aboutUs") }}</h3>
        <p class="text-sm leading-relaxed">{{ $t("FOOTER.aboutDesc") }}</p>

        <button class="mt-4 text-sm text-text hover:underline">
          {{ $t("FOOTER.readMore") }}
        </button>

        <div class="mt-6 relative">
          <input
            type="email"
            :placeholder="$t('FOOTER.newsletterPlaceholder')"
            class="w-full bg-dark text-sm px-4 py-3 rounded focus:outline-none"
          />
          <button class="absolute end-3 top-1/2 -translate-y-1/2 text-text">
            <Icon name="bytesize:send" />
          </button>
        </div>
      </div>

      <div>
        <h3 class="text-white text-lg font-semibold mb-6">
          {{ $t("FOOTER.navigation") }}
        </h3>
        <ul class="space-y-3 text-sm">
          <li>
            <NuxtLink :to="localePath('/')">{{ $t("FOOTER.navLinks.home") }}</NuxtLink>
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
const { t,locale } = useI18n();
const localePath = useLocalePath();
const allServices = reactive({
  ar: ["النقل البري","التخزين","التوصيل السريع","النقل العالمي","الشحن البحري","موثوق"],
  en: ["Land Transport","Storage","Express Delivery","Global Shipping","Sea Freight","Reliable"]
})

const servicesList = computed(() => allServices[locale.value] || [])
</script>
