<template>
  <div class="home no-padding-top">
    <Loading :loading="load" />
    <SideNavigation v-if="isSide" />
    <Navigation v-if="!isMobile" />
    <MClose v-else />
    <!-- <Indigator :viewIndex="viewIndex" /> -->
    <!-- <full-page
      ref="fullPage"
      :options="options"
      id="fullpage"
    > -->
    <!-- <vue-lazy-component class="section" id="sectionDe" @init="init">
      <SwiperDemo />
    </vue-lazy-component> -->
    <vue-lazy-component class="section" id="section1" @init="init">
      <S1 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section2" @init="init">
      <!-- PC -->
      <img v-if="!isMobile" :style="pcTop1" class="wave wave_l1 waveAni" src="../projects/hpym/all/wave_l1.png" />
      <S2 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section0" @init="init">
      <S0 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section3" @init="init">
      <!-- PC -->
      <img v-if="!isMobile" class="wave wave_r1 waveAni" :style="pcTop2" src="../projects/hpym/all/wave_r1.png" />
      <!-- MB -->
      <img v-if="isMobile" class="wave wave_l1 waveAni" :style="mbTop1" src="../projects/hpym/all/wave_l1.png" />
      <img v-if="isMobile" class="wave wave_r1 waveAni" :style="mbTop2" src="../projects/hpym/all/wave_r1.png" />
      <S3 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section4" @init="init">
      <S4 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section5" @init="init">
      <!-- PC -->
      <img v-if="!isMobile" :style="pcTop3" class="wave wave_l2 waveAni" src="../projects/hpym/all/wave_l2.png" />
      <img v-if="!isMobile" :style="pcTop4" class="wave wave_r2 waveAni" src="../projects/hpym/all/wave_r2.png" />
      <!-- MB -->
      <img v-if="isMobile" class="wave wave_l2 waveAni" :style="mbTop3" src="../projects/hpym/all/wave_l2.png" />
      <S5 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section6" @init="init">
      <!-- MB -->
      <img v-if="isMobile" class="wave wave_r1 waveAni" :style="mbTop4" src="../projects/hpym/all/wave_r1.png" />
      <S6 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section7" @init="init">
      <!-- MB -->
      <img v-if="isMobile" class="wave wave_l2 waveAni" :style="mbTop5" src="../projects/hpym/all/wave_l1.png" />
      <img v-if="isMobile" class="wave wave_r2 waveAni" :style="mbTop6" src="../projects/hpym/all/wave_r1.png" />
      <S7 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section8" @init="init">
      <S8 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="contact">
      <ContactSection />
    </vue-lazy-component>
    <!-- ======================== -->
    <MobileNav />
  </div>
</template>

<script>
// @ is an alias to /src
import $ from 'jquery'
import Navigation from '@/layouts/Navigation.vue'
import { isMobile } from '@/utils'
import SideNavigation from '@/layouts/SideNavigation.vue'
import ContactSection from '@/layouts/ContactSection.vue'
import MobileNav from '@/layouts/MobileNav.vue'
import Loading from '@/components/Loading.vue'
// import Indigator from '@/components/Indigator.vue'
// import SwiperDemo from '@/projects/hpym/swiperDemo_S7_single.vue'
import MClose from '@/projects/hpym/MClose.vue'
import S0 from '@/projects/hpym/S0.vue'
import S1 from '@/projects/hpym/S1.vue'
import S2 from '@/projects/hpym/S2.vue'
import S3 from '@/projects/hpym/S3.vue'
import S4 from '@/projects/hpym/S4.vue'
import S5 from '@/projects/hpym/S5.vue'
import S6 from '@/projects/hpym/S6.vue'
import S7 from '@/projects/hpym/S7.vue'
import S8 from '@/projects/hpym/S8.vue'

