<template>
  <div class="grid grid-cols-1 gap-5 md:grid-cols-2 container mx-auto">
    <div class="flex flex-col bg-light-gray">
      <div class="grid grid-cols-3">
        <button
          @click="activeCategory = item"
          v-for="item in categories"
          class="flex flex-col justify-center items-center p-2 md:p-4"
          :class="activeCategory.name === item.name ? 'bg-light-gray' : 'bg-dark-gray'"
        >
          <Icon :name="item.icon" class="size-8 md:size-10 text-secondary" />
          <span class=" text-xs md:text-base text-text-gray">{{ item.name }}</span>
        </button>
      </div>
      <div class="p-5 space-y-4">
        <h3 class="text-secondary text-xl font-semibold">
          {{ activeCategory.name }}
        </h3>

        <p class="text-text font-light leading-relaxed text-base">
          {{ activeCategory.desc }}
        </p>

        <button class=" text-secondary rounded-md border border-secondary py-2 px-4">
          Read more
        </button>
      </div>
    </div>
    <div class="space-y-5 md:px-8">
    <h2 class="text-xl md:text-3xl font-bold text-secondary">
    About us
    </h2>
    
    <p class="text-graish font-light text-2xl md:text-5xl">Sed ut perspiciatis unde omnis iste natus error sit voluptatem</p>
    <p class="font-light">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip exea...</p>
       <button class="text-secondary rounded-md border border-secondary py-2 px-4">
          Read more
        </button>
    </div>
  </div>
</template>

<script setup lang="ts">
const categories = ref([
  {
    name: "Land Transport",
    icon: "hugeicons:truck-delivery",
    desc:
      "Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores.",
  },
  {
    name: "WorldWide Transport",
    icon: "mdi:flight",
    desc:
      "Voluptatem quia voluptas sit aspernatur aut odit aut fugit . Perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam, sed quia consequuntur magni dolores.",
  },
  {
    name: "Own Warehousing",
    icon: "solar:delivery-linear",
    desc:
      "Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores.",
  },
]);
const activeCategory = ref(categories.value[0]);
</script>

<style scoped></style>
