<template>
  <div class="container mx-auto mt-5">
    <div class="w-full flex flex-col gap-5 items-center mb-10">
      <div
        class="w-full min-w-52 max-w-[650px] relative overflow-hidden rounded-3xl"
      >
        <input type="text"
        
        class="bg-white focus:outline-0 w-full p-2" />
        <button
          class="absolute right-0 top-0 h-full bg-[#fa0] aspect-square transition-all hover:opacity-35 cursor-pointer"
        >
          <img src="/search.png" class="mx-auto w-2/3 invert" />
        </button>
      </div>
      <div
        v-if="categories"
        class="grid grid-cols-3 text-xl w-full md:grid-cols-6 gap-y-2 gap-2 p-2"
      > 
        <router-link
          :to="'/category/' + category"
          class="bg-[#800020] text-[#F8F1E5] w-full text-center hover:opacity-70 transition-all rounded-3xl p-2"
          v-for="category in categories"
          :key="category"
        >
          {{ category[0].toUpperCase() + category.slice(1) }}
        </router-link>
      </div>
    </div>

    <div v-if="products" class="flex flex-wrap gap-1 gap-y-2 justify-evenly">
      <product v-for="product in products" :key="product" :product="product" />
    </div>
    <loading v-else />
  </div>
</template>

<script setup>
let categories = ref(null);

fetch("https://fakestoreapi.in/api/products/category")
  .then((res) => res.json())
  .then((res) => (categories.value = res["categories"]));

let products = ref(null);
fetch("https://fakestoreapi.in/api/products")
  .then((res) => res.json())
  .then((res) => (products.value = res.products));
</script>

<style></style>
