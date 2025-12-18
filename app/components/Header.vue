<template>
  <header class=" bg-dark-white p-2 md:p-4 font-light fixed  w-full text-sm md:text-base">
    <div class="max-w-7xl mx-auto flex items-center md:justify-between md:px-6">
    <ul class="flex gap-5">
      <li class="flex items-center justify-center gap-1 ">
        <Icon name="lineicons:phone" class="text-secondary font-semibold" />
        <span  >1-234-567-8000</span>
      </li>
      <li class=" hidden md:flex items-center justify-center gap-1">
        <Icon name="mdi-light:email" class="text-secondary font-semibold" />
        <span >tranship@mail.com</span>
      </li>
      <li class="hidden md:flex items-center justify-center gap-1">
        <Icon name="mdi-light:clock" class="text-secondary font-semibold" />
        <span>Sat - Thu: 8AM - 7PM</span>
      </li>
    </ul>
    <ul class="flex justify-between ms-auto md:ms-0 ">
      <li>
        <NuxtLink to="/" aria-label="facebook">
          <Icon name="ri:facebook-fill" class="text-secondary mx-2 size-4" />
        </NuxtLink>
      </li>
      <li>
        <NuxtLink to="/" aria-label="twitter">
          <Icon name="mdi:twitter" class="text-secondary mx-2 size-4" />
        </NuxtLink>
      </li>
      <li>
        <NuxtLink to="/" aria-label="linkedin">
          <Icon name="basil:linkedin-solid" class="text-secondary mx-2 size-4" />
        </NuxtLink>
      </li>
      <li>
        <NuxtLink to="/" aria-label="google plus">
          <Icon name="mdi:google-plus" class="text-secondary mx-2 size-4" />
        </NuxtLink>
      </li>
    </ul>
    </div>
  </header>
</template>
