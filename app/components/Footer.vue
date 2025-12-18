<template>
  <footer class="bg-footer text-white mt-auto">
    <div
      class="container mx-auto px-6 py-16 grid gap-12 md:grid-cols-2 lg:grid-cols-4"
    > <div>
        <h3 class="text-white text-lg font-semibold mb-6">
          {{ $t("FOOTER.aboutUs") }}
        </h3>

        <p class="text-sm leading-relaxed">
          {{ $t("FOOTER.aboutDesc") }}
        </p>

        <button
          aria-label="read more"
          class="mt-4 text-sm text-text hover:underline"
        >
          {{ $t("FOOTER.readMore") }}
        </button>

        <VeeForm @submit.prevent="handleNewsletterSubmit" class="mt-6">
          <div class="relative">
            <inputsBase
            name="email"
              type="email"
              :placeholder="$t('FOOTER.newsletterPlaceholder')"
              class="w-full bg-dark text-sm px-4 py-4 rounded-l focus:outline-none focus:ring-2 focus:ring-accent min-h-12"
            
            />
            <button
              type="submit"
              aria-label="Send newsletter subscription"
              class="absolute inset-y-0 end-0 flex items-center justify-center w-14 min-w-14 bg-accent hover:bg-accent-dark rounded-r"
            >
              <Icon
                name="material-symbols:send-outline"
                class="size-5 text-white"
              />
            </button>
          </div>
        </VeeForm>
      </div>

      <div>
        <h3 class="text-white text-lg font-semibold mb-6">
          {{ $t("FOOTER.navigation") }}
        </h3>

        <ul class="space-y-3 text-sm">
          <li v-for="link in navLinks" :key="link.key">
            <NuxtLink :to="localePath(link.to)">
              {{ $t(`FOOTER.navLinks.${link.key}`) }}
            </NuxtLink>
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
          <li
            v-for="item in contactItems"
            :key="item.textKey"
            class="flex gap-3"
          >
            <Icon :name="item.icon" class="size-7" />
            <span>{{ $t(item.textKey) }}</span>
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
          <li v-for="social in socialLinks" :key="social.label">
            <NuxtLink :to="localePath(social.to)">
              <Icon :name="social.icon" class="size-4" />
              <span class="sr-only">
                {{ $t(`FOOTER.social.${social.label}`) }}
              </span>
            </NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<script setup>
const { locale } = useI18n()
const localePath = useLocalePath()
import { Form as VeeForm } from "vee-validate";


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
})

const servicesList = computed(() => allServices[locale.value] || [])

const navLinks = [
  { key: "home", to: "/" },
  { key: "about", to: "/" },
  { key: "blog", to: "/" },
  { key: "services", to: "/" },
  { key: "contact", to: "/" },
  { key: "sitemap", to: "/" },
]

const contactItems = [
  {
    icon: "material-symbols:map-outline-rounded",
    textKey: "FOOTER.address",
  },
  {
    icon: "fluent:call-20-filled",
    textKey: "FOOTER.phone",
  },
  {
    icon: "ic:round-email",
    textKey: "FOOTER.email",
  },
]

const socialLinks = [
  { icon: "ri:facebook-fill", label: "facebook", to: "/" },
  { icon: "mdi:twitter", label: "twitter", to: "/" },
  { icon: "basil:linkedin-solid", label: "linkedin", to: "/" },
  { icon: "mdi:google-plus", label: "googlePlus", to: "/" },
]

const handleNewsletterSubmit = () => {

}
</script>
