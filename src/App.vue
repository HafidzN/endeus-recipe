<template>
  <Header />
  <router-view/>
</template>

<script>
import Header from '@/components/Header.vue';

export default {
  name: 'MainApp',
  components: {
    Header,
  },
};
</script>

<style lang="scss" scoped>
body {
  font-family: 'Rubik', Arial;
}
</style>
