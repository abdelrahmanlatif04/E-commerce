<template>
  <div
    class="max-w-sm h-fit rounded-2xl overflow-hidden relative shadow-lg bg-white p-4 my-auto text-[#F8F1E5]"
  >
    <div class="w-full aspect-[1.5] relative">
      <img
        :src="product.image"
        :alt="product.title"
        class="w-full h-full object-contain rounded-lg"
      />
      <span
        class="font-bold absolute left-0 bottom-0 text-[#CBA135] px-2 py-1 bg-[#0B1E36]/80 rounded-tr-lg"
      >
        {{ product.brand[0].toUpperCase() + product.brand.slice(1) }}
      </span>
      <span
        class="font-bold absolute right-0 bottom-0 px-2 py-1 bg-[#800020] text-[#F8F1E5] rounded-tl-lg"
        v-if="product.discount"
      >
        {{ product.discount }} %
      </span>
    </div>

    <div class="flex flex-col gap-2">
      <h2 class="text-2xl font-semibold text-[#CBA135]">{{ product.title }}</h2>
      <p class="text-slate-500 text-sm">
        {{ product.description.slice(0, 200) }}
      </p>

      <p class="text-[#CBA135] font-bold">
        Model: <span class="text-[#0B1E36]">{{ product.model }}</span>
      </p>
      <p class="text-[#CBA135] font-bold">
        Color: <span class="text-[#0B1E36]">{{ product.color }}</span>
      </p>

      <p class="text-lg text-[#0B1E36] font-semibold flex items-center gap-1">
        Price :
        <span class="text-[#CBA135]">${{ discountedPrice }}</span>
        <span
          v-if="product.discount"
          class="text-red-400 line-through text-sm ml-1"
        >
          ${{ product.price }}
        </span>
      </p>

      <div class="flex justify-evenly">
        <button
          class="bg-[#800020] border-[3px] border-[#800020] cursor-pointer transition-all text-[#F8F1E5] py-2 rounded-lg shadow hover:text-[#800020] font-semibold hover:bg-transparent hover:shadow-xl self-center w-32 text-center"
        >
          Add to Cart
        </button>

        <button
          class="bg-[#CBA135] border-[3px] border-[#CBA135] cursor-pointer transition-all text-[#F8F1E5] py-2 rounded-lg shadow hover:text-[#CBA135] font-semibold hover:bg-transparent hover:shadow-xl self-center w-32 text-center"
        >
          Add to Cart
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  computed: {
    discountedPrice() {
      return this.product.discount
        ? (this.product.price * (1 - this.product.discount / 100)).toFixed(2)
        : this.product.price;
    },
  },
};
</script>
