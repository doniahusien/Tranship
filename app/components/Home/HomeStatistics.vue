<template>
  <GeneralSection image="/images/general2.jpg">
      <div class=" bg-white rounded-md grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-5">
        <div
          v-for="item in stats"
          class="flex flex-col items-center justify-center md:p-8"
          :class="{ 'border-r border-dark-gray': item !== stats[stats.length - 1] }"
        >
          <h3 class="flex items-center gap-2">
            <Icon :name="item.icon" class="size-10 text-secondary" />
            <span class="text-3xl font-semibold text-black uppercase">{{
              item.value
            }}
            </span>
          </h3>
          <p class="text-center text-base text-graish font-medium ">
            {{ item.label }}
          </p>
        </div>
      </div>
  </GeneralSection>
</template>
<script setup>
const stats = [
  {
    icon: "solar:calendar-outline",
    value: 15,
    label: "Offices Worldwide",
  },
  {
    icon: "pepicons-pencil:people",
    value: 97,
    label: "Hardworking People",
  },
  {
    icon: "ion:earth-sharp",
    value: 12,
    label: "Countries Covered",
  },
  {
    icon: "pepicons-pencil:people",

    value: 25,
    label: "Years of Experience",
  },
];
</script>
