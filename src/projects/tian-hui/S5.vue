<template>
  <div class="relative">
    <section id="sec5">
      <div
        class="boxp"
        data-aos="fade-up"
        data-aos-duration="1000"
        data-aos-delay="0"
        data-aos-once="false"
      >
        <swiper :options="swiperOptions5" ref="swipers5">
          <swiper-slide v-for="(item, i) in swipList" :key="'s5' + i">
            <div class="item">
              <div class="text">{{ item }}</div>
            </div>
          </swiper-slide>
          <template v-slot:button-prev>
            <div class="swiper-button-prev" @click="prevBtns5"></div>
          </template>
          <template v-slot:button-next>
            <div class="swiper-button-next" @click="nextBtns5"></div>
          </template>
          <template v-slot:pagination>
            <div class="swiper-pagination"></div>
          </template>
        </swiper>
      </div>
      <div class="boxt">
        <div class="deco">
          <div
            class="title"
            data-aos="fade-up"
            data-aos-duration="1000"
            data-aos-delay="0"
            data-aos-once="false"
          >
            方圓之內 食尚玩家
        <div class="bird"
          data-aos="fade-up"
          data-aos-duration="1000"
          data-aos-delay="0"
          data-aos-once="false"
        >
          <img src="./S1/bird1.png" />
        </div>
          </div>
          <div
            class="content"
            data-aos="fade-up"
            data-aos-duration="1000"
            data-aos-delay="0"
            data-aos-once="false"
          >
            石牌路一段商家繁華不斷線<br/>
            自強市場是行家的新鮮廚房<br/>
            天母異國餐廳是美食饕客的味蕾饗宴<br/>
            還有各色拿手大饌小食都為生活增添好滋味<br/>
          </div>
        </div>
        <ul class="dot5"
          data-aos="fade-up"
          data-aos-duration="1000"
          data-aos-delay="0"
          data-aos-once="false"
        >
          <li
            v-for="item in 3"
            :key="'dot5' + item"
            @click="fnDotChange(item)"
          ></li>
          <!-- :class="[{ active: dotNow === item }]" -->
        </ul>
      </div>
    </section>
  </div>
</template>

<script>
import { isMobile, isTablet } from '@/utils'
import $ from 'jquery'
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'

export default {
  components: {
    Swiper,
    SwiperSlide
  },

  computed: {
    // dotNow() {
    //   return 1
    // }
  },

  data() {
    return {
      isMobile,
      isTablet,
      swipList: [
        '天母商圈',
        '天母商圈',
        '天母星巴克',
      ],
      swiperOptions5: {
        slidesPerView: 1,
        loop: true, // 是否 slide 後循環
        // initialSlide: 0, // 最初 pic index
        // slidesPerView: 'auto',
        spaceBetween: 0,
        autoplay: {
          delay: 1500,
          disableOnInteraction: false // 換頁後是否停止 autoplay
        },
        speed: 1000,
        grabCursor: true,
        pagination: {
          el: '.swiper-pagination',
          clickable: true,
          type: 'bullets'
        },
        on: {
          slideChangeTransitionEnd: function() {
            // console.log(this.activeIndex) // 切換結束時，告訴我現在是第幾個slide
          },
          slideChangeTransitionStart: function() {
            let eq = this.activeIndex
            // console.log(eq)
            if (eq >= 3) {
              eq = eq - 3
            }
            // console.log(eq) // 切換啟動前，告訴我現在是第幾個slide
            $('.dot5 li')
              .removeClass('active')
              .eq(eq)
              .addClass('active')
          }
        }
      }
    }
  },
  methods: {
    prevBtns5() {
      this.$refs.swipers5.$swiper.slidePrev()
    },
    nextBtns5() {
      this.$refs.swipers5.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      // console.log(eq)
      if (eq >= 3) {
        eq = eq - 3
      }
      // console.log(eq)
      this.$refs.swipers5.$swiper.slideTo(eq)
    }
  }
}
</script>

<style lang="sass" scoped>
@import "src/assets/style/myvar"

// 上下頁
.swiper-button-prev,
.swiper-button-next
  width: 50px
  height: 80px
  &:after
    color: #fff
    // text-shadow: 0px 0px 5px rgba(0, 0, 0, 0.5), 0px 0px 5px rgba(0, 0, 0, 0.5)

@media screen and (max-width: $bp-mb)
  .swiper-button-prev,
  .swiper-button-next
    width: 30px !important
    top: 50%
    transform: translateY(-20%)
    &:after
      font-size: 32px

// 圖片
.swiper-slide
  background:
    position: center
    size: cover
  &:nth-child(1), &:nth-child(4), &:nth-child(7)
    background-image: url('./S5/1.jpg')

  &:nth-child(2), &:nth-child(5), &:nth-child(8)
    background-image: url('./S5/2.jpg')

  &:nth-child(3), &:nth-child(6), &:nth-child(9)
    background-image: url('./S5/3.jpg')

