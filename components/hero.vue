<template>
  <section
    class="bg-[#0B1E36] grid place-content-center text-[#F8F1E5] text-center py-24 px-6 w-full aspect-[2.5]"
  >
    <div class="max-w-3xl">
      <h1 class="text-5xl font-bold font-montserrat text-[#CBA135]">
        Welcome to the World of Luxury
      </h1>
      <p class="text-lg font-poppins mt-4">
        Elegant design, unique experience, and a lasting impression.
      </p>
      <button
        class="mt-6 bg-[#800020] text-[#F8F1E5] px-6 py-3 text-lg font-medium rounded-lg transition duration-300 hover:bg-[#CBA135] hover:text-[#0B1E36] cursor-pointer"
        @click="useRouter().push('/category/general')"
      >
        Discover More
      </button>
    </div>
  </section>
</template>

<style></style>
