<template>
  <div
    class="h-screen flex flex-col justify-center items-center bg-[#0B1E36] text-[#F8F1E5] text-center"
  >
    <h1 class="text-8xl font-bold text-[#800020]">404</h1>
    <p class="text-2xl my-4">
      Oops! The page you're looking for doesn't exist.
    </p>
    <NuxtLink
      to="/"
      class="mt-6 bg-[#800020] text-[#F8F1E5] px-6 py-3 text-lg font-medium rounded-lg transition duration-300 hover:bg-[#CBA135] hover:text-[#0B1E36] cursor-pointer"
    >
      Return to Home page</NuxtLink
    >
  </div>
</template>
