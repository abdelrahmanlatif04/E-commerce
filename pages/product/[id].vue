<template>
  <div class="view-product p-8 mx-auto max-w-4xl">
    <img
      :src="product.image"
      :alt="product.title"
      class="w-full h-96 object-contain bg-white mb-8 rounded"
    />
    <h1 class="text-4xl font-bold mb-4 text-gold">{{ product.title }}</h1>
    <p class="text-ivory-white mb-6">{{ product.description }}</p>
    <div class="grid grid-cols-2 gap-4">
      <p class="text-gold font-semibold">Brand: {{ product.brand }}</p>
      <p class="text-ivory-white">Model: {{ product.model }}</p>
      <p class="text-ivory-white">Color: {{ product.color }}</p>
      <p class="text-ivory-white">Category: {{ product.category }}</p>
    </div>


<!--     
    <div class="flex justify-center gap-5" v-if="product.discount">
      <p class="class=text-gold font-bold text-3xl mt-6">
        ${{ product.price - product.discount }}
      </p>
      <p class="text-red-800 line-through text-xl">${{ product.price }}</p>
    </div> -->
  </div>
</template>

<script setup>
const route = useRoute();
const product = ref(null);
const { data, pending, error } = await useFetch(
  `https://fakestoreapi.in/api/products/${route.params.id}`
);

if (data.value?.status === "SUCCESS") {
  product.value = data.value.product;
}
</script>

d
<style scoped>
.view-product {
  background-color: #0b1e36;
  color: #f8f1e5;
}
.text-gold {
  color: #cba135;
}
.text-ivory-white {
  color: #f8f1e5;
}
.text-burgundy {
  color: #800020;
}
</style>
