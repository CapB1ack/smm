<template>
  <q-layout>
    <header class="header">
      <div class="header-top" :class="{'header-top-hidden': scrolled}">
        <div class="row justify-around items-center full">
          <div>123123123</div>
          <div>123123123</div>
        </div>
      </div>
      <div class="header-fixed" :class="{'header-fixed-hidden': scrolled}"></div>
    </header>
    <div v-for="x in 5" style="height: 100vh"></div>
  </q-layout>
</template>
<script>
  import {QLayout} from 'quasar'

  export default {
    components: {
      QLayout
    },
    data () {
      return {
        scrolled: false
      }
    },
    created () {
      window.addEventListener('scroll', this.handleScroll)
    },
    methods: {
      handleScroll() {
        this.scrolled = window.scrollY > 0;
      }
    }
  }
</script>
<style lang="stylus">
  .header
    width: 100vw
    position fixed
    &-top
      height: 3rem
      background-color #fff
      transition all .1s ease
      &-hidden
        transform translateY(-100%)
    &-fixed
      height: 7rem;
      background-color #2a353c
      transition all .1s ease
      &-hidden
        transform translateY(-3rem)
  .full
    height 100%
    width 100%
</style>
