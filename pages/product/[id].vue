<template>
  <div class="view-product p-8 mx-auto max-w-4xl flex flex-col gap-1">
    <div class="w-full h-96 mb-8 relative rounded-xl overflow-hidden">
      <img
        :src="product.image"
        :alt="product.title"
        class="w-full h-full object-contain bg-white rounded"
      />
      <p
        class="text-[#f8f1e5] font-semibold text-xl absolute left-0 top-0 bg-[#800020] p-2 rounded-br-xl"
      >
        {{ product.brand }}
      </p>

      <p
        class="text-ivory-white text-xl bg-[#cba135] absolute p-2 rounded-bl-xl right-0 top-0"
      >
        {{ product.category }}
      </p>
    </div>
    <h1 class="text-3xl font-bold mb-4 text-gold text-center md:text-left">
      {{ product.title }}
    </h1>

    <p class="text-ivory-white mb-6 text-center md:text-left">
      {{ product.description }}
    </p>
    <div class="flex flex-col gap-2">
      <p class="text-ivory-white font-semibold text-xl">
        Model : {{ product.model }}
      </p>
      <p class="text-ivory-white font-semibold text-xl">
        Color : {{ product.color }}
      </p>

      <p class="text-xl text-[#F8F1E5] font-semibold flex items-center gap-1">
        Price :
        <span class="text-[#CBA135]"
          >${{
          this.product.discount
            ? (this.product.price * (1 - this.product.discount / 100)).toFixed(
                2
              )
            : this.product.price
          }}</span
        >
        <span v-if="product.discount" class="text-red-400 line-through ml-1">
          ${{ product.price }}
        </span>
      </p>
    </div>
    <button
      class="bg-[#cba135] border-[3px] border-[#cba135] cursor-pointer transition-all text-[#F8F1E5] py-2 rounded-lg shadow hover:text-[#cba135] font-semibold hover:bg-transparent hover:shadow-xl self-center w-32 text-center"
    >
      Add to Cart
    </button>
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
