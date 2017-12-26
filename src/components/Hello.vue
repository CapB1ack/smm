<template>
  <q-layout>
    <div class="background">
      <img :src='bgPics[bgPicsIndex]' alt="">
    </div>
    <div class="f1"></div>
    <div class="f2"></div>
    <div class="f3"></div>
    <div class="f4"></div>
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
        bgPics: [
          'https://hsto.org/files/39e/0b3/fa8/39e0b3fa81974ba59b1482a3e38b802f.png',
          'http://adapto.rs/arc/site/data/uploads/newsimg/github-logo.jpg'
        ],
        bgPicsIndex: 0
      }
    },
    created () {
      window.addEventListener('wheel', this.handleWheel)
    },
    methods: {
      handleWheel (e) {
        console.log(window.screen.height, window.pageYOffset)
        if (window.screen.height < window.pageYOffset && this.bgPicsIndex === 0) {
          this.bgPicsIndex = 1
        }
        else if (window.screen.height > window.pageYOffset && this.bgPicsIndex !== 0) {
          this.bgPicsIndex = 0
        }
      }
    }
  }
</script>
<style lang="stylus">
  .background
    position fixed
    z-index -1
    width 100vw
    height 100vh
    img
      width 100%
      height 100%
  .f1
    height 100vh
    background-color rgba(1, 255, 47, 0.2)
  .f2
    height 100vh
    background-color rgba(173, 255, 47, 0.2)
  .f3
    height 100vh
    background-color pink
  .f4
    height 100vh
    background-color teal
</style>
