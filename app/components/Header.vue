<template>
  <header
    class="bg-dark-white p-2 md:p-4 font-light text-text fixed w-full text-sm md:text-base"
  >
    <div class="max-w-7xl mx-auto flex items-center md:justify-between md:px-6">

      <ul class="flex gap-5">
        <li
          v-for="item in contactInfo"
          :key="item.label"
          :class="item.hiddenOnMobile"
          class="flex items-center justify-center gap-1"
        >
          <Icon
            :name="item.icon"
            class="text-secondary font-semibold"
          />
          <span>{{ item.label }}</span>
        </li>
      </ul>

      <ul class="flex justify-between ms-auto md:ms-0">
        <li
          v-for="social in socialLinks"
          :key="social.label"
        >
          <NuxtLink
            :to="social.to"
            :aria-label="social.label"
          >
            <Icon
              :name="social.icon"
              class="text-secondary mx-2 size-4"
            />
          </NuxtLink>
        </li>
      </ul>

    </div>
  </header>
</template>

<script setup>
const contactInfo = [
  {
    icon: "lineicons:phone",
    label: "1-234-567-8000",
    hiddenOnMobile: "",
  },
  {
    icon: "mdi-light:email",
    label: "tranship@mail.com",
    hiddenOnMobile: "hidden md:flex",
  },
  {
    icon: "mdi-light:clock",
    label: "Sat - Thu: 8AM - 7PM",
    hiddenOnMobile: "hidden md:flex",
  },
]

const socialLinks = [
  {
    icon: "ri:facebook-fill",
    label: "facebook",
    to: "/",
  },
  {
    icon: "mdi:twitter",
    label: "twitter",
    to: "/",
  },
  {
    icon: "basil:linkedin-solid",
    label: "linkedin",
    to: "/",
  },
  {
    icon: "mdi:google-plus",
    label: "google plus",
    to: "/",
  },
]
</script>
