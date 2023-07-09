<template>
  <main class="recipe">
    <section class="recipe__container leading-[1.15] box-border mb-6 h-pt-70 pb-10">
        <Navbar 
            @on-click-bookmark="showToast('Bookmarked')"
            @on-click-share="showToast('Shared')"
        />
        <div class="leading-[1.15] box-border text-left text-[#323e48]">
            <h1 class="text-left box-border font-extrabold text-2xl leading-[30px] text-[#231f20] mt-4 mb-0 mx-0 my-[0.67em] px-4">{{recipe.title}}</h1>
            <div class="recipe__review leading-[1.15] text-left text-[#323e48] box-border mt-3 px-4">
                <div class="text-left text-[#323e48] box-border leading-[21px] inline-block align-middle">
                    <svg width="21" height="21" viewBox="0 0 24 24" fill="none" class="leading-[21px] w-[21] h-[21] box-border fill-current text-[#ffcd00] inline-block ml-0"><path d="M21.7415 11.119C22.1352 10.7185 22.2741 10.1308 22.1043 9.58445C21.9341 9.03812 21.4908 8.64812 20.9462 8.56535L16.1036 7.83091C15.8974 7.79956 15.7191 7.66454 15.627 7.46933L13.4621 2.88964C13.219 2.37507 12.7256 2.0553 12.1757 2.0553C11.6263 2.0553 11.1329 2.37507 10.8898 2.88964L8.72444 7.46975C8.63233 7.66496 8.45371 7.79998 8.24747 7.83133L3.40491 8.56577C2.86067 8.64812 2.41694 9.03854 2.24674 9.58487C2.07694 10.1312 2.2159 10.7189 2.60957 11.1194L6.11333 14.6841C6.26271 14.8363 6.33119 15.0553 6.29595 15.2694L5.46937 20.303C5.39608 20.7461 5.50741 21.1771 5.78214 21.5169C6.20905 22.0465 6.95433 22.2079 7.55024 21.881L11.881 19.5042C12.062 19.4051 12.2899 19.406 12.4705 19.5042L16.8016 21.881C17.0123 21.9968 17.237 22.0553 17.4688 22.0553C17.8921 22.0553 18.2934 21.8588 18.5693 21.5169C18.8445 21.1771 18.9554 20.7453 18.8821 20.303L18.0551 15.2694C18.0199 15.0549 18.0884 14.8363 18.2377 14.6841L21.7415 11.119Z" fill="currentColor"></path></svg>
                </div>
                <div class="text-left box-border text-lg text-[#323e48] font-medium leading-[21px] inline-block align-middle ml-2.5">
                    {{recipe.stars}}/{{recipe.total_review}}
                </div>
                <div class="text-left box-border inline-block align-middle text-[#7d8ca3] text-xs leading-[21px] ml-2">(3 rating)</div>
            </div>
            <div class="recipe__desc leading-[1.15] text-left text-[#323e48] box-border relative overflow-hidden max-h-[none] mt-4 pb-0 px-4">
                <p class="text-left text-[#323e48] box-border text-base leading-[26px] m-0">{{recipe.desc}}<br></p>
            </div>
            <div class="leading-[1.15] text-left text-[#323e48] box-border px-4">
                <div class="leading-[1.15] text-left text-[#323e48] box-border bg-[#d2dce6] rounded relative mt-4 pb-[100%]">
                    <video controls="" :poster="recipe.imgSrc" style="height:100%;position:absolute;top:0;left:0;width:100%" class="leading-[1.15] text-left text-[#323e48] box-border h-full absolute w-full left-0 top-0" :src="recipe?.videoUrl ?? ''"></video>
                    <!-- <div v-if="play" @click="setPlay" class="recipe__media leading-[1.15] text-left text-[#323e48] box-border absolute w-full h-full cursor-pointer">
                        <svg width="96" height="96" viewBox="0 0 24 24" fill="none" class="leading-[1.15] text-left cursor-pointer w-[96] h-[96] box-border absolute -translate-x-2/4 translate-y-[-65%] fill-current block text-[#5d687b] left-2/4 top-2/4"><g filter="url(#filter0_d)"><circle cx="12" cy="12" r="9" fill="#fff"></circle></g><path fill-rule="evenodd" clip-rule="evenodd" d="M15.412 11.172a1 1 0 010 1.782l-4.959 2.522A1 1 0 019 14.585V9.54a1 1 0 011.453-.891l4.959 2.522z" fill="#000"></path><defs><filter id="filter0_d" x="2" y="3" width="20" height="20" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB"><feFlood flood-opacity="0" result="BackgroundImageFix"></feFlood><feColorMatrix in="SourceAlpha" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0"></feColorMatrix><feOffset dy="1"></feOffset><feGaussianBlur stdDeviation="0.5"></feGaussianBlur><feColorMatrix values="0 0 0 0 0.309804 0 0 0 0 0.309804 0 0 0 0 0.309804 0 0 0 0.15 0"></feColorMatrix><feBlend in2="BackgroundImageFix" result="effect1_dropShadow"></feBlend><feBlend in="SourceGraphic" in2="effect1_dropShadow" result="shape"></feBlend></filter></defs></svg>
                    </div> -->
                </div>
            </div>
            <div class="recipe__tab leading-[1.15] text-left text-[#323e48] box-border flex flex-col mt-2">
                <div class="leading-[1.15] text-left text-[#323e48] box-border sticky w-full z-[101] bg-white px-4 top-[70px]">
                    <div class="leading-[1.15] text-left text-[#323e48] box-border flex overflow-auto pb-0.5 border-b-[#d8d8d8] border-b border-solid">
                        <div @click="changeTab('bahan')" :class="`box-border select-none cursor-pointer text-[#5d687b] text-base font-normal not-italic leading-5 tracking-[normal] text-center basis-full capitalize whitespace-nowrap pt-4 pb-3 px-2 ${tab === 'bahan' ?'tab-active'  : ''}`">bahan</div>
                        <div @click="changeTab('tutorial')" :class="`box-border select-none cursor-pointer text-[#5d687b] text-base font-normal not-italic leading-5 tracking-[normal] text-center basis-full capitalize whitespace-nowrap pt-4 pb-3 px-2 ${tab === 'tutorial' ?'tab-active'  : ''}`">cara membuat</div>
                    </div>
                </div>
            </div>
            <div class="recipe__steps">
                <div v-if="tab === 'bahan'" class="leading-[1.15] text-left text-[#323e48] box-border overflow-hidden opacity-100 h-auto visible h-transition-1">
                    <ul class="leading-[1.15] text-left text-[#323e48] visible box-border mt-6 m-0 p-0">
                        <li class="leading-[1.15] text-[#323e48] visible box-border flex list-none mb-1.5 px-4">
                            <h2 class="visible list-none box-border font-medium text-base capitalize leading-5 text-[#5d687b] m-0" style="list-style: none !important">bahan</h2>
                            <span class="leading-[1.15] text-[#323e48] visible list-none box-border mx-2">·</span>
                            <div class="visible list-none box-border text-sm leading-[18px] text-[#7d8ca3] inline-flex items-center" style="list-style: none !important">
                                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" class="visible list-none text-sm leading-[18px] w-[20] h-[20] box-border fill-current block text-[#7d8ca3]"><path fill-rule="evenodd" clip-rule="evenodd" d="M3.80006 15.1756C3.84081 10.5605 7.68902 6.84545 12.4169 6.84545C17.1445 6.84545 20.9926 10.5605 21.0333 15.1756L21.0396 15.8818H3.79382L3.80006 15.1756ZM19.5628 14.2639C19.0805 10.939 16.1928 8.36219 12.6588 8.24931L12.4169 8.24545C8.77316 8.24545 5.76387 10.8634 5.27059 14.2639L5.24203 14.481H19.59L19.5628 14.2639Z" fill="currentColor"></path><path fill-rule="evenodd" clip-rule="evenodd" d="M3.05576 15.3303H20.9443C21.882 15.3303 22.7 15.9878 22.7 16.8788C22.7 17.7698 21.882 18.4273 20.9443 18.4273H3.05576C2.11807 18.4273 1.30005 17.7698 1.30005 16.8788C1.30005 15.9878 2.11807 15.3303 3.05576 15.3303ZM20.9443 16.7303H3.05576C2.83221 16.7303 2.70005 16.8365 2.70005 16.8788C2.70005 16.9211 2.83221 17.0273 3.05576 17.0273H20.9443C21.1679 17.0273 21.3 16.9211 21.3 16.8788C21.3 16.8365 21.1679 16.7303 20.9443 16.7303Z" fill="currentColor"></path><path fill-rule="evenodd" clip-rule="evenodd" d="M10.4667 6.27273C10.4667 5.18599 11.3371 4.3 12.4172 4.3C13.4965 4.3 14.3667 5.18623 14.3667 6.27273C14.3667 7.35923 13.4965 8.24546 12.4172 8.24546C11.3371 8.24546 10.4667 7.35947 10.4667 6.27273ZM12.9667 6.27273C12.9667 5.95375 12.7175 5.7 12.4172 5.7C12.1159 5.7 11.8667 5.95368 11.8667 6.27273C11.8667 6.59178 12.1159 6.84546 12.4172 6.84546C12.7175 6.84546 12.9667 6.59171 12.9667 6.27273Z" fill="currentColor"></path></svg>
                                <span class="visible list-none text-sm leading-[18px] text-[#7d8ca3] box-border ml-1">{{recipe.porsi}} porsi</span>
                            </div>
                        </li>
                        <li class="recipe__list text-[#323e48] visible box-border text-[15px] leading-6 relative pl-[38px] pr-4 py-2.5 border-b border-solid border-[#f0f4fb]" style="list-style: none" v-for="material in recipe.bahan" :key="material"><span class="text-[#323e48] visible text-[15px] leading-6 box-border">{{material}}</span></li>
                        
                        <li class="leading-[1.15] text-[#323e48] visible box-border flex list-none mb-1.5 px-4">
                            <h2 class="visible list-none box-border font-medium text-base capitalize leading-5 text-[#5d687b] mt-8 m-0" style="list-style: none !important">bumbu, haluskan:</h2>
                        </li>
                        <li v-for="season in recipe.seasoning" :key="season" class="recipe__list text-[#323e48] visible box-border text-[15px] leading-6 relative pl-[38px] pr-4 py-2.5 border-b border-solid border-[#f0f4fb]" style="list-style: none"><span class="text-[#323e48] visible text-[15px] leading-6 box-border">{{season}}</span></li>
                    </ul>
                </div>

                <div v-if="tab === 'tutorial'" class="leading-[1.15] text-left text-[#323e48] box-border overflow-hidden opacity-100 h-auto visible h-transition-1">
                  <div class="leading-[1.15] text-left text-[#323e48] visible box-border mt-6 px-4">
                    <div class="leading-[1.15] text-left text-[#323e48] visible box-border flex">
                        <h2 class="text-left visible box-border font-medium text-base leading-5 text-[#5d687b] m-0">Cara Membuat</h2>
                        <span class="leading-[1.15] text-left text-[#323e48] visible box-border mx-2">·</span>
                        <div class="text-left visible box-border text-sm leading-[18px] text-[#7d8ca3] inline-flex">
                            <svg width="18" height="18" viewBox="0 0 16 16" fill="none" class="text-left visible text-sm leading-[18px] w-[18] h-[18] box-border fill-current block text-[#7d8ca3]">
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M6.826 2.074c-.329.096-.627.193-.901.294a.467.467 0 11-.322-.876c.295-.109.613-.212.961-.314a.467.467 0 11.262.896zm-4.01 2.71c.251-.435.568-.83.957-1.183a.467.467 0 10-.626-.692c-.463.418-.84.891-1.14 1.409a.467.467 0 00.81.466zm-.643 3.895l-.021-.125-.018-.136a6.478 6.478 0 01-.022-1.269.467.467 0 10-.93-.074 7.403 7.403 0 00.025 1.454l.023.169.02.126.01.047a.467.467 0 00.913-.192zM8.241 1.628a.291.291 0 11-.582 0 .291.291 0 01.582 0z" fill="currentColor"></path>
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M7.953 1.336v.583a6.011 6.011 0 015.988 6.005 6.012 6.012 0 01-6.005 6.005c-2.596 0-4.806-1.659-5.642-3.97l-.275.1-.273.1c.919 2.534 3.343 4.354 6.19 4.354a6.596 6.596 0 006.589-6.59 6.596 6.596 0 00-6.572-6.587z" fill="currentColor"></path>
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M2.323 10.101a.291.291 0 11-.582 0 .291.291 0 01.582 0z" fill="currentColor"></path>
                                <path d="M7.883 2.695c.236 0 .431.176.462.404l.004.063v5.121L3.761 10.07a.467.467 0 01-.401-.84l.062-.03 3.993-1.554V3.162c0-.236.176-.432.404-.462l.064-.005z" fill="currentColor"></path>
                            </svg>
                            <span class="ml-2">{{recipe.duration}} menit</span>
                        </div>
                    </div>
                    <ol class="leading-[1.15] text-left text-[#323e48] visible box-border mt-4 m-0 p-0">
                        <li v-for="tutorial in recipe.tutorial" :key="tutorial" class="recipe__list-2 text-[#323e48] visible box-border text-base leading-[26px] relative">
                            <p class="text-[#323e48] visible text-base leading-[26px] box-border relative pl-[30px]">{{tutorial}}</p>
                        </li>
                    </ol>
                 </div>
                </div>                
            </div>
        </div>
    </section>
    <FloatingButton @on-main-clicked="showToast('Mulai Masak, Yuk!')" @on-lamp-clicked="toggleModal"/>
    <Toast v-if="showToastNotification" :message="toastMessage" :show="showToastNotification" />
    <Modal :is-open="isModalOpen" @update:is-open="handleModalUpdate">
        <template #title>
            Tips
        </template>
        <p>This is the modal content.</p>
    </Modal>
  </main>  
</template>

<script>
import Navbar from '@/components/Navbar.vue'
import FloatingButton from '@/components/FloatingButton.vue'
import Toast from '@/components/Toast.vue'
import Modal from '@/components/Modal.vue'
import { ref, computed } from 'vue'
import { useStore } from 'vuex'
import { useRoute } from 'vue-router'

export default {
    components: {
        Navbar,
        FloatingButton,
        Toast,
        Modal
    },
    setup () {
        const tab = ref('bahan')
        const play = ref(true)
        const showToastNotification = ref(false)
        const toastMessage = ref('')

        const changeTab = (mode) => {
            tab.value = mode
        }
        const setPlay = () => {
            play.value = false
        }

        const showToast = (message = '') => {
            showToastNotification.value = true;
            toastMessage.value = message;
            setTimeout(() => {
                showToastNotification.value = false;
            }, 2000);
        };
        
        const isModalOpen = ref(false)
        const toggleModal = () => {
            isModalOpen.value = !isModalOpen.value
        }
        const handleModalUpdate = (newValue) => {
            isModalOpen.value = newValue
        }

        const store = useStore()
        const route = useRoute()
        const idParam = route.params.id

        const recipe = computed(() => store.getters['recipes/getRecipeById'](+idParam));
        console.log(recipe.value)
       

        return {
            tab,
            play,
            changeTab,
            setPlay,
            showToast,
            showToastNotification,
            toastMessage,
            isModalOpen,
            toggleModal,
            handleModalUpdate,
            recipe
        }
    }
}
</script>

<style lang="scss" scoped>
.recipe{
    &__container {
      max-width: 1200px;
      margin: 0 auto;
      justify-content: space-between;
    }
    &__list {
        ::before {
            content: "";
            background-color: #d2dce6;
            height: 6px;
            width: 6px;
            margin: 9px 0;
            position: absolute;
            top: 10px;
            left: 16px;
            border-radius: 50%;
        }
    }
    &__list-2 {
        ::before{
            content: "*"; //counter(inst);
            color: #231f20;
            background-color: #f0f4fb;
            font-size: 14px;
            font-weight: 700;
            text-align: center;
            position: absolute;
            top: 0;
            left: 0;
            margin-top: 1.5px;
            width: 22px;
            height: 20px;
            line-height: 21px;
            z-index: -1;
        }
    }
}

.h-pt-70 {
    padding-top: 70px
}

.h-transition-1 {
    transition: height 0ms 0.4s, opacity 0.4s 0ms
}

.tab-active {
    color: #ff8d6b;
    box-shadow: 0 4px 0 -1px #ff8d6b;
    font-weight: 500
}
</style>