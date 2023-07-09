<template>
  <div class="category-item leading-[1.15] box-border flex-[0_0_100px] mt-5 mb-0 mx-2">
    <router-link class="leading-[1.15] box-border bg-transparent no-underline text-[#222]"
       :to="'/kategory' + categoryLink"
       >
      <div class="leading-[1.15] text-[#222] box-border shadow-[0_1px_15px_0_rgba(0,0,0,0.06)] bg-white relative overflow-hidden pb-[100%] rounded-[13px]">
        <div class="leading-[1.15] text-[#222] box-border">
          <figure class="leading-[1.15] text-[#222] box-border relative m-0">
            <picture class="leading-[1.15] text-[#222] box-border absolute block w-full h-full left-0 top-0">
              <img :src="imageUrl" class="leading-[1.15] text-[#222] aspect-[auto_200_/_200] box-border h-auto w-full border-none" :alt="imageAlt" :width="imageWidth" :height="imageHeight">
            </picture>
            <figcaption class="leading-[1.15] text-[#222] box-border absolute invisible">{{ categoryTitle }}</figcaption>
          </figure>
        </div>
      </div>
      <p class="leading-[1.15] box-border text-center text-[#5d687b] text-sm mt-4 m-0">{{ categoryTitle }}</p>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CategoryComponent',
  props: {
    categoryTitle: {
      type: String,
      required: true,
    },
    containerTitle: {
      type: String,
      required: true,
    },
    categoryLink: {
      type: String,
      required: true,
    },
    imageUrl: {
      type: String,
      required: true,
    },
    imageAlt: {
      type: String,
      required: true,
    },
    imageWidth: {
      type: Number,
      default: 100
    },
    imageHeight: {
      type: Number,
      default: 100
    },
  },
};
</script>