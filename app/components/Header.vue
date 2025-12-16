<template>
  <header class=" bg-dark-white p-2 md:p-4 font-light fixed w-full flex justify-between md:justify-around flex-wrap md:text-base font-400">
    <ul class="flex items-center justify-center gap-5">
      <li class="flex items-center justify-center gap-1 ">
        <Icon name="lineicons:phone" class="text-secondary " />
        <span  >1-234-567-8000</span>
      </li>
      <li class=" hidden md:flex items-center justify-center gap-1">
        <Icon name="mdi-light:email" class="text-secondary" />
        <span >tranship@mail.com</span>
      </li>
      <li class="hidden md:flex items-center justify-center gap-1">
        <Icon name="mdi-light:clock" class="text-secondary" />
        <span>Sat - Thu: 8AM - 7PM</span>
      </li>
    </ul>
    <ul class="flex justify-between ms-auto md:ms-0 ">
      <li>
        <a href="#">
          <Icon name="ri:facebook-fill" class="text-secondary mx-2 size-4" />
        </a>
      </li>
      <li>
        <a href="#">
          <Icon name="mdi:twitter" class="text-secondary mx-2 size-4" />
        </a>
      </li>
      <li>
        <a href="#">
          <Icon name="basil:linkedin-solid" class="text-secondary mx-2 size-4" />
        </a>
      </li>
      <li>
        <a href="#">
          <Icon name="mdi:google-plus" class="text-secondary mx-2 size-4" />
        </a>
      </li>
    </ul>
  </header>
</template>