// 總高
@media screen and (min-width: $bp-pc)
  .swiper-container, // height 1
  .swiper-wrapper,
  .swiper-slide,
  .item
    height: 100%
    // max-height: 70vh
@media screen and (max-width: $bp-mb) and (orientation: portrait)
  .swiper-container,
  .swiper-wrapper,
  .swiper-slide,
  .item
    height: 106vw

@media screen and (max-width: $bp-mb) and (orientation: landscape)
  .swiper-container,
  .swiper-wrapper,
  .swiper-slide,
  .item
    height: 100vh

// --------------------------------
// -- 我內部介面
// --------------------------------
.item
  position: relative

.text
  font:
    size: 14px
  line-height: 1.5
  position: absolute
  right: 1em
  bottom: .5em
  color: #fff
  text-shadow: 0 0 0.36em #000,0 0 0.5em #000
@media screen and (max-width: $bp-mb)
  .text
    font:
      size: 12px


// ------------------nextBtns4--------------
// -- by case customize
// --------------------------------
#sec5

.boxp

.boxt
  display: flex
  flex-direction: column

@media screen and (min-width: $bp-pc)
  #sec5
    overflow: hidden
    padding: 7vw 0
  .boxp
    width: 60vw
    height: 33vw // w * 0.75 // height 2
    float: left
  .boxt
    // float: right
    // width: 35vw
    // padding-right: 10vw
    justify-content: flex-end
    height: 100%
    position: relative
@media screen and (max-width: $bp-mb)
  #sec5
    display: flex
    flex-direction: column
  .boxp
    order: 2

  .boxt
    order: 1

// right msg

.boxt
  position: relative
  z-index: 1
  font:
    size: 22px

$pl: 40px
.deco
  // padding-left: $pl
  margin-bottom: 2em
  position: relative
  color: #fff
  display: flex
  align-items: flex-start
  flex-direction: column
  text-align: left
  line-height: 1.45
  width: 21em
  margin: auto

.title
  color: $c_pink
  // margin: 20px 0 40px
  font:
    size: 1.59em
    weight: bold

.content
  color: #333

.bird
  img
    width: 100%

@media screen and (min-width: $bp-pc)
  .boxt
    height: 33vw
    // padding-bottom: 7.5vw
  .deco
    display: flex
    justify-content: flex-end
    height: 100%
  .title
    position: absolute
    width: 1em
    top: 0
    right: 0
    line-height: 1.05

  .content
    // font-size: 100vw * 22 / 1920

  .bird
    width: 1.55em
    float: right
    margin: 
      top: .5em
@media screen and (max-width: 1490px)  
  .boxt
    height: 36vw
  .boxp
    height: 36vw
    width: 55vw
@media screen and (max-width: 1360px)  
  .boxt
    font:
      size: 14px
    height: 32vw
  .boxp
    height: 32vw
@media screen and (max-width: 980px)  
  .boxt
    height: 40vw
  .boxp
    height: 40vw
    width: 53vw
  
@media screen and (max-width: $bp-mb)
  .boxp
    height: auto
    width: 100%
  .boxt
    margin: 10vw 8vw 0
    font-size: 100vw * 14 / 375
    height: auto

  .deco
    margin-bottom: 4vw
    margin: auto
    width: 100%

  .title
    margin-bottom: 5vw
    font:
      size: 1.78em

  .content
  .bird
    position: absolute
    right: -5vw
    bottom: -21vw
    width: 14vw
// dot
.dot5
  @include swiperCustomDot
@media screen and (min-width: $bp-pc)
  .dot5
    margin: .8em auto 1em auto
    width: 21em
    // width: 100px
@media screen and (max-width: $bp-mb)
  .dot5
    margin: 1.5em auto 3em 0
</style>

<style lang="scss">
// ----------------------------
// -- 不可 sass (?!!!!) 也不可 scoped
// ----------------------------
@import 'src/assets/style/myvar';
// 輪撥點點點的顯示 & 美術
.swiper-container-horizontal
  > .swiper-pagination-bullets
  .swiper-pagination-bullet {
  &.swiper-pagination-bullet-active {
    background: #f2f2f2;
  }
}

.swiper-container-horizontal
  > .swiper-pagination-bullets
  .swiper-pagination-bullet {
  display: none;
}

// ???
// #s5 {
//   .swiper-container-horizontal > .swiper-pagination-bullets {
//     bottom: auto;
//     top: 999px;
//   }
// }

// @media screen and (max-width: $bp-mb) {
// ??
// #s5 {
//   .swiper-container-horizontal > .swiper-pagination-bullets {
//     display: none;
//   }
// }
</style>
