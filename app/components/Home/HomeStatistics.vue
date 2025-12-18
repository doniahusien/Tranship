<template>
  <GeneralSection image="/images/general2.webp">
      <div class=" bg-white rounded-md grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-5">
        <div
          v-for="item in stats"
          class="flex flex-col items-center justify-center py-3 md:p-8"
          :class="{ 'border-e border-dark-gray': item !== stats[stats.length - 1] }"
        >
          <h3 class="flex items-center gap-2">
            <Icon :name="item.icon" class="size-10 text-secondary" />
            <span class="text-3xl font-semibold text-black uppercase">{{
              item.value
            }}
            </span>
          </h3>
          <p class="text-center text-base text-graish font-medium ">
            {{$t(`TITLES.${item.label}`) }}
          </p>
        </div>
      </div>
  </GeneralSection>
</template>
<script setup>
  const {t,locale}= useI18n();
  const isRTL = computed(() => locale.value === 'ar')
const stats = [
  {
    icon: "solar:calendar-outline",
    value: 15,
    label: "officesWorldwide",
  },
  {
    icon: "pepicons-pencil:people",
    value: 97,
    label: "hardworkingPeople",
  },
  {
    icon: "ion:earth-sharp",
    value: 12,
    label: "countriesCovered",
  },
  {
    icon: "pepicons-pencil:people",

    value: 25,
    label: "yearsOfExperience",
  },
];
</script>
