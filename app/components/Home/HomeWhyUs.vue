<template>
  <div
    class="conatiner text-center mx-auto flex flex-col items-center justify-center gap-5"
  >
    <h2 class="text-secondary text-lg md:text-2xl font-bold">WHY CHOOSE US</h2>
    <p class="max-w-4xl">
      Lorem ipsum dolor sit amet consectetur to adipiscing elit, sed dot eiusmod tempor
      incididunt labore et dolore magna aliqua. Veniam quis nostrud exercitation ullamco
      laboris nisiut.
    </p>
    <div class="container grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-5">
      <div v-for="item in reasons">
        <div class="flex flex-col items-center justify-center space-y-3">
          <div class="border border-secondary rounded-lg p-4">
            <Icon
              :name="item.icon"
              class="size-12 text-secondary"
            />
          </div>
          <h3 class="text-xl font-semibold text-graish uppercase">{{ item.title }}</h3>
          <p class="text-center text-sm text-text-gray font-light max-w-xl">{{ item.desc }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const reasons = ref([
  {
    title: "Secure",
    desc:
      "Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusant iudol oremq dauri.",
    icon: "tdesign:secured-filled",
  },
  {
    title: "fast delivery",
    desc:
      "Accusan tiused ut perspiciatis unde omnis iste natus error sit voluptatem dolore mque.",
    icon: "material-symbols-light:delivery-truck-speed-outline",
  },
  {
    title: "Trackable",
    desc:
      "Voluptatem sed ut perspiciatis unde omnis iste natus error sit accusantiu dolo remque laud.",
    icon: "icon-park-outline:connection-point-two",
  },
  {
    title: "Reliable",
    desc:
      "Perspiciatis sed ut unde omnis iste natus error sit voluptatem accusantiu dolor emques.",
    icon: "solar:cup-bold",
  },
]);
</script>

<style scoped></style>
