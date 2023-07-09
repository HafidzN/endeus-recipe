<template>
  <header class="header shadow-md w-full fixed z-10 bg-white">
    <div class="header__container leading-[1.15] box-border flex w-full h-[70px] items-center relative px-4 py-0">
        <router-link :to="'/'" class="header__main-logo leading-[1.15] box-border bg-transparent block relative w-[165px] h-[60px] no-underline text-[#222] mr-4 mt-1.5 mb-[5px] mx-0" href="/">
          <picture class="header__picture leading-[1.15] text-[#222] box-border">
              <source media="(min-width:800px)" :srcset="require('@/assets/images/endeus_logo.svg')" class="leading-[1.15] text-[#222] box-border">
              <img class="leading-[1.15] text-[#222] box-border block w-[165px] h-[60px] border-none" :src="require('@/assets/images/endeus_logo-m.svg')" alt="Endeus TV Logo" width="36" height="36">
          </picture>
        </router-link>
        <Search class="flex-shrink-0 ml-auto flex-1" :placeholder="'Cari resep endeus'"/>
        <span class="ml-2">
        <svg class="w-6 h-6 text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 16 21">
            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 3.464V1.1m0 2.365a5.338 5.338 0 0 1 5.133 5.368v1.8c0 2.386 1.867 2.982 1.867 4.175C15 15.4 15 16 14.462 16H1.538C1 16 1 15.4 1 14.807c0-1.193 1.867-1.789 1.867-4.175v-1.8A5.338 5.338 0 0 1 8 3.464ZM4.54 16a3.48 3.48 0 0 0 6.92 0H4.54Z"/>
        </svg>
        </span>
    </div>
  </header>
</template>

<script>
import { defineComponent } from 'vue'
import Search from './Search.vue'

export default defineComponent({
  name: 'HeaderComponent',
  components: {
    Search,
  },
});
</script>

<style lang="scss" scoped>
.header__container {
    max-width: 1200px;
    margin: 0 auto;
    justify-content: space-between;
}

@media (max-width: 767px) {
  .header__main-logo {
    display: none;
  }
}
</style>