<template>
  <div class="wrapper">
    <user-from v-if="!showSuccessComponent" v-on:show="setState"/>
    <success-screen v-on:fire-click='setState' v-else />
  </div>
</template>

<script>
import UserFrom from './components/UserFrom.vue'
import SuccessScreen from './components/SuccessScreen.vue'

export default {
  name: 'App',
  components: {
    UserFrom,
    SuccessScreen
  },
  data() {
    return {
      showSuccessComponent: false
    }
  },
  methods: {
    setState() {
      this.showSuccessComponent = !this.showSuccessComponent
    }
  }
}
</script>

// <style lang="sass" scoped>
.wrapper 
  background-color: #FBAB7E
  background-image: linear-gradient(62deg, #FBAB7E 0%, #F7CE68 100%)
  display: flex
  justify-content: center
  align-items: center
  height: 100%
  width: 100%
</style>
