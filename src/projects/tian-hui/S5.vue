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
        <div class="bird"
          data-aos="fade-up"
          data-aos-duration="1000"
          data-aos-delay="0"
          data-aos-once="false"
        >
          <img src="./all/bird_pink.png" />
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
    background-image: url('./S5/1.png')

  &:nth-child(2), &:nth-child(5), &:nth-child(8)
    background-image: url('./S5/2.png')

  &:nth-child(3), &:nth-child(6), &:nth-child(9)
    background-image: url('./S5/3.png')

// 總高
@media screen and (min-width: $bp-pc)
  .swiper-container, // height 1
  .swiper-wrapper,
  .swiper-slide,
  .item
    height: 33vw
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
  line-height: 1.7
  position: absolute
  right: .5em
  bottom: .3em
  color: #fff
  text-shadow: 0px 0px 5px rgba(0, 0, 0, 0.5), 0px 0px 5px rgba(0, 0, 0, 0.5)
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
    float: right
    width: 35vw
    padding-right: 10vw
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

$pl: 40px
.deco
  // padding-left: $pl
  margin-bottom: 40px
  position: relative
  color: #fff
  display: flex
  align-items: flex-start
  flex-direction: column
  text-align: left

.title
  color: $c_pink
  // margin: 20px 0 40px
  font:
    size: 28px
    weight: bold

.content
  color: #333
  font:
    size: 100vw * 18 / 1920
    weibht: bold
  line-height: 1.5
  text-align: justify

.bird
  position: absolute
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
    width: 28px
    top: 0
    right: 0
  .content
    font-size: 100vw * 22 / 1920

  .bird
    right: 8.5vw
    top: 230px
    width: 5vw
@media screen and (max-width: $bp-mb)
  .boxt
    margin: 18vw 8vw 0

  .deco
    margin-bottom: 4vw

  .title
    margin-bottom: 5vw
    font-size: 23px

  .content
    font-size: 100vw * 13 / 375
  .bird
    right: -5vw
    bottom: -1vw
    width: 20vw
// dot
.dot5
  @include swiperCustomDot
@media screen and (min-width: $bp-pc)
  .dot5
    margin-bottom: 2vw
    // width: 100px
@media screen and (max-width: $bp-mb)
  .dot5
    margin-bottom: 12vw
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
