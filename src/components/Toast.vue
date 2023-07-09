<template>
  <transition name="toast-fade">
    <div v-if="show" class="toast-notification">
      <div class="toast-message">
        {{ message }}
      </div>
      <!-- <button class="toast-close" @click="closeToast">
        Close
      </button> -->
    </div>
  </transition>
</template>

<script>
import { ref, watch, onMounted } from 'vue';

export default {
  name: 'ToastNotification',
  props: {
    message: {
      type: String,
      default: ''
    },
    show: {
      type: Boolean,
      default: false
    }
  },
  setup(props) {
    const showToast = ref(false);

    watch(() => {
      showToast.value = props.show;
    });

    const closeToast = () => {
      showToast.value = false;
    };

    onMounted(() => {
      if (showToast.value) {
        setTimeout(() => {
          showToast.value = false;
        }, 2500);
      }
    });

    return {
      showToast,
      closeToast
    };
  }
};
</script>

<style scoped>
.toast-notification {
  position: fixed;
  top: 90px;
  left: 50%;
  transform: translateX(-50%);
  background-color: rgba(0, 0, 0, 0.8);
  color: #fff;
  padding: 10px 20px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  z-index: 999;
}

.toast-message {
  flex-grow: 1;
}

.toast-close {
  background-color: transparent;
  border: none;
  color: #fff;
  cursor: pointer;
}
</style>