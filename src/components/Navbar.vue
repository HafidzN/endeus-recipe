<template>
    <nav class="navbar">
        <div class="navbar-left">
        <button class="arrow-button" @click="goBack">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
            <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 19.5L3 12m0 0l7.5-7.5M3 12h18" />
            </svg>
        </button>
        </div>
        <div class="navbar-right">
        <button
            class="bookmark-button"
            @click="toggleBookmark"
        >
            <svg v-if="isBookmarked" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6">
            <path fill-rule="evenodd" d="M6.32 2.577a49.255 49.255 0 0111.36 0c1.497.174 2.57 1.46 2.57 2.93V21a.75.75 0 01-1.085.67L12 18.089l-7.165 3.583A.75.75 0 013.75 21V5.507c0-1.47 1.073-2.756 2.57-2.93z" clip-rule="evenodd" />
            </svg>

            <svg v-else xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
            <path stroke-linecap="round" stroke-linejoin="round" d="M17.593 3.322c1.1.128 1.907 1.077 1.907 2.185V21L12 17.25 4.5 21V5.507c0-1.108.806-2.057 1.907-2.185a48.507 48.507 0 0111.186 0z" />
            </svg>
        </button>
        <button class="share-button" @click="emitClickShareEvent">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
            <path stroke-linecap="round" stroke-linejoin="round" d="M7.217 10.907a2.25 2.25 0 100 2.186m0-2.186c.18.324.283.696.283 1.093s-.103.77-.283 1.093m0-2.186l9.566-5.314m-9.566 7.5l9.566 5.314m0 0a2.25 2.25 0 103.935 2.186 2.25 2.25 0 00-3.935-2.186zm0-12.814a2.25 2.25 0 103.933-2.185 2.25 2.25 0 00-3.933 2.185z" />
            </svg>
        </button>
        </div>
    </nav>
</template>

<script>

import { useRouter } from 'vue-router'
import { ref } from 'vue'
export default {
  name: 'NavigationBar',
  setup(props, { emit }) {
    const isBookmarked = ref(false)
    const router = useRouter()
    const goBack = () => {
        router.go(-1)
    }

    const toggleBookmark = () => {
        isBookmarked.value = !isBookmarked.value
        emitClickBookmarkEvent()
        console.log(isBookmarked.value)
    }

    const emitClickBookmarkEvent = () => {
         emit("on-click-bookmark", true)
    }

    const emitClickShareEvent = () => {
        emit("on-click-share", true)
    }

    return {
        goBack,
      emitClickBookmarkEvent,
      emitClickShareEvent,
      toggleBookmark,
      isBookmarked
    }
  }
};
</script>

<style scoped>
.nav__container {
  max-width: 1200px;
  margin: 0 auto;
}
.navbar {
  z-index: 999;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 70px;
  background-color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.navbar-left {
  display: flex;
  align-items: center;
}

.arrow-button {
  background: none;
  border: none;
  padding: 0;
  margin-right: 10px;
  cursor: pointer;
}

.navbar-right {
  display: flex;
  align-items: center;
}

.bookmark-button,
.share-button {
  background: none;
  border: none;
  padding: 0;
  margin-left: 10px;
  cursor: pointer;
}

.bookmark-button-active {
  background-color: black;
  /* Add any additional styles you want for the active bookmark button */
}
</style>