export default {
  name: 'home',
  components: {
    Loading,
    // Indigator,
    Navigation,
    SideNavigation,
    ContactSection,
    MobileNav,
    // SwiperDemo,
    MClose,
    S0,
    S1,
    S2,
    S3,
    S4,
    S5,
    S6,
    S7,
    S8,
  },

  data() {
    return {
      isMobile,
      isSide: false,
      load: true,
      pcTop1: '',
      pcTop2: '',
      pcTop3: '',
      pcTop4: '',
      //
      mbTop1: '',
      mbTop2: '',
      mbTop3: '',
      mbTop4: '',
      mbTop5: '',
      mbTop6: '',
    }
  },
  created() {
    $(document).ready(() => {
      // Images loaded is zero because we're going to process a new set of images.
      var imagesLoaded = 0
      // Total images is still the total number of <img> elements on the page.
      var totalImages = $('img').length

      const allImagesLoaded = () => {
        this.load = false
      }
      const imageLoaded = () => {
        imagesLoaded++
        if (imagesLoaded === totalImages) {
          allImagesLoaded()
        }
      }
      $('img').each(function(idx, img) {
        $('<img>')
          .on('load', imageLoaded)
          .attr('src', $(img).attr('src'))
      })

      const fnPcTop1 = () => {
        const h = document.getElementById('section1').offsetHeight
        const st = $(window).scrollTop() + $(window).height()
        const top = 'top:' + (h + st / 100 * -15) + 'px'
        this.pcTop1 = top
      }
      const fnPcTop2 = () => {
        const h = document.getElementById('section1').offsetHeight
        const st = $(window).scrollTop() + $(window).height()
        const top = 'top:' + (h + st / 100 * -40) + 'px'
        this.pcTop2 = top
      }
      const fnPcTop3 = () => {
        const h = (document.getElementById('section1').offsetHeight) * 2.5
        const st = $(window).scrollTop() + $(window).height()
        const top = 'top:' + (h + st / 100 * -55) + 'px'
        this.pcTop3 = top
      }
      const fnPcTop4 = () => {
        const h = (document.getElementById('section1').offsetHeight) + (document.getElementById('section2').offsetHeight) + (document.getElementById('section3').offsetHeight) + (document.getElementById('section4').offsetHeight)
        const st = $(window).scrollTop() + $(window).height()
        const top = 'top:' + (h + st / 100 * -40) + 'px'
        this.pcTop4 = top
      }
      // --------------------------------
      // --------------------------------
      const fnMbTop1 = () => {
        const h = (document.getElementById('section1').offsetHeight) * 1
        const st = $(window).scrollTop() + $(window).height()
        const top = 'top:' + (h + st / 100 * -30) + 'px'
        this.mbTop1 = top
      }
      const fnMbTop2 = () => {
        const h = (document.getElementById('section1').offsetHeight) * 3.5
        const st = $(window).scrollTop() + $(window).height()
        const top = 'top:' + (h + st / 100 * -40) + 'px'
        this.mbTop2 = top
      }
      const fnMbTop3 = () => {
        const h = (document.getElementById('section1').offsetHeight) * 3
        const st = $(window).scrollTop() + $(window).height()
        const top = 'top:' + (h + st / 100 * -50) + 'px'
        this.mbTop3 = top
      }
      const fnMbTop4 = () => {
        const h = (document.getElementById('section1').offsetHeight) * 3
        const st = $(window).scrollTop() + $(window).height()
        const top = 'top:' + (h + st / 100 * -38) + 'px'
        this.mbTop4 = top
      }
      const fnMbTop5 = () => {
        const h = (document.getElementById('section1').offsetHeight) * 4
        const st = $(window).scrollTop() + $(window).height()
        const top = 'top:' + (h + st / 100 * -33) + 'px'
        this.mbTop5 = top
      }
      const fnMbTop6 = () => {
        const h = (document.getElementById('section1').offsetHeight) * 7
        const st = $(window).scrollTop() + $(window).height()
        const top = 'top:' + (h + st / 100 * -42) + 'px'
        this.mbTop6 = top
      }
      if (!this.isMobile) {
        const action = () => {
          fnPcTop1()
          fnPcTop2()
          fnPcTop3()
          fnPcTop4()
        }
        setTimeout(() => {
          action()
        }, 1000)
        $(window).scroll(() => {
          action()
        })
      } else {
        const action = () => {
          fnMbTop1()
          fnMbTop2()
          fnMbTop3()
          fnMbTop4()
          fnMbTop5()
          fnMbTop6()
        }
        setTimeout(() => {
          action()
        }, 1000)
        $(window).scroll(() => {
          action()
        })
      }
    })
  },
  mounted() {

  },
  methods: {
    init() {}
  }
}
</script>

