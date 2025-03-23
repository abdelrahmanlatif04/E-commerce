<template>
  <div class="w-full bg-[#CBA135] py-1">
    <div
      class="h-10 min-w-96 max-w-[650px] w-full mx-auto grid gap-2 place-content-center grid-cols-4 text-[#F8F1E5] font-bold tracking-wide"
    >
      <NuxtLink
        class="flex justify-center items-center gap-3 hover:opacity-70 text-black tracking-wider"
        v-for="(route, i) in routes"
        :key="route"
        :to="route"
      >
        <img :src="`/${i}.png`" class="w-6.5" />
        <div class="hidden sm:block">
          {{ i }}
        </div>
      </NuxtLink>
    </div>
  </div>
</template>

<script setup>
let routes = ref({
  Home: "/",
  Categories: "/category/general",
  User: "/user",
  Cart: "/cart",
});
</script>

<style>
.router-link-active {
  @apply invert;
}
</style>
