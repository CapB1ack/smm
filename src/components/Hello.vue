<template>
  <q-layout>
    <header class="header">
      <div class="header-top" :class="{'header-top-hidden': scrolled}">
        <div class="row justify-around items-center full">
          <div>8-(950)-111-11-11</div>
          <div>super@email.com</div>
        </div>
      </div>
      <div class="header-fixed row justify-around items-center" :class="{'header-fixed-hidden': scrolled}">
        <span style="font-size: 1rem; color: white">ссылка</span>
        <span style="font-size: 1rem; color: white">ссылка</span>
        <span style="font-size: 2rem; color: red; font-weight: bold">ЛОГО</span>
        <span style="font-size: 1rem; color: white">ссылка</span>
        <span style="font-size: 1rem; color: white">ссылка</span>
      </div>
    </header>
    <div style="height: 7rem"></div>
    <div class="column justify-center items-center">
      <h4>Очень умный текст, описывающий картинки ниже</h4>
      <q-gallery-carousel
        infinite
        autoplay
        dots
        handle-arrow-keys
        class="gall-size" :src="gallery"></q-gallery-carousel>
    </div>
    <div style="height: 100vh">
      <div class="col-12 row justify-center items-center">
        <div class="decore-heading">Что же, блин, такое SMM?? Да хз, вот видос</div>
      </div>
      <div class="row justify-around items-center">
        <div style="max-width: 20rem">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci at aut deleniti, dolorum esse harum non obcaecati odio, quisquam recusandae, saepe sed. Dolor dolores explicabo in molestias, quis repudiandae tempora.</div>
        <q-video
          src="https://www.youtube.com/embed/nMgWS45EWek?rel=0"
          style="width: 853px; height: 480px"
        />
        <div style="max-width: 20rem">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci aperiam, asperiores blanditiis cumque delectus dicta dolores earum, eos est ex ipsam laborum nesciunt nobis officia officiis optio quidem recusandae repudiandae. Lorem ipsum dolor sit amet, consectetur adipisicing elit. A, ad asperiores commodi consectetur deserunt dolorem impedit, laboriosam magni nemo nulla perferendis possimus quam quod reiciendis repellendus sunt veritatis voluptate voluptatem.</div>
      </div>

    </div>
    <div style="height: 120vh">
      <q-parallax :src="'http://4.bp.blogspot.com/-d68l8RLoLc4/UWAJF-ofbJI/AAAAAAAAST4/SUJbO2Dz-RI/s1600/cat1.jpg'" :height="1200">
        <div slot="loading">Загрузка...</div>
        <h1>Текстик едет перед картинкой</h1>
      </q-parallax>
    </div>

    <div style="height: 100vh;" class="row justify-center items-center">
      <div class="col-12 row justify-center items-center">
        <div class="decore-heading">Галерея котиков, где потом будут .. а что будет?</div>
      </div>
      <div class="my-gallery row justify-around items-center">
        <img :src="pic" alt="" v-for="pic in gallery">
      </div>
    </div>

    <div style="height: 20vh; background-color: #2a353c" class="row justify-around items-center">
      <img class="logo" :src="vkLogo" alt="">
      <img class="logo" :src="insLogo" alt="">
    </div>
  </q-layout>
</template>
<script>
  import {
    QLayout,
    QVideo,
    QGalleryCarousel,
    QGallery,
    QParallax
  } from 'quasar'
  import * as vkLogo from '../assets/vk_logo.svg'
  import * as insLogo from '../assets/ins_logo.svg'

  export default {
    components: {
      QLayout,
      QVideo,
      QGallery,
      QGalleryCarousel,
      QParallax
    },

    data () {
      return {
        scrolled: false,
        vkLogo: vkLogo,
        insLogo: insLogo,
        gallery: [
          'http://itd0.mycdn.me/image?id=813737148729&t=20&plc=WEB&tkn=*pyvVEVUtVw-rjl2xjhlLC43uwSM',
          'https://qna.center/storage/photos/ilux555/309850.jpg',
          'http://4.bp.blogspot.com/-d68l8RLoLc4/UWAJF-ofbJI/AAAAAAAAST4/SUJbO2Dz-RI/s1600/cat1.jpg',
          'http://oboi.cc/1600-1200-100-uploads/11_05_2013/view/201209/oboik.ru_3071.jpg'
        ]
      }
    },
    created () {
      window.addEventListener('scroll', this.handleScroll)
    },
    methods: {
      handleScroll () {
        this.scrolled = window.scrollY > 0
      }
    }
  }
</script>
<style lang="stylus">
  .header
    width: 100vw
    position fixed
    z-index 999
    &-top
      height: 2rem
      background-color #fff
      transition all .1s ease
      &-hidden
        transform translateY(-100%)
    &-fixed
      height: 5rem;
      background-color #2a353c
      transition all .1s ease
      &-hidden
        transform translateY(-2rem)
  .full
    height 100%
    width 100%
  .gall-size
    height 80vh
    width 90vw
  .decore-heading
    font-size: 3rem
    margin 7rem
    box-sizing border-box
    border-bottom 2px solid red
    border-top 2px solid red
  .my-gallery
    width 100vw
    img
      width 300px
      height 300px
      transition all .2s linear
      &:hover
        transform scale(1.3)
  .logo
    width 4rem
    height 4rem
    color white
</style>
