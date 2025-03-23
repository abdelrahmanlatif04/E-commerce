<template>
  <div
    class="min-h-screen bg-dark-navy text-ivory-white flex justify-center items-center p-6"
  >
    <div
      class="w-full max-w-2xl bg-ivory-white text-dark-navy p-6 rounded-2xl shadow-lg"
    >
      <h2 class="text-xl font-semibold border-b pb-3 border-gold">
        Shopping Cart
      </h2>

      <div v-if="cart.length" class="mt-4 space-y-4">
        <div
          v-for="(item, index) in cart"
          :key="index"
          class="flex items-center gap-4 p-4 bg-white rounded-lg shadow relative aspect-[6.5]"
        >
          <img
            :src="item.image"
            :alt="item.name"
            class="w-16 h-16 object-cover rounded-lg"
          />

          <h3 class="text-sm flex-1 font-medium truncate">{{ item.title }}</h3>
          <p
            class="text-sm absolute bottom-0 left-0 bg-burgundy text-white p-1.5 rounded-tr-lg"
          >
            {{ (item.price * ((100 - item.discount) / 100)).toFixed(0) }} E£
          </p>

          <span
            class="absolute left-0 top-0 px-1.5 rounded-br-lg bg-gold text-white"
          >
            {{ item.id / NUMBER }}
          </span>
          <div class="flex flex-col gap-1.5">
            <button
              @click="removeItem(index)"
              class="px-3 py-1 bg-burgundy text-white rounded-md cursor-pointer transition-all duration-300 hover:opacity-85"
            >
              Remove
            </button>

            <button
              @click="useRouter().push(`/product/${item.id}`)"
              class="px-3 py-1 bg-gold text-white rounded-md cursor-pointer transition-all duration-300 hover:opacity-85"
            >
              See product
            </button>
          </div>
        </div>

        <div class="text-lg font-semibold border-t pt-3 border-gold">
          Total: {{ (totalPrice / NUMBER).toFixed(0) }} E£
        </div>

        <button
          class="w-2/3 mx-auto relative left-1/2 -translate-x-1/2 bg-[#cba135] text-white py-2 rounded-md font-medium hover:bg-[#800020] transition-all self-center cursor-pointer"
          @click="location.reload()"
        >
          Proceed to Checkout
        </button>
      </div>

      <p v-else class="text-center text-gray-500 mt-6">Your cart is empty.</p>
    </div>
  </div>
</template>

<script setup>
const totalPrice = ref(0);
const cart = ref([]);
const quantity = ref((Math.random() * 2 + 1).toFixed(0));
const NUMBER = 10;

const fetchCartItems = async () => {
  try {
    const response = await fetch("https://fakestoreapi.in/api/products");
    const data = await response.json();
    cart.value = data.products.filter((e) => !(e.id % NUMBER));

    totalPrice.value = cart.value.reduce(
      (total, item) =>
        total + item.id * item.price * ((100 - item.discount) / 100),
      0
    );
  } catch (error) {
    console.error("Error fetching cart items:", error);
  }
};
onMounted(fetchCartItems);
const removeItem = (index) => {
  if (cart.value) {
    cart.value.splice(index, 1);
  }

  totalPrice.value = cart.value.reduce(
    (total, item) =>
      total + item.id * item.price * ((100 - item.discount) / 100),
    0
  );
};
</script>

<style scoped>
.bg-dark-navy {
  background-color: #0b1e36;
}
.bg-gold {
  background-color: #cba135;
}
.bg-burgundy {
  background-color: #800020;
}
.bg-ivory-white {
  background-color: #f8f1e5;
}
.text-dark-navy {
  color: #0b1e36;
}
.text-ivory-white {
  color: #f8f1e5;
}
.border-gold {
  border-color: #cba135;
}
</style>
