<template>
  <div id="app">
  </div>
</template>

<script>
import bModal from 'bootstrap-vue/es/components/modal/modal'

export default {
  name: 'app',
  data () {
    return {
      themeColors: ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'light', 'dark'],
      modalShow: false
    }
  },
  components: {
    'b-modal': bModal
  }
}
</script>

<style lang="scss">
@import './assets/styles/variables';
@import './assets/styles/bootstrap';
</style>
