<template>
  <div
    class="conatiner text-center mx-auto flex flex-col items-center justify-center gap-5"
  >
    <h2 class="text-secondary text-lg md:text-2xl font-bold">
      {{ $t("TITLES.WHY_CHOOSE_US") }}
    </h2>
    <p class="text-sm md:textbase max-w-4xl">
      {{ $t("LABELS.WHY_DESC") }}
    </p>
    <div class="container grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-5">
      <div v-for="item in reasons" :key="item.key">
        <div class="flex flex-col items-center justify-center space-y-3">
          <div class="border border-secondary rounded-lg p-3 md:p-4">
            <Icon :name="item.icon" class="size-6 md:size-12 text-secondary" />
          </div>
          <h3 class="text-base md:text-xl font-semibold text-graish uppercase">
            {{ $t(`REASONS.${item.key}.TITLE`) }}
          </h3>
          <p class="text-center text-sm text-text-gray font-light max-w-xl">
            {{ $t(`REASONS.${item.key}.DESC`) }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const { t } = useI18n();
const reasons = ref([
  { key: "SECURE", icon: "tdesign:secured-filled" },
  { key: "FAST_DELIVERY", icon: "material-symbols-light:delivery-truck-speed-outline" },
  { key: "TRACKABLE", icon: "icon-park-outline:connection-point-two" },
  { key: "RELIABLE", icon: "solar:cup-bold" },
]);
</script>

<style scoped></style>
