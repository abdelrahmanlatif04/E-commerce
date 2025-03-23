<template>
  <div
    v-if="user"
    class="bg-dark-navy text-ivory-white flex flex-col gap-2 p-5 border-2 border-gold rounded-lg w-full mx-auto shadow-lg"
  >
    <img src="/avatar.jpeg" class="rounded-full border-4 w-42 aspect-square" />
    <h2 class="text-gold text-2xl mb-2">
      {{ user.name.firstname }} {{ user.name.lastname }}
    </h2>
    <p>Email: {{ user.email }}</p>
    <p>Username: {{ user.username }}</p>
    <p>Phone: {{ user.phone.slice(0, 12) }}</p>
    <p>
      Address: {{ user.address.number }} {{ user.address.street }},
      {{ user.address.city }}, {{ user.address.zipcode }}
    </p>
    <p>
      Coordinates: {{ user.address.geolocation.lat }},
      {{ user.address.geolocation.long }}
    </p>

    <div class="flex">
      <button
        class="mt-6 bg-[#800020] text-[#F8F1E5] px-6 py-3 text-lg font-medium rounded-lg self-start mx-10 transition duration-300 hover:bg-[#CBA135] hover:text-[#0B1E36] cursor-pointer"
        @click="useRouter().push('/cart')"
      >
        See Cart
      </button>
      <button
        class="mt-6 bg-[#cba135] text-[#0b1e36] px-6 py-3 text-lg font-medium rounded-lg self-start mx-10 transition duration-300 hover:bg-[#800020] hover:text-[#f8f1e5] cursor-pointer"
      >
        Purchase History
      </button>
    </div>
  </div>
  <loading v-else />
</template>

<script setup>
const user = ref(null);

onMounted(() => {
  fetch("https://fakestoreapi.com/users/1")
    .then((res) => res.json())
    .then((data) => {
      user.value = data;
    })
    .catch((error) => console.error("Error fetching user:", error));
});
</script>

<style scoped>
.bg-dark-navy {
  background-color: #0b1e36;
}
.text-gold {
  color: #cba135;
}
.text-ivory-white {
  color: #f8f1e5;
}
</style>
