<template>
  <Html :lang="locale" :dir="dir">
    <Body :dir="dir">
      <div class="flex min-h-screen flex-col md:mb-0">
   <Header/>
   <Nav/>
        <NoInternetConnection v-if="!isOnline" />
        <div v-else>
          <div class="app_wrapper" id="app_wrapper">
            <slot />
          </div>
        </div>

      </div>
    </Body>
  </Html>
</template>

<script setup>

const i18n = useI18n();
const locale = computed(() => i18n.locale.value);
const isOnline = ref(true);
const dir = computed(() => (locale.value === "ar" ? "rtl" : "ltr"));

onMounted(async () => {

  isOnline.value = window.navigator.onLine;
  window.addEventListener("online", () => (isOnline.value = true));
  window.addEventListener("offline", () => (isOnline.value = false));
 
});

</script>