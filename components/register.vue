<template>
  <div
    class="min-h-screen flex items-center justify-center bg-[#0B1E36] text-[#F8F1E5]"
  >
    <form
      class="bg-[#0B1E36] border border-[#CBA135] p-8 rounded-2xl shadow-lg w-full max-w-md space-y-6"
    >
      <h2 class="text-2xl font-bold text-center text-[#CBA135]">Register</h2>

      <div>
        <label for="name" class="block mb-2">Full Name</label>
        <input
          v-model="name"
          type="text"
          id="name"
          class="w-full p-3 rounded-xl bg-[#F8F1E5] text-[#0B1E36] placeholder:text-[#800020] focus:outline-none"
          placeholder="Your full name"
        />
      </div>

      <div>
        <label for="email" class="block mb-2">Email</label>
        <input
          v-model="email"
          type="email"
          id="email"
          class="w-full p-3 rounded-xl bg-[#F8F1E5] text-[#0B1E36] placeholder:text-[#800020] focus:outline-none"
          placeholder="Enter your email"
        />
      </div>

      <div>
        <label for="password" class="block mb-2">Password</label>
        <input
          v-model="password"
          type="password"
          id="password"
          class="w-full p-3 rounded-xl bg-[#F8F1E5] text-[#0B1E36] placeholder:text-[#800020] focus:outline-none"
          placeholder="Create a password"
        />
      </div>

      <button
        @click.prevent="register"
        class="w-full bg-[#CBA135] text-[#0B1E36] font-bold py-3 rounded-xl hover:bg-[#800020] hover:text-[#F8F1E5] transition"
      >
        Register
      </button>
    </form>
  </div>
</template>

<script setup>
const name = ref("");
const email = ref("");
const password = ref("");

const register = () => {
  console.log("Registering:", name.value, email.value, password.value);
};
</script>
