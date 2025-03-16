<template>
  <div class="container mx-auto px-4 py-10">
    <!-- Loading State -->
    <div v-if="pending" class="text-center text-lg font-semibold text-gray-600">
      Loading product...
    </div>

    <!-- Error State -->
    <div v-else-if="error" class="text-center text-red-500 font-semibold">
      Failed to load product. Please try again.
    </div>

    <!-- Product Details -->
    <div
      v-else-if="product"
      class="max-w-5xl mx-auto flex flex-col md:flex-row gap-10"
    >
      <!-- Product Image -->
      <div class="flex-1">
        <img
          :src="product.image"
          :alt="product.title"
          class="w-full h-auto object-cover rounded-2xl shadow-lg border border-gray-200"
        />
      </div>

      <!-- Product Info -->
      <div class="flex-1 space-y-5">
        <h1 class="text-3xl font-bold text-gray-900">{{ product.title }}</h1>
        <p class="text-lg text-gray-600 leading-relaxed">
          {{ product.description }}
        </p>

        <div class="flex items-center gap-4">
          <span class="text-2xl font-semibold text-gold-600"
            >${{ product.price }}</span
          >
          <span
            v-if="product.discount"
            class="text-red-500 text-lg font-semibold line-through"
          >
            ${{ product.originalPrice }}
          </span>
        </div>

        <button
          class="bg-gold-600 text-white py-3 px-8 rounded-lg font-semibold shadow-md hover:bg-gold-700 transition"
        >
          Add to Cart
        </button>
      </div>
    </div>
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
