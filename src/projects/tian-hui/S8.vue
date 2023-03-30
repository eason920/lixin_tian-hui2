<template>
  <div class="relative">
    <section id="sec8">
      <div v-if="!isMobile" class="pic_pc"></div>
      <div class="sign"
        data-aos-once="false"
        data-aos="fade-up"
        data-aos-delay="0"
        data-aos-duration="1200"
      >
        <img v-if="isMobile" src="./S8/sign_mb.png" />
        <img v-else src="./S8/sign_pc.png" />
      </div>
      <div class="outerBox">
        <div class="msgBox pic_mb">
          <h3
            data-aos-once="false"
            data-aos="fade-up"
            data-aos-delay="0"
            data-aos-duration="800"
          >耐震六級安全制霸</h3>
          <div class="tbox">
            <div class="tbox1">
              <h4
              data-aos-once="false"
              data-aos="fade-up"
              data-aos-delay="200"
              data-aos-duration="800"
              >結構設計｜織本構造株式會社</h4>
              <div
                data-aos-once="false"
                data-aos="fade-up"
                data-aos-delay="200"
                data-aos-duration="800"
              >
                <span v-if="isMobile">日商織本構造總公司位於東京，是日本首屈一指的抗震權威，於2011年在台成立分公司，將日本抗震建築引進台灣，一生懸命的職人精神，並以百年建築為基礎。</span>
                <span v-else>日商織本構造總公司位於東京，是日本首屈一指的抗震權威，於2011年在台成立分公司，將日本抗震建築引進台灣，一生懸命的職人精神，讓織本構造從不放過任何一個結構細節，並以百年建築為基礎，確保建築堅固如山，構築安心家園。</span>
              </div>
            </div>
            <div class="tbox2">
              <h5
                data-aos-once="false"
                data-aos="fade-up"
                data-aos-delay="200"
                data-aos-duration="800"
              >代表作品</h5>
              <ul>
                <li v-for="(item, i) in workShipList" :key="i+item.title"
                  data-aos-once="false"
                  data-aos="fade-up"
                  data-aos-delay="200"
                  data-aos-duration="800"
                >
                  <h6>{{ item.title }}</h6>
                  <span v-html="item.msg"></span>
                </li>
              </ul>
            </div>
          </div>
        </div>
        <ul class="dot8" v-if="!isMobile">
          <li
            v-for="item in 4"
            :key="'dot8' + item"
            @click="fnDotChange(item)"
          ></li>
        </ul>
        <div class="switchBox">
          <div class="pre" @click="prevBtn"></div>
          <div class="nxt" @click="nextBtn"></div>
          <swiper :options="swiperOption" ref="swiper8">
            <swiper-slide v-for="item in 4" :key="'s8' + item" />
          </swiper>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import $ from 'jquery'
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'

import { isMobile, isTablet } from '@/utils'

export default {
  name: 'swiper-example-thumbs-gallery',
  title: 's4',
  components: {
    Swiper,
    SwiperSlide
  },

  data() {
    return {
      vm: this,
      isMobile,
      isTablet,
      workShipList: [
        {
          title: '台灣作品',
          msg: '宏盛帝寶、信義之星、忠泰風格、東騰千里等頂尖豪宅'
        },
        {
          title: '日本作品',
          msg: '國際連合大學本部設施、東京國際展示場、韓國漢城羅德世界<br/>東京都藝術文化會館、北澤美術館、橫濱市立美術館<br/>琦玉縣立大學、西武百貨、JR東海大廈'
        },
      ],
      swiperOption: {
        loop: true,
        slidesPerView: 1,
        spaceBetween: 0,
        autoplay: {
          delay: 4000,
          disableOnInteraction: false
        },
        speed: 800,
        on: {
          slideChangeTransitionStart: function() {
            let eq = this.activeIndex
            if (eq >= 4) {
              eq = eq - 4
            }
            $('.dot8 li')
              .removeClass('active')
              .eq(eq)
              .addClass('active')
          }
        }
      }
    }
  },

  methods: {
    prevBtn() {
      this.$refs.swiper8.$swiper.slidePrev()
    },
    nextBtn() {
      this.$refs.swiper8.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      if (eq >= 3) {
        eq = eq - 3
      }
      this.$refs.swiper8.$swiper.slideTo(eq)
    }
  },

  created() {},

  mounted() {},

  computed: {}
}
</script>

<style lang="sass" scoped>
@import "src/assets/style/myvar"
@import ./sass/share

// ====================================
// == 架構
// ====================================
#sec8
  position: relative
  overflow: hidden

