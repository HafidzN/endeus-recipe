<template>
  <div class="search leading-[1.15] box-border block relative mt-1.5 mb-[5px] mx-0">
    <div class="search__container leading-[1.15] box-border flex items-center bg-[#f0f4fb] border cursor-text h-12 px-4 py-0 rounded-lg border-solid border-white">
      <svg width="24" height="24" viewBox="0 0 24 24" class="Icon_iconJMUCM Icon_icon--grey40_fJsxJ">
        <path d="M4.4 10.45a6.057 6.057 0 0 1 6.05-6.05 6.057 6.057 0 0 1 6.05 6.05 6.03 6.03 0 0 1-1.768 4.27c-.002.001-.005.001-.008.004-.003.002-.003.006-.006.008A6.026 6.026 0 0 1 10.45 16.5a6.057 6.057 0 0 1-6.05-6.05m17.045 10.005l-5.258-5.258A7.418 7.418 0 0 0 17.9 10.45C17.9 6.342 14.558 3 10.45 3 6.341 3 3 6.342 3 10.45c0 4.108 3.341 7.45 7.45 7.45a7.416 7.416 0 0 0 4.747-1.713l5.258 5.258a.697.697 0 0 0 .99 0 .7.7 0 0 0 0-.99" fill="currentColor" fill-rule="evenodd"></path></svg>
        <input class="search__input outline-none box-border leading-[1.15] overflow-visible -outline-offset-2 text-base text-[#323e48] w-full ml-4 m-0 pr-2 border-[none]" type="search" :placeholder="placeholder" v-model="searchValue">
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'SearchComponent',
  props: {
    placeholder: String,
  },
  setup() {
    const searchValue = ref('');

    return {
      searchValue,
    };
  },
};
</script>

<style scoped lang="sass">
.search
  &__container
    svg
      line-height: 1.15
      -webkit-text-size-adjust: 100%
      font-family: 'Rubik', Arial
      cursor: text
      width: 24
      height: 24
      box-sizing: border-box
      fill: currentColor
      display: block
      color: #7d8ca3
    
    input
      background: transparent
</style>
