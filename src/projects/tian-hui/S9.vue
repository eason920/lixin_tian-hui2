<template>
  <div class="relative">
    <section id="sec9">
      <div v-if="!isMobile" class="pic_pc"></div>
      <div class="sign"
        data-aos-once="false"
        data-aos="fade-up"
        data-aos-delay="0"
        data-aos-duration="1200"
      >
        <img v-if="isMobile" src="./S9/sign_mb.png" />
        <img v-else src="./S9/sign_pc.png" />
      </div>
      <div class="outerBox">
        <div class="msgBox pic_mb">
          <h3
            data-aos-once="false"
            data-aos="fade-up"
            data-aos-delay="0"
            data-aos-duration="800"
          >講究細節低奢品味</h3>
          <div class="tbox">
            <div class="tbox1">
              <h4
              data-aos-once="false"
              data-aos="fade-up"
              data-aos-delay="200"
              data-aos-duration="800"
              >門廳公設｜門廳公設</h4>
              <div
                data-aos-once="false"
                data-aos="fade-up"
                data-aos-delay="200"
                data-aos-duration="800"
              >
                <span v-if="isMobile">What you see is not design , but life. 全球得獎無數、頂尖作品橫跨兩岸，並榮獲亞洲最佳十強的極高榮耀，擅長揉合東方貴氣典雅與西式當代美學。</span>
                <span v-else>What you see is not design , but life. 全球得獎無數、頂尖作品橫跨兩岸，並榮獲亞洲最佳十強的極高榮耀，唐忠漢擅長揉合東方貴氣典雅與西式當代美學，交融出最和諧的效。作品涵蓋星級酒店、會所與兩岸豪宅。</span>
              </div>
            </div>
            <div class="tbox2">
              <h5
                data-aos-once="false"
                data-aos="fade-up"
                data-aos-delay="200"
                data-aos-duration="800"
              >得獎經歷</h5>
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
        <ul class="dot9" v-if="!isMobile">
          <li
            v-for="item in 5"
            :key="'dot9' + item"
            @click="fnDotChange(item)"
          ></li>
        </ul>
        <div class="switchBox">
          <div class="pre" @click="prevBtn"></div>
          <div class="nxt" @click="nextBtn"></div>
          <swiper :options="swiperOption" ref="swiper9">
            <swiper-slide v-for="item in 5" :key="'s9' + item" />
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
          title: '',
          msg: 'Andrew Martin國際室內設計大 獎得主'
        },
        {
          title: '',
          msg: '德國iF傳達設計獎'
        },
        {
          title: '',
          msg: "義大利A'DESIGN AWARD鉑金獎得主"
        },
        {
          title: '',
          msg: '韓國K-Design Award'
        },
        {
          title: '',
          msg: '安邸AD100中國最具影響力100位設計精英'
        },
        {
          title: '',
          msg: '亞太設計師聯盟IAI AWRADS商業空間金獎 '
        },
        {
          title: '',
          msg: '亞太APIDA Living Space Best 10 '
        },
        {
          title: '',
          msg: '台灣室內設計大獎TID獎'
        },
        {
          title: '',
          msg: '中國Idea Stone IDS年度風雲人物'
        }
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
            if (eq >= 5) {
              eq = eq - 5
            }
            $('.dot9 li')
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
      this.$refs.swiper9.$swiper.slidePrev()
    },
    nextBtn() {
      this.$refs.swiper9.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      if (eq >= 5) {
        eq = eq - 5
      }
      this.$refs.swiper9.$swiper.slideTo(eq)
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
#sec9
  position: relative

@media screen and (min-width: $bp-pc)
  $stickyH: 200px
  #sec9
    width: 100vw
    height: calc(45vw + #{$stickyH} )
@media screen and (max-width: $bp-mb)
  #sec9
    // padding-top: 15vw

// ====================================
// == pcPicBox
// ====================================
@media screen and (min-width: $bp-pc)
  .pic_pc
    background:
      image: url( ./S9/bg.png)
      size: cover
      position: 100% 100%
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
      image: url( ./S9/bg.png)
      size: cover
      position: -55vw 100%

// ====================================
// == msgBox
// ====================================
.msgBox
  color: #fff
  text-align: left
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
      weight: lighter
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
        top: 1px
        
      h6
        font:
          size: 12px
          wight: bold
      span
        font:
          size: 12px
          weight: lighter
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
    transform: translateY(-1vw)
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
          

@media screen and (max-width: $bp-mb)
  .msgBox
    color: #000
    padding: 23vw 8vw 2vw
    display: flex
    flex-direction: column
    justify-content: flex-end
    h3

  .tbox
    flex-direction: column
  .tbox1
    h4
      margin: 4vw 0 2vw
      font-size: 17px
    span
      display: block
      padding-right: 40vw
      font:
        weight: bold
      line-height: 1.4
  .tbox2
    color: #fff
    margin-top: 15vw
    h5
      border-bottom: solid 1px #fff
      padding-bottom: 1.5vw
      margin-bottom: 3vw
    ul
      li
        display: none
        &:nth-child(1), &:nth-child(2)
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
    right: 3vw
    bottom: 3vw
    width: 20vw
@media screen and (max-width: $bp-mb)
  .sign
    right: 8vw
    top: 61vw
    width: 24vw

// ====================================
// == OUT BOX
// ====================================
.outerBox

@media screen and (min-width: $bp-pc)
  .outerBox
    position: absolute
    width: 45vw
    bottom: 3vw
    left: 7vw

@media screen and (max-width: $bp-mb)

// ====================================
// == SWIPER v
// ====================================
// 圖片
.swiper-slide
  background:
    position: 0 0
    size: cover
  position: relative

.swiper-slide
  background-repeat: no-repeat
  &:nth-child(1), &:nth-child(6), &:nth-child(11)
    background-image: url('./S9/1.png')

  &:nth-child(2), &:nth-child(7), &:nth-child(12)
    background-image: url('./S9/2.png')

  &:nth-child(3), &:nth-child(8), &:nth-child(13)
    background-image: url('./S9/3.png')

  &:nth-child(4), &:nth-child(9), &:nth-child(14)
    background-image: url('./S9/4.png')

  &:nth-child(5), &:nth-child(10), &:nth-child(15)
    background-image: url('./S9/5.png')

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
    height: 25.2vw // w * 0.562

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
.dot9
  @include swiperCustomDot
@media screen and (min-width: $bp-pc)
  .dot9
    margin-bottom: 1.5vw
    // width: 100px
@media screen and (max-width: $bp-mb)
  .dot9
    display: none

</style>
