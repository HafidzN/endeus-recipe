<template>
 <div class="recipe">
    <router-link :to="'/resep/' + id" class="leading-[1.15] text-left box-border bg-transparent no-underline text-[#222]">
        <div class="leading-[1.15] text-left text-[#222] box-border bg-[#d2dce6] relative cursor-pointer overflow-hidden pb-[100%] rounded-lg">
            <div class="leading-[1.15] text-left text-[#222] cursor-pointer box-border">
                <figure class="leading-[1.15] text-left text-[#222] cursor-pointer box-border relative m-0">
                    <picture class="leading-[1.15] text-left text-[#222] cursor-pointer box-border absolute block w-full h-full left-0 top-0">
                        <img :src="imgSrc" class="leading-[1.15] text-left text-[#222] cursor-pointer aspect-[auto_380_/_380] box-border h-auto w-full border-none" :alt="title" width="380" height="380">
                    </picture>
                    <figcaption class="leading-[1.15] text-left text-[#222] cursor-pointer box-border absolute invisible">{{title}}</figcaption>
                </figure>
            </div>
            <svg v-if="hasVideo" width="34" height="34" viewBox="0 0 24 24" fill="none" class="leading-[1.15] text-left cursor-pointer w-[34] h-[34] box-border absolute fill-current block text-[#5d687b] m-auto right-2 top-2"><g filter="url(#filter0_d)"><circle cx="12" cy="12" r="9" fill="#fff"></circle></g><path fill-rule="evenodd" clip-rule="evenodd" d="M15.412 11.172a1 1 0 010 1.782l-4.959 2.522A1 1 0 019 14.585V9.54a1 1 0 011.453-.891l4.959 2.522z" fill="#000"></path><defs><filter id="filter0_d" x="2" y="3" width="20" height="20" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB"><feFlood flood-opacity="0" result="BackgroundImageFix"></feFlood><feColorMatrix in="SourceAlpha" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0"></feColorMatrix><feOffset dy="1"></feOffset><feGaussianBlur stdDeviation="0.5"></feGaussianBlur><feColorMatrix values="0 0 0 0 0.309804 0 0 0 0 0.309804 0 0 0 0 0.309804 0 0 0 0.15 0"></feColorMatrix><feBlend in2="BackgroundImageFix" result="effect1_dropShadow"></feBlend><feBlend in="SourceGraphic" in2="effect1_dropShadow" result="shape"></feBlend></filter></defs></svg>
        </div>
    </router-link>

    <div class="recipe__info leading-[1.15] text-left box-border relative mt-2 pr-8">
        <div class="leading-[1.15] text-left box-border absolute cursor-pointer right-0 top-0">
            <svg width="24" height="24" viewBox="0 0 24 24" class="leading-[1.15] text-left w-[24] h-[24] box-border cursor-pointer fill-current block text-[#7d8ca3]">
                <path stroke="currentColor" fill="transparent" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round" d="M19.611 22l-6.946-6.436a.9.9 0 0 0-1.22 0L4.5 22V2.75c0-.484.397-.875.889-.875h13.333c.492 0 .89.391.89.875V22z"></path>
            </svg>
        </div>
        <router-link class="leading-[1.15] text-left box-border bg-transparent no-underline text-[#222]" :to="'/resep/endeusiast-udah-tau-jenis-tempe-ini-belum'">
            <h3 class="text-left box-border font-medium text-base capitalize leading-5 text-[#231f20] overflow-hidden text-ellipsis m-0">{{title}}</h3>
        </router-link>
        <div class="leading-[1.15] text-left box-border flex items-center">
            <div class="leading-[1.15] text-left box-border flex items-center">
                <svg width="16" height="16" viewBox="0 0 16 16" fill="none" class="leading-[1.15] text-left w-[16] h-[16] box-border fill-current block text-[#7d8ca3]">
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M6.826 2.074c-.329.096-.627.193-.901.294a.467.467 0 11-.322-.876c.295-.109.613-.212.961-.314a.467.467 0 11.262.896zm-4.01 2.71c.251-.435.568-.83.957-1.183a.467.467 0 10-.626-.692c-.463.418-.84.891-1.14 1.409a.467.467 0 00.81.466zm-.643 3.895l-.021-.125-.018-.136a6.478 6.478 0 01-.022-1.269.467.467 0 10-.93-.074 7.403 7.403 0 00.025 1.454l.023.169.02.126.01.047a.467.467 0 00.913-.192zM8.241 1.628a.291.291 0 11-.582 0 .291.291 0 01.582 0z" fill="currentColor"></path>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M7.953 1.336v.583a6.011 6.011 0 015.988 6.005 6.012 6.012 0 01-6.005 6.005c-2.596 0-4.806-1.659-5.642-3.97l-.275.1-.273.1c.919 2.534 3.343 4.354 6.19 4.354a6.596 6.596 0 006.589-6.59 6.596 6.596 0 00-6.572-6.587z" fill="currentColor"></path>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M2.323 10.101a.291.291 0 11-.582 0 .291.291 0 01.582 0z" fill="currentColor"></path><path d="M7.883 2.695c.236 0 .431.176.462.404l.004.063v5.121L3.761 10.07a.467.467 0 01-.401-.84l.062-.03 3.993-1.554V3.162c0-.236.176-.432.404-.462l.064-.005z" fill="currentColor"></path>
                </svg>
                <span class="text-left box-border font-normal text-xs leading-4 text-[#7d8ca3] ml-1">{{duration}} menit</span>
            </div>
        </div>
    </div>
 </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'RecipeItem',
  components: {
  },
  props: {
    title: {
        type: String,
        default: ''
    },
    imgSrc: {
        type: String,
        default: ''
    },
    hasVideo: {
        type: Boolean,
        default: false
    },
    duration: {
        type: Number,
        default: 0
    },
    id: {
        type: Number,
        required: true
    }
  }
})
</script>

<style lang="sass" scoped>

</style>