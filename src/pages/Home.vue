<template>
  <div class="home no-padding-top">
    <Loading :loading="load" />
    <vue-lazy-component class="section maskFixed addBg" id="section1" style="" @init="init">
      <S1 />
    </vue-lazy-component>
    <vue-lazy-component class="section maskFixed addBg" id="section2" @init="init">
      <S2 />
    </vue-lazy-component>
    <vue-lazy-component class="section maskFixed addBg" id="section3" @init="init">
      <S3 />
    </vue-lazy-component>
    <vue-lazy-component class="section maskFixed addBg" id="section4" @init="init">
      <S4 />
    </vue-lazy-component>
    <vue-lazy-component class="section maskFixed addBg" id="section5" @init="init">
      <S5 />
    </vue-lazy-component>
    <vue-lazy-component class="section maskFixed addBg" id="section6" @init="init">
      <S6 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section7" @init="init">
      <S7 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section8" @init="init">
      <S8 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section9" @init="init">
      <S9 />
    </vue-lazy-component>
    <vue-lazy-component class="section maskFixed addBg" id="section10" @init="init">
      <S10 />
    </vue-lazy-component>
    <vue-lazy-component class="section maskFixed addBg" id="section11" @init="init">
      <S11 />
    </vue-lazy-component>
    <vue-lazy-component class="section maskFixed addBg" id="section12" @init="init">
      <S12 />
    </vue-lazy-component>
    <vue-lazy-component class="section maskFixed" id="contact">
      <ContactSection />
    </vue-lazy-component>
    <div class="fixed">帝寶團隊 巨匠建築</div>
    <!-- ======================== -->
    <MobileNav />
  </div>
</template>

<script>
// @ is an alias to /src
import $ from 'jquery'
import { isMobile } from '@/utils'
import ContactSection from '@/layouts/ContactSection.vue'
import MobileNav from '@/layouts/MobileNav.vue'
import Loading from '@/components/Loading.vue'
// import Indigator from '@/components/Indigator.vue'
// import SwiperDemo from '@/projects/tian-hui/swiperDemo_S7_single.vue'
import MClose from '@/projects/tian-hui/MClose.vue'
import S1 from '@/projects/tian-hui/S1.vue'
import S2 from '@/projects/tian-hui/S2.vue'
import S3 from '@/projects/tian-hui/S3.vue'
import S4 from '@/projects/tian-hui/S4.vue'
import S5 from '@/projects/tian-hui/S5.vue'
import S6 from '@/projects/tian-hui/S6.vue'
import S7 from '@/projects/tian-hui/S7.vue'
import S8 from '@/projects/tian-hui/S8.vue'
import S9 from '@/projects/tian-hui/S9.vue'
import S10 from '@/projects/tian-hui/S10.vue'
import S11 from '@/projects/tian-hui/S11.vue'
import S12 from '@/projects/tian-hui/S12.vue'

export default {
  name: 'home',
  components: {
    Loading,
    // Indigator,
    ContactSection,
    MobileNav,
    // SwiperDemo,
    MClose,
    S1,
    S2,
    S3,
    S4,
    S5,
    S6,
    S7,
    S8,
    S9,
    S10,
    S11,
    S12
  },

  data() {
    return {
      isMobile,
      isSide: false,
      load: true,
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
@import url('https://fonts.googleapis.com/css?family=Noto+Serif+TC')
@import "src/assets/style/myvar"
*
  font-family: "sans-serif" !important
  letter-spacing: 1px
  // Noto Sans CJK TC  粗細Regular 400
  // Noto Serif CJK TC  粗細Regular 400  Bold 700
.addBg
  background:
    position: top center
    size: 100% auto
section
  // overflow: visible
  position: relative

@media screen and (min-width: $bp-pc)
  .addBg
    background:
      image: url(../projects/tian-hui/S1/bg_pc.png)
@media screen and (max-width: $bp-mb)
  .addBg
    background:
      image: url(../projects/tian-hui/S1/bg_mb.png)

// FIXED
.fixed
  background-color: rgba(23,23,23, .2)
  color: #fff
  display: flex
  justify-content: center
  align-items: center
  width: 100%
  height: 70px
  position: fixed
  left: 0
  top: 0
  font-size: 25px
  font-weight: bold
  letter-spacing: 3px
  z-index: 20

.maskFixed
  position: relative
  z-index: 99
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
