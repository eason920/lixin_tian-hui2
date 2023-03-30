<template>
  <div class="relative">
    <section id="sec7">
      <div v-if="!isMobile" class="pic_pc"></div>
      <div class="sign"
        data-aos-once="false"
        data-aos="fade-up"
        data-aos-delay="0"
        data-aos-duration="1200"
      >
        <img v-if="isMobile" src="./S7/sign_mb.png" />
        <img v-else src="./S7/sign_pc.png" />
      </div>
      <div class="outerBox">
        <div class="msgBox pic_mb">
          <h3
            data-aos-once="false"
            data-aos="fade-up"
            data-aos-delay="0"
            data-aos-duration="800"
          >國際美學藝術地景</h3>
          <div class="tbox">
            <div class="tbox1">
              <h4
              data-aos-once="false"
              data-aos="fade-up"
              data-aos-delay="200"
              data-aos-duration="800"
              >建築規劃｜三門建築師事務所</h4>
              <div
                data-aos-once="false"
                data-aos="fade-up"
                data-aos-delay="200"
                data-aos-duration="800"
              >
                <span v-if="isMobile">台灣豪宅御用建築團隊，與英美日澳香港葡萄牙義大利等世界頂尖事務所共同合作，創造台灣傲視群雄的地景藝術，是上市企業總部百貨旗艦大型開發案的合作首選。</span>
                <span v-else>台灣豪宅御用建築團隊，與英美日澳香港葡萄牙義大利等世界頂尖事務所共同合作，創造台灣傲視群雄的地景藝術，是上市企業總部百貨旗艦大型開發案的合作首選。</span>
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
        <ul class="dot7" v-if="!isMobile">
          <li
            v-for="item in 3"
            :key="'dot7' + item"
            @click="fnDotChange(item)"
          ></li>
        </ul>
        <div class="switchBox">
          <div class="pre" @click="prevBtn"></div>
          <div class="nxt" @click="nextBtn"></div>
          <swiper :options="swiperOption" ref="swiper7">
            <swiper-slide v-for="item in 3" :key="'s7' + item" />
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
          title: '百貨商場．國際旅館',
          msg: '微風廣場、萬豪酒店、美福酒店'
        },
        {
          title: '企業大樓．整體開發',
          msg: '台中•台灣塔、國泰金融中心、群光電子總部、元大企業總部<br/>長虹科技大樓、南港展覽館、遠揚新世紀'
        },
        {
          title: '指標豪宅',
          msg: '信義之心、元大一品苑、天母紘琚'
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
            if (eq >= 3) {
              eq = eq - 3
            }
            $('.dot7 li')
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
      this.$refs.swiper7.$swiper.slidePrev()
    },
    nextBtn() {
      this.$refs.swiper7.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      if (eq >= 3) {
        eq = eq - 3
      }
      this.$refs.swiper7.$swiper.slideTo(eq)
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
#sec7
  position: relative
  overflow: hidden

@media screen and (min-width: $bp-pc)
  $stickyH: 200px
  #sec7
    width: 100%
    height: calc(45vw + #{$stickyH} )
@media screen and (max-width: $bp-mb)
  #sec7
    // padding-top: 15vw

// ====================================
// == pcPicBox
// ====================================
@media screen and (min-width: $bp-pc)
  .pic_pc
    background:
      image: url( ./S7/bg.jpg)
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
      image: url( ./S7/bg.jpg)
      size: cover
      position: 79% 100%

// ====================================
// == msgBox
// ====================================
.msgBox
  color: #fff
  text-align: justify
  font:
    size: 15px
  line-height: 1.5
  h3
    font:
      weight: bold
      size: 2.6em
.tbox
  display: flex
.tbox1
  h4
    font:
      weight: bold
      size: 1.53em
  span
    font:
      weight: lighter
.tbox2
  h5
    font:
      weight: bold
  ul
    margin-left: 20px
    font:
      size: 0.8em
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
          wight: bold
      span
        font:
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
  $wh5: 3em
  .tbox2
    width: calc( 100% - #{$g} - #{$wt1})
    display: flex
    h5
      width: $wh5
      line-height: 1.3
      border-right: solid 1px #fff
      padding-right: 3px
      margin-right: 5px
      text-align: left

    ul
      width: calc( 100% - #{$wh5} - 5px)
          
@media screen and (max-width: 1730px)  
  .msgBox
    font:
      size: 15 * 100vw / 1920
@media screen and (max-width: 1160px)  
  .tbox
    width: 115%
  $wt1: 45%
  $g: 3%
  .tbox1
    width: $wt1
  .tbox2
    width: calc( 100% - #{$g} - #{$wt1})
@media screen and (max-width: 960px)  
  .msgBox
    margin: 0 0 0 -15%

@media screen and (max-width: $bp-mb)
  .msgBox
    color: #000
    padding: 30vw 8vw 2vw
    margin: auto
    display: flex
    flex-direction: column
    justify-content: flex-end
    font:
      size: 12 * 100vw / 375
    h3
      font:
        size: 1.8em


  .tbox
    flex-direction: column
    width: auto
  .tbox1
    width: auto
    h4
      margin: 2vw 0 2vw
      font:
        size: 1.15em
    span
      display: block
      padding-right: 32vw
      line-height: 1.4
  .tbox2
    width: auto
    color: #fff
    margin-top: 15vw
    h5
      border-bottom: solid 1px #fff
      padding-bottom: 1.5vw
      margin-bottom: 3vw
    ul
      li
        display: none
        &:nth-child(1)
          display: block
// ====================================
// == SIGN
// ====================================
.sign
  position: absolute
  img
    width: 100%

@media screen and (min-width: $bp-pc)
  .sign
    right: 4vw
    bottom: 4vw
    width: 20vw
@media screen and (max-width: $bp-mb)
  .sign
    right: 21vw
    top: 81vw
    width: 21vw

// ====================================
// == OUT BOX
// ====================================
.outerBox

@media screen and (min-width: $bp-pc)
  .outerBox
    position: absolute
    width: 45vw
    bottom: 1vw
    left: 10vw

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
  &:nth-child(1), &:nth-child(4), &:nth-child(7)
    background-image: url('./S7/1.jpg')

  &:nth-child(2), &:nth-child(5), &:nth-child(8)
    background-image: url('./S7/2.jpg')

  &:nth-child(3), &:nth-child(6), &:nth-child(9)
    background-image: url('./S7/3.jpg')

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
.dot7
  @include swiperCustomDot
@media screen and (min-width: $bp-pc)
  .dot7
    margin-bottom: 1.5vw
    // width: 100px
@media screen and (max-width: $bp-mb)
  .dot7
    display: none

</style>
