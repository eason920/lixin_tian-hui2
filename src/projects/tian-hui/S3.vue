<template>
  <div class="relative">
    <section id="sec3">
      <img v-if="isMobile" src="./S3/mb.png" />
      <img v-else src="./S3/pc.png" />
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
  h3
    margin-bottom: .5vw
    font:
      weight: bold
      size: 21px
  p
    line-height: 1.4
    font:
      size: 14px
.msg
  font-size: 14px
  color: #fff
  text-shadow: 0 0 5px #000,0 0 5px #000, 0 0 5px #000

@media screen and (min-width: $bp-pc)
  .title
    padding: 2vw 2vw
    right: 0
    bottom: 7vw
    width: 29vw
    text-align: left
  .msg
    right: 2vw
    bottom: 2vw
@media screen and (max-width: $bp-mb)
  .title
    padding: 10vw 8vw
    right: 10vw
    top: 23vw
    width: 80vw
    h3
      margin-bottom: 2.5vw
      font-size: 6.5vw
    p
      text-align: left
  .msg
    right: 4vw
    bottom: 6vw
</style>
