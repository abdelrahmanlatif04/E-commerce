<template>
  <div
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
  </div>
</template>

<script setup>
let user = ref(null);

fetch("https://fakestoreapi.in/api/users/1")
  .then((res) => res.json())
  .then((res) => (user.value = res.user));
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
