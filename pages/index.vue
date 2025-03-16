<template>
  <div class="flex flex-col gap-1">
    <hero />
    <div class="container mx-auto">
      <div v-if="products" class="flex flex-wrap gap-1 gap-y-2 justify-evenly">
        <product
          v-for="product in products"
          :key="product"
          :product="product"
        />
      </div>
      <loading v-else />
    </div>
  </div>
</template>

<script setup>
let products = ref(null);
fetch("https://fakestoreapi.in/api/products")
  .then((res) => res.json())
  .then(
    (res) =>
      (products.value = res.products.filter((e) => {
        return e.id % 5 == 0;
      }))
  );
</script>