@media screen and (min-width: $bp-pc)
  $stickyH: 200px
  #sec8
    width: 100%
    height: calc(45vw + #{$stickyH} )
@media screen and (max-width: $bp-mb)
  #sec8
    // padding-top: 15vw

// ====================================
// == pcPicBox
// ====================================
@media screen and (min-width: $bp-pc)
  .pic_pc
    background:
      image: url( ./S8/bg.jpg)
      size: cover
      position: 0% 100%
    position: absolute
    left: 0
    top: 0
    width: 100%
    height: 100%

@media screen and (max-width: $bp-mb)
  $stickyH: 200px
  .pic_mb
    // height: calc(45vw + #{$stickyH} )
    background:
      image: url( ./S8/bg.jpg)
      size: cover
      position: -21vw 100%

// ====================================
// == msgBox
// ====================================
.msgBox
  color: #fff
  text-align: justify
  h3
    font:
      weight: bold
      size: 23px
.tbox
  display: flex
.tbox1
  h4
    font:
      weight: bold
      size: 15px
  span
    font:
      size: 12px
      weight: revert
.tbox2
  h5
    font:
      weight: bold
      size: 13px
  ul
    margin-left: 20px
    li
      position: relative
      padding-bottom: 8px
      &:before
        content: "◎"
        position: absolute
        left: -16px
        top: -1px
        
      h6
        font:
          size: 12px
          wight: bold
      span
        font:
          size: 12px
          weight: revert
@media screen and (min-width: $bp-pc)
  .msgBox
    h3
  .tbox
    justify-content: space-between
    margin-bottom: 1.5vw
  $wt1: 40%
  $g: 3%
  .tbox1
    width: $wt1
    h4
      padding:
        top: 20px
        bottom: 8px
    span
  $wh5: 35px
  .tbox2
    width: calc( 100% - #{$g} - #{$wt1})
    display: flex
    h5
      width: $wh5
      line-height: 1.3
      border-right: solid 1px #fff
      padding-right: 3px
      margin-right: 5px
    ul
      width: calc( 100% - #{$wh5})
      li
        h6
        span

@media screen and (max-width: 1160px) 
  .tbox
    width: 105%
  $wt1: 45%
  $g: 3%
  .tbox1
    width: $wt1
  .tbox2
    width: calc( 100% - #{$g} - #{$wt1})
@media screen and (max-width: 960px)  
  .msgBox
    margin: 0 0 0 -20%
@media screen and (max-width: $bp-mb)
  $l: 32vw
  .msgBox
    color: #000
    padding: 14vw 5vw 2vw
    // height: 100vw
    display: flex
    flex-direction: column
    margin: auto
    // justify-content: fle=…
    h3
      padding-left: $l
  .tbox
    flex-direction: column
    width: auto
  .tbox1
    padding-left: $l
    width: auto
    h4
      margin: 4vw 0 2vw
      font-size: 15px
    span
      display: block
      line-height: 1.4
  .tbox2
    color: #fff
    margin-top: 32vw
    width: auto
    h5
      border-bottom: solid 1px #fff
      padding-bottom: 1.5vw
      margin-bottom: 3vw
    ul
      li
        display: none
        &:nth-child(1)
          display: block
        h6
        span
// ====================================
// == SIGN
// ====================================
.sign
  position: absolute
  img
    width: 100%

@media screen and (min-width: $bp-pc)
  .sign
    left: 4vw
    bottom: 4vw
    width: 20vw
@media screen and (max-width: $bp-mb)
  .sign
    right: 10vw
    top: 71vw
    width: 26vw

// ====================================
// == OUT BOX
// ====================================
.outerBox

@media screen and (min-width: $bp-pc)
  .outerBox
    position: absolute
    width: 45vw
    bottom: 0vw
    right: 7vw

@media screen and (max-width: $bp-mb)

// ====================================
// == SWIPER v
// ====================================
// 圖片
.swiper-slide
  background:
    position: 0 0
    size: contain
  position: relative

.swiper-slide
  background-repeat: no-repeat
  &:nth-child(1), &:nth-child(5), &:nth-child(9)
    background-image: url('./S8/1.jpg')

  &:nth-child(2), &:nth-child(6), &:nth-child(10)
    background-image: url('./S8/2.jpg')

  &:nth-child(3), &:nth-child(7), &:nth-child(11)
    background-image: url('./S8/3.jpg')

  &:nth-child(4), &:nth-child(8), &:nth-child(12)
    background-image: url('./S8/4.jpg')

// W/H
.switchBox
  font-size: 0
  overflow: hidden
.swiper-container
  z-index: 2
  overflow: hidden
@media screen and (min-width: $bp-pc)
  // h
  .swiper-container, // height
  .swiper-wrapper,
  .swiper-slide
    height: 28.2vw // w * 0.562

  // w
  .swiper-container
    width:  45vw

  // gurter
  .switchBox
    position: relative

@media screen and (max-width: $bp-mb)
  // h
  .swiper-container, // height
  .swiper-wrapper,
  .swiper-slide
    height: 46vw // w * 2.87

  // w
  .swiper-container
    width: 80vw

  // gurter
  .switchBox
    position: relative
    background-color: #525B64
    padding: 10vw 0

// --------------------------------
// PRE NEX
.switchBox
  position: relative

.pre, .nxt
  display: block
  position: absolute
  width: 0
  padding-left: 18px!important // 真正 width 控制
  height: 20px
  font:
    size: 20px
  z-index: 4
  cursor: pointer
  background:
    size: contain
  top: 50%
  transform: translateY(-50%)
  background:
    repeat: no-repeat

.pre
  background:
    image: url("./all/prev-btn.png")
    repeat: no-repeat

.nxt
  background:
    image: url("./all/next-btn.png")

@media screen and (min-width: $bp-pc)
  $lr: 2vw
  .pre
    left: $lr

  .nxt
    right: $lr

@media screen and (max-width: $bp-mb)
  $lr: 12vw
  .pre, .nxt
    padding-left: 15px!important // 真正 width 控制
    height: 20px
  .pre
    left: $lr

  .nxt
    right: $lr

// ====================================
// == DOT
// ====================================
.dot8
  @include swiperCustomDot
@media screen and (min-width: $bp-pc)
  .dot8
    margin-bottom: 1.5vw
    // width: 100px
@media screen and (max-width: $bp-mb)
  .dot8
    display: none

</style>
