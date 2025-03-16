<template>
  <div class="w-full bg-[#CBA135] py-1">
    <div
      class="h-10 min-w-96 max-w-[650px] w-full mx-auto grid gap-2 place-content-center grid-cols-4 text-[#F8F1E5] font-bold tracking-wide"
    >
      <NuxtLink
        class="text-center hover:opacity-70 text-[#0B1E36] tracking-wider"
        v-for="(route, i) in routes"
        :key="route"
        :to="route"
        >{{ i }}</NuxtLink
      >
    </div>
  </div>
</template>

<script setup>

let routes = ref({
  Home: "/",
  Categories: "/category/general",
  Account: "/account",
  Cart: "/cateagory",
});
</script>
