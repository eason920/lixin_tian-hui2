<template>
  <div class="relative">
    <section id="sec3">
      <div class="s3box" id="box3">
        <div class="s3pic">
          <img v-if="isMobile" src="./S2/bg.jpg" class="basic" />
        </div>
      </div>
      <div class="s3msg"
        data-aos-once="false"
        data-aos="fade-up"
        data-aos-delay="0"
        data-aos-duration="800"
      >
        <div class="s3tbox">
          <div class="s3s">石牌站前 全勝置產</div>
        </div>
        <div class="s3p">
          捷運站通勤+綠蔭公園+優質雙學區<span>+北士科前景+飯店精品=滿分建築</span>
        </div>
      </div>
      <div v-if="!isMobile" class="s3stxt">空拍修照示意</div>
      <div v-else id="fingerbox">
        <div class="finger">
          <img
            src="./S2/finger.png"
            lazy="loaded"
          />
          <span>可左右滑動觀看全景</span>
        </div>
      </div>
    </section>
  </div>
</template>

<style lang="sass" scoped>
@import "src/assets/style/myvar"

@mixin fullScreen
  position: absolute
  top: 0
  right: 0
  bottom: 0
  left: 0
  margin: auto
%centerX
  left: 50%
  transform: translateX(-50%)

%centerY
  top: 50%
  transform: translateY(-50%)
#sec3
  // height: 100vh
.s3box

@media screen and (min-width: $bp-pc)
  // $area: 300px
  .s3pic
    background:
      image: url(./S2/bg.jpg)
      size: contain
      position: 0 100%
      repeat: no-repeat
    font-size: 0
    position: relative
    width: 100vw
    height: 56.25vw
    transition: .1s

@media screen and (max-width: $bp-mb)
  #sec3
    background:
      color: #048fd4
  .s3box
    overflow:
      x: scroll
      y: hidden
    height: 180vw
    position: relative
  .s3pic
    position: relative
    height: 100%
    img
      height: 100%

// --------------------------------
// -- msg
// --------------------------------
.s3msg
  position: absolute
  top: 4vw
  left: 5vw
  color: #fff
  display: flex
  align-items: center
  justify-content: center
.s3tbox
  // width: 496px

.s3s
  font:
    size:100vw * 32 / 1920
    weight: 700

.s3p
  font-size:(100vw * 18 / 1920)
  line-height: 2
  letter-spacing: 2px

@media screen and (min-width: $bp-pc)
  .s3s
    margin:
      right: 1.2vw
  .s3stxt
    position: absolute
    bottom: 1vw
    right: 1vw
    color: #fff
    font-size: (100vw * 12 / 1920)
    text-shadow: 0 2px 3px #000
@media screen and (max-width: $bp-mb)
  .s3pic
    padding-top: 165px
  .s3msg
    top: 10vw
    width: 90vw
    flex-direction: column
  .s3tbox
    width: 100%

  .s3s
    font:
      size: 100vw * 22 / 375
    margin: 15px -10% 15px
    width: 120%

  .s3p
    font:
      size: 100vw * 14 / 375
      weight: lighter
    width: 100%
    span
      display: block
      letter-spacing: 2px
      text-indent: -2px
  .s3stxt
    display: none
// --------------------------------

@media screen and (max-width: $bp-mb)
  @keyframes move
    0%
      transform: translateX(80%)
    to
      transform: translateX(-50%)
  // FINGER BOX
  #fingerbox
    @include fullScreen
    background-image: linear-gradient(to top, rgba(148 ,55 ,85 , 1) , rgba(148 ,55 ,85 , 0) 25%)
    cursor: ew-resize
    transform: .3s
    &.on
      background: rgba(0,102,153,0)
  .finger
    opacity: 1
    transform: .2s
    position: absolute
    left: 50%
    transform: translateX(-50%)
    display: flex
    flex-direction: column
    align-items: center
    justify-content: center
    color: #fff
    font:
      size: 100vw * 12 / 375
    bottom: 10vw
    width: 34vw
    img
      margin-left: -3vw
      width: 6vw
      animation: move 2s ease-in-out infinite alternate-reverse
      margin-bottom: 2vw
</style>

<script>
import $ from 'jquery'
// @ is an alias to /src
import { isMobile, isTablet } from '@/utils'

export default {
  name: 'section1',

  data() {
    return {
      isMobile,
      isTablet
    }
  },

  methods: {
    // fnFingerFadeOut() {
    //   console.log('got')
    //   $('#fingerbox').fadeOut()
    // }
  },

  created() {},

  mounted() {
    if (isMobile) {
      console.log('=========MB=========')
      const $doc = document.getElementById('box3')
      setTimeout(() => {
        let SL =  105 * $doc.offsetWidth / 100  // 位子換成%
        $doc.scrollLeft = SL

        // $('#fingerbox').fadeOut()

        let startX = 0
        $('#fingerbox').on('touchstart', e => {
          $('#fingerbox').addClass('on')

          if (startX === 0) {
            startX = e.targetTouches[0].pageX
          }
          console.log('touchstart', startX)
          // $('.s3box').addClass('move')
        })

        $('#fingerbox').on('touchmove', e => {
          let move = (e.targetTouches[0].pageX - startX) * -1
          switch (true) {
            case move <= -150:
              move = -150
              break
            case move >= 150:
              move = 150
              break
            default:
          }
          $doc.scrollLeft = SL + move
        })

        $('#fingerbox').on('touchend', e => {
          $('#fingerbox').remove()
        })
      }, 1000)
    }
  },

  computed: {}
}
</script>
