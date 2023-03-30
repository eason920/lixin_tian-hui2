<template>
  <div class="relative">
    <section id="sec1">
      <div class="imgtt"
        data-aos="fade-left"
        data-aos-duration="1200"
        data-aos-once="false"
        data-aos-delay="0">
        <img src="./S1/00.png" class="imgbg">
        <div class="leaf leaf1"><img src="./S1/leaf.png" alt="leaf" /></div>
        <div class="leaf leaf3"><img src="./S1/leaf.png" alt="leaf" /></div>
        <img src="./S1/tree2.png" class="tree2" alt="tree" />
        <div class="leaf leaf5"><img src="./S1/leaf.png" alt="leaf" /></div>
        <div class="leaf bird2"><img src="./S1/bird2.png" alt="bird" /></div>
        <butterfly3 class="butt b3"/>
      </div>
      
      <div class="imgtb"
        data-aos="fade-right"
        data-aos-duration="1200"
        data-aos-once="false"
        data-aos-delay="0">
        <img src="./S1/00.png" class="imgbg">
        <div class="leaf leafmo1" v-if="isMobile"><img src="./S1/leaf.png" alt="leaf" /></div>
        <div class="leaf leafmo2" v-if="isMobile"><img src="./S1/leaf.png" alt="leaf" /></div>
        <div class="leaf leaf2"><img src="./S1/leaf.png" alt="leaf" /></div>
        <div class="leaf leaf2"><img src="./S1/leaf.png" alt="leaf" /></div>
        <div class="leaf leaf2"><img src="./S1/leaf.png" alt="leaf" /></div>
        <img src="./S1/tree1.png" class="tree1" alt="tree" />
        <div class="leaf leaf4"><img src="./S1/leaf.png" alt="leaf" /></div>
        <div class="leaf bird1"><img src="./S1/bird1.png" alt="bird" /></div>
        <butterfly1 v-if="!isMobile" class="butt b1"/>
        <butterfly2 class="butt b2"/><!--  -->
      </div>
      <div class="logo"
        data-aos="fade-up"
        data-aos-duration="1500"
        data-aos-once="false"
        data-aos-delay="0"
      >
        <img src="./S1/logo.png" class="logo logo_logo">
      </div>
    </section>
  </div>
</template>

<script>
import { isMobile, isTablet } from '@/utils'
import butterfly1 from './butterfly1.vue'
import butterfly2 from './butterfly2.vue'
import butterfly3 from './butterfly3.vue'

export default {
  name: 'section1',
  components: {
    butterfly1,
    butterfly2,
    butterfly3,
  },
  data() {
    return {
      isMobile,
      isTablet
    }
  },

  methods: {},

  created() {},

  mounted() {},

  computed: {}
}
</script>

<style lang="sass" scoped>
@import "src/assets/style/myvar"
#sec1
  overflow: hidden
.logo
  position: absolute
  top: 0
  right: 0
  bottom: 0
  left: 0
  margin: auto
  img
    width: 100%
.logo_logo
  transform: translateY(-3vw)
@keyframes an 
  to
    transform: translateX(0%)
.imgtt
  position: absolute
  right: 0
  top: 0
  height: 100%
  .imgbg
    height: 100%
.imgtb
  position: absolute
  left: 0
  bottom: 0
  width: 50%
  .imgbg
    width: 100%
  
.leaf
  position: absolute
  animation: an 5s alternate infinite
  img
    width: 100%
.leaf1
  width: 69%
  right: 43%
  top: -22%
  transform: skewX(-3deg)
  transform-origin: 50% -20%
  img
    transform: rotate(2.35deg)
.leaf3
  width: 119%
  right: -51%
  top: -16%
  transform: skewX(4deg)rotate(3deg)
  transform-origin: 40% 60%
  img
    transform: rotate(-165deg)
    
.tree2
  position: absolute
  width: 29%
  right: 6%
  top: 18%
.leaf5
  width: 140%
  right: -97%
  top: 26%
  transform: skewY(3deg)
  transform-origin: 60% 50%
  img
    transform: rotate(2.35deg)
.bird2
  width: 20%
  right: 8%
  top: 20%
  transform: rotate(-5deg)
  transform-origin: 30% 50%
  animation-duration: 2s
  
.butt
  position: absolute
.b3
  left: 31%
  top: 22%
  width: 5%
.b2
  left: 85%
  bottom: 20%
  width: 14%
.b1
  left: 44%
  bottom: 53%
  width: 5%
.leaf2
  width: 102%
  left: -42%
  bottom: 8%
  transform: skewX(-5deg)rotate(-3deg)
  transform-origin: 50% 57%
  img
    transform: rotate(-165deg)
.tree1
  position: absolute
  width: 23%
  left: 3%
  bottom: -1%
.leaf4
  width: 155%
  left: -31%
  bottom: -62.5%
  transform: skewX(3deg)rotate(-2deg)
  transform-origin: 50% 80%
  img
    transform: rotate(-180deg)
.bird1
  width: 9%
  left: 12%
  bottom: 31%
  transform: rotate(5deg)
  transform-origin: 50% 100%
  animation-duration: 2s
  

@media screen and (min-width: $bp-pc)
  #sec1
    height: 100vh
    min-height: calc(900 * 100vw / 1920)
    max-height: calc(1080 * 100vw / 1920)
  .logo
    width: 17vw

@media screen and (max-width: $bp-mb)
  #sec1
    height: calc( 100vh - 63px )
    min-height: calc(604 * 100vw / 375)
    max-height: calc(750 * 100vw / 375)
  .logo
    width: 45vw
    
  .imgtt
    right: 0
    top: 0
    height: auto
    width: 100%
    .imgbg
      height: auto
      width: 100%
  .imgtb
    width: 100%
    height: 100%
    // background: url(./S1/mb_b.png) bottom
    // background-size: 100% auto
  .leaf1
    width: 87%
    right: 19%
    top: -32%
  .leaf3
    width: 128%
    right: -70%
    top: -32%
    img
      transform: rotate(-200deg)
  .tree2
    width: 40%
    right: -13%
    top: 14%
    z-index: 1
  .leaf5
    width: 80%
    right: -63%
    top: 34%
    img
      transform: rotate(125deg)
  .bird2
    width: 20%
    right: 7%
    top: 15%
    z-index: 1
  .b3
    left: 35%
    top: 23%
    width: 7%
  .b2
    left: 42%
    bottom: 35vw
    width: 17%
  .leaf2
    width: 105%
    left: -50%
    bottom: calc(40% + (46 - 667 * .4) * 100vw / 375)
  .tree1
    width: 31%
    left: -3%
    bottom: calc(35% + (-20 - 667 * .35) * 100vw / 375)
  .leaf4
    width: 155%
    left: -40%
    bottom: calc(20% + (-230 - 667 * .2) * 100vw / 375)
  .bird1
    width: 10%
    left: 11.5%
    bottom: calc(35% + (145 - 667 * .35) * 100vw / 375)
  .leafmo1
    width: 88%
    left: -43.5%
    bottom: calc(35% + (100 - 667 * .35) * 100vw / 375)
    transform: skewY(-3deg)
    transform-origin: 80% 50%
    img
     transform: rotate(90deg)
  .leafmo2
    width: 100%
    left: 65.5%
    bottom: calc(40% + (70 - 667 * .4) * 100vw / 375)
    transform: skewX(-3deg)rotate(-3deg)
    transform-origin: 50% 50%
    z-index: 1
    img
     transform: rotate(10deg)
</style>
