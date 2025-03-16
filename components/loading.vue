<template>
  <div class="flex justify-center items-center grow">
    <div
      v-if="isLoading"
      class="animate-spin rounded-full h-20 aspect-square border-t-4 border-r-4 border-[#0B1E36]"
    ></div>

    <!-- <div v-else>Poor internet connection</div> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      isLoading: true,
    };
  },
  mounted() {
    // setTimeout(() => {
    //   this.isLoading = false;
    // }, 5000);
  },
};
</script>