<style lang="sass">
@import "src/assets/style/myvar"
#section8
  background:
    color: #000

.waveAni
  animation: tree 5s infinite alternate
  transform: skewY(-15deg)
  transform-origin: 100% 50%
@keyframes tree
  to
    transform: skewY(0)

@media screen and (min-width: $bp-pc)
  $ga: #141F24
  $gb: #4C7589
  $gc: #649EB9
  $gd: #11556E
  $ge: #00202C
  #section2
    background:
      image: linear-gradient(to bottom, #000, #000)

  #section0
    background:
      image: linear-gradient(to bottom, #000, #{$ga})

  #section3
    background:
      image: linear-gradient(to bottom, #{$ga}, #{$gb})

  #section4
    background:
      image: linear-gradient(to bottom, #{$gb}, #{$gc})
  #section5
    background:
      image: linear-gradient(to bottom, #{$gc}, #{$gd})
  #section6
    background:
      image: linear-gradient(to bottom, #{$gd}, #{$ge})
  #section7
    background:
      image: linear-gradient(to bottom, #{$ge}, #000)
@media screen and (max-width: $bp-mb)
  $ga: #41758A
  $gb: #5A92AC
  $gc: #031217
  $gd: #031217
  #section0
    background:
      image: linear-gradient(to bottom, #000 , #000)
  #section3
    background:
      image: linear-gradient(to bottom, #000 10%, #{$ga})
  #section4
    background:
      image: linear-gradient(to bottom, #{$ga}, #{$gb})
  #section5
    background:
      image: linear-gradient(to bottom, #{$gb}, #{$gc})
  #section6
    background:
      image: linear-gradient(to bottom, #{$gc}, #{$gd})
  #section7
    background:
      image: linear-gradient(to bottom, #{$gd}, #000)
</style>

<style lang="sass">
@import url('https://fonts.googleapis.com/css?family=Noto+Serif+TC')
@import "src/assets/style/myvar"
*
  font-family: "Noto Serif TC", serif !important
  letter-spacing: 1px
  // Noto Sans CJK TC  粗細Regular 400
  // Noto Serif CJK TC  粗細Regular 400  Bold 700
.wave
  position: absolute
.wave_l1, .wave_l2
  left: 0
.wave_r1, .wave_r2
  right: 0
section
  // overflow: visible
  position: relative

@media screen and (min-width: $bp-pc)
  .wave_l1, .wave_l2
    left: 0
    width: calc(517 * 100vw / 1920)
  .wave_r1, .wave_r2
    right: 0
    width: calc(517 * 100vw / 1920)

  // --------------------------------
  #section2
    z-index: 2
    .wave_l1
  #section3
    z-index: 3
    .wave_r1
  #section5
    z-index: 1
    .wave_l2
    .wave_r2
@media screen and (max-width: $bp-mb)
  .wave_l1, .wave_l2
    left: 0
    width: calc(100 * 100vw / 375)
  .wave_r1, .wave_r2
    right: 0
    width: calc(172 * 100vw / 375)

  // --------------------------------
  #section3
    padding-top: 1px
    .wave_l1
    .wave_r1
  #section5
    .wave_l2
      width: 60vw
  #section6
    .wave_r1
  #section7
    .wave_l2
      width: 40vw
    .wave_r2
</style>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Playball&display=swap');
@import '../assets/style/variableColor.scss';

.section,
.section .fp-slide,
.section .fp-tableCell {
  height: auto !important;
}

</style>
