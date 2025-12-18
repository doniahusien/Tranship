<template>
  <div class="grid grid-cols-1 gap-5 md:grid-cols-2 container mx-auto">

    <div class="flex flex-col bg-light-gray">
  
      <div class="grid grid-cols-3">
        <button
        aria-label="set active category"
          v-for="item in categories"
          :key="item.key"
          @click="setActiveCategory(item.key)"
          class="flex flex-col justify-center items-center p-2 md:p-4
                 transition-all duration-300 ease-in-out
                "
          :class="activeCategoryKey === item.key
            ? 'bg-light-gray'
            : 'bg-dark-gray opacity-70 hover:opacity-100'"
        >
          <Icon :name="item.icon" class="size-8 md:size-10 text-secondary" />
          <span class="text-xs md:text-base text-text-gray">
            {{ t(`CATEGORIES.${item.key}.NAME`) }}
          </span>
        </button>
      </div>

      <div>
        <Transition
          enter-active-class="transition-all duration-500 ease-out"
          enter-from-class="opacity-0 translate-y-3"
          enter-to-class="opacity-100 translate-y-0"
          leave-active-class="transition-all duration-500 ease-in"
          leave-from-class="opacity-100 translate-y-0"
          leave-to-class="opacity-0 -translate-y-4"
          mode="out-in"
        >
          <div :key="activeCategoryKey" class="p-5 space-y-4">
            <h3 class="text-secondary text-xl font-semibold">
              {{ activeCategory.name }}
            </h3>

            <p class="text-text font-light leading-relaxed text-base">
              {{ activeCategory.desc }}
            </p>

            <NuxtLink
            aria-label="Read more"
              :to="localePath(`/`)"
              class="inline-block text-secondary rounded-md border border-secondary py-2 px-4
                     transition hover:bg-secondary hover:text-white"
            >
              {{ $t("TITLES.READ_MORE") }}
            </NuxtLink>
          </div>
        </Transition>
      </div>
    </div>

    <div class="space-y-5 p-2 md:px-8">
      <h2 class="text-xl md:text-3xl font-bold text-secondary">
        {{ $t("TITLES.ABOUT_US") }}
      </h2>

      <p class="text-graish font-light text-2xl md:text-5xl">
        {{ $t("LABELS.ABOUT_SUBTITLE") }}
      </p>

      <p class="font-light">
        {{ $t("LABELS.ABOUT_DESC") }}
      </p>

      <button
      aria-label="read more about us"
        class="text-secondary rounded-md border border-secondary py-2 px-4
                 hover:bg-secondary hover:text-white"
      >
        {{ $t("TITLES.READ_MORE") }}
      </button>
    </div>
  </div>
</template>


<script setup lang="ts">
const { t } = useI18n();
const localePath = useLocalePath();
const categories = ref([
  {
    key: "LAND_TRANSPORT",
    icon: "hugeicons:truck-delivery",
  },
  {
    key: "WORLDWIDE_TRANSPORT",
    icon: "mdi:flight",
  },
  {
    key: "WAREHOUSING",
    icon: "solar:delivery-linear",
  },
]);

const activeCategoryKey = ref(categories.value[0].key);

const activeCategory = computed(() => {
  const key = activeCategoryKey.value;
  return {
    key,
    name: t(`CATEGORIES.${key}.NAME`),
    desc: t(`CATEGORIES.${key}.DESC`),
    icon: categories.value.find((c) => c.key === key)?.icon,
  };
});

const setActiveCategory = (key: string) => {
  activeCategoryKey.value = key;
};
</script>

<style scoped></style>
