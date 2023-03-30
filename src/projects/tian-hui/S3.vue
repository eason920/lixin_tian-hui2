<template>
  <div class="relative">
    <section id="sec3">
      <img v-if="isMobile" src="./S3/mb.jpg" />
      <img v-else src="./S3/pc.jpg" />
      <div class="title"
        data-aos="fade-up"
        data-aos-duration="1200"
        data-aos-once="false"
        data-aos-delay="0"
      >
        <h3>石牌捷運站 快意通勤</h3>
        <p>買屋就選捷運站，生活快意通。一線直通台北數位藝術中心、藝術表演中心、北美館、信義計畫101，並連結北士科園區。假日登山看海，優雅掌握精采生活</p>
      </div>
      <div class="msg">石牌捷運站</div>
    </section>
  </div>
</template>

<script>

import { isMobile, isTablet } from '@/utils'

export default {
  name: 'section3',

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
img
  width: 100%

.title, .msg
  position: absolute
.title
  background:
    color: rgba(148, 55, 85, .9)
  color: #fff
  line-height: 1.45
  text-align: justify
  padding: 2.36em
  font:
    size: 22px
  h3
    margin-bottom: 0.3em
    font:
      weight: bold
      size: 1.59em
  p
    line-height: 1.4
.msg
  font-size: 14px
  color: #fff
  line-height: 1.5
  text-shadow: 0 0 0.36em #000,0 0 0.5em #000
  right: 1em
  bottom: .5em

@media screen and (min-width: $bp-pc)
  .title
    right: 0
    bottom: 3.64em
    width: 27.4em

@media screen and (max-width: 1360px)
  .title
    font:
      size: 14px

@media screen and (max-width: $bp-mb)
  .title
    padding: 2.36em 2em
    right: 0
    left: 0
    margin: auto
    top: 23vw
    width: 21em
    font:
      size: 100vw * 14 / 375
    h3
      font-size: 1.73em
      text-align: center
  .msg
    font-size: 12px
</style>
