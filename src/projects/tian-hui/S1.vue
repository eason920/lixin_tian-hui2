<template>
  <div class="relative">
    <section id="sec1">
      <div class="t_t"
        data-aos="fade-left"
        data-aos-duration="1200"
        data-aos-once="false"
        data-aos-delay="0"
      >
        <div class="boxt">
          <img v-if="isMobile" src="./S1/mb_t.png" />
          <img v-else src="./S1/pc_t.png" />
          <butterfly3 class="butt b3"/>
        </div>
      </div>
      <div class="t_b"
        data-aos="fade-right"
        data-aos-duration="1200"
        data-aos-once="false"
        data-aos-delay="0"
      >
        <div class="boxb">
          <img v-if="isMobile" src="./S1/mb_b.png" />
          <img v-else src="./S1/pc_b.png" />
          <butterfly1 v-if="!isMobile" class="butt b1"/>
          <butterfly2 class="butt b2"/>
        </div>
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
  // background:
  //   position: top center
  //   size: cover
.t_t,
.t_b
  position: absolute

.t_t
  right: 0
  top: 0
.t_b
  left: 0
  bottom: -1vw

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
@media screen and (min-width: $bp-pc)
  #sec1
    height: 100vh
    // background:
    //   image: url(./S1/bg_pc.png)
  .t_t
    height: 100%
    img
      height: 100%
      width: auto
  .t_b
    width: 53vw
    img
      width: 100%
  .logo
    width: 17vw

@media screen and (max-width: $bp-mb)
  #sec1
    height: calc( 100vh - 63px )
    // background:
    //   image: url(./S1/bg_mb.png)
  .t_t
    height: 92%
    img
      height: 100%
  .t_b
    width: 95vw
    img
      width: 100%
  .logo
    width: 45vw

// --------------------------------
.boxt, .boxb
  position: relative
  width: 100%
  height: 100%
.butt
  position: absolute

@media screen and (min-width: $bp-pc)
  .b1
    left: 35%
    top: 10%
    width: 5vw
  .b2
    right: 15%
    top: 50%
    width: 6vw
  .b3
    left: 40%
    top: 22%
    width: 3vw
@media screen and (max-width: $bp-mb)
  .b2
    left: 45%
    top: 51%
    width: 17vw
    transform: rotate(-90deg) !important
  .b3
    right: 54%
    top: 12%
    width: 10vw
    transform: rotateY(180deg) !important
</style>
