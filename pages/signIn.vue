<template>
  <div
    class="min-h-screen flex items-center justify-center bg-[#0B1E36] text-[#F8F1E5]"
  >
    <form
      class="bg-[#0B1E36] border border-[#CBA135] p-8 rounded-2xl shadow-lg w-full max-w-md space-y-6"
    >
      <h2 class="text-2xl font-bold text-center text-[#CBA135]">Sign In</h2>

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
          placeholder="Enter your password"
        />
      </div>

      <p>Already have an account ? <nuxt-link to="/register">Register now!!</nuxt-link></p>

      <button
        @click.prevent="signIn"
        class="w-full bg-[#CBA135] text-[#0B1E36] font-bold py-3 rounded-xl hover:bg-[#800020] hover:text-[#F8F1E5] transition"
      >
        Sign In
      </button>
    </form>
  </div>
</template>

<script setup>
const email = ref("");
const password = ref("");

const signIn = () => {
  console.log("Signing in with:", email.value, password.value);
};
</script>
