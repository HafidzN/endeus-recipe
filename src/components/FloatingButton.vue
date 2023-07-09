<template>
  <div class="floating-button flex justify-center items-center">
    <button @click="$emit('on-main-clicked')" class="box-border inline-flex cursor-pointer relative text-base leading-5 justify-center items-center font-medium w-9 min-w-[160px] h-12 bg-[#ffcd00] mt-1.5 mb-[5px] mx-0 px-0 py-2 rounded-3xl border-[none]">
      {{ text }}
    </button>
    <button @click="$emit('on-lamp-clicked')" class="rounded-full w-10 h-10 bg-yellow-400 text-black flex items-center justify-center ml-2 shadow-md cursor-pointer">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
        <path stroke-linecap="round" stroke-linejoin="round" d="M12 18v-5.25m0 0a6.01 6.01 0 001.5-.189m-1.5.189a6.01 6.01 0 01-1.5-.189m3.75 7.478a12.06 12.06 0 01-4.5 0m3.75 2.383a14.406 14.406 0 01-3 0M14.25 18v-.192c0-.983.658-1.823 1.508-2.316a7.5 7.5 0 10-7.517 0c.85.493 1.509 1.333 1.509 2.316V18" />
        </svg>
    </button>
  </div>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      default: 'Mulai Masak, Yuk!'
    }
  },
};
</script>

<style scoped>
.floating-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 999;
  background-color: transparent;
}

.floating-button button {
  display: flex;
  align-items: center;
}

.floating-button button:first-child {
  margin-right: 8px;
}
</style>