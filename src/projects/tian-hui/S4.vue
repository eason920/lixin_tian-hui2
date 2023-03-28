<template>
  <div class="relative">
    <section id="sec4">
      <div
        class="boxp"
        data-aos="fade-up"
        data-aos-duration="1000"
        data-aos-delay="0"
        data-aos-once="false"
      >
        <swiper v-if="hasSwiper" :options="swiperOptions4" ref="swipers4">
          <swiper-slide v-for="(item, i) in swipList" :key="'s4' + i">
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
        <div v-else class="single"><div class="text">榮光公園</div></div>
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
            綠金加持 健康無價
          </div>
          <div
            class="content"
            data-aos="fade-up"
            data-aos-duration="1000"
            data-aos-delay="0"
            data-aos-once="false"
          >
            街道林蔭相隨<br />
            近享榮光公園、石牌公園、<br />
            致遠公園、福興公園等綠蔭環境<br />
            還有軍艦岩、大屯山登高望遠<br />
            打造舒適的親山近綠健康生活
          </div>
          <div
            class="s4tree"
            data-aos-once="false"
            data-aos="fade-in"
            data-aos-duration="1000"
            data-aos-delay="0"
            >
            <img src="./all/tree1.png" />
          </div>
          <butterfly3 class="butt b3"/>
        </div>
        <ul class="dot4"
          v-if="hasSwiper"
          data-aos="fade-up"
          data-aos-duration="1000"
          data-aos-delay="0"
          data-aos-once="false"
        >
          <li
            v-for="item in 2"
            :key="'dot4' + item"
            @click="fnDotChange(item)"
          ></li>
          <!-- :class="[{ active: dotNow === item }]" -->
        </ul>
      </div>
      <!-- deco vv -->
    </section>
  </div>
</template>

<script>
import { isMobile, isTablet } from '@/utils'
import $ from 'jquery'
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'
import butterfly3 from './butterfly3.vue'

export default {
  components: {
    Swiper,
    SwiperSlide,
    butterfly3
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
        '2天母商圈',
        '1天母星巴克',
      ],
      swiperOptions4: {
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
            if (eq >= 2) {
              eq = eq - 2
            }
            // console.log(eq) // 切換啟動前，告訴我現在是第幾個slide
            $('.dot4 li')
              .removeClass('active')
              .eq(eq)
              .addClass('active')
          }
        }
      },
      hasSwiper: false
    }
  },
  methods: {
    prevBtns5() {
      this.$refs.swipers4.$swiper.slidePrev()
    },
    nextBtns5() {
      this.$refs.swipers4.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      // console.log(eq)
      if (eq >= 2) {
        eq = eq - 2
      }
      // console.log(eq)
      this.$refs.swipers4.$swiper.slideTo(eq)
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
  &:nth-child(1), &:nth-child(3), &:nth-child(5)
    background-image: url('./S4/1.jpg')

  &:nth-child(2), &:nth-child(4), &:nth-child(6)
    background-image: url('./S4/2.jpg')

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
// --------------------------------
// -- by case customize
// --------------------------------
#sec4

.boxp

.boxt
  display: flex
  flex-direction: column

@media screen and (min-width: $bp-pc)
  #sec4
    overflow: hidden
    padding: 7vw 0
  .boxp
    width: 60vw
    height: 33vw // w * 0.75 // height 2
    float: right
  .boxt
    float: left
    width: 35vw
    padding-left: 10vw
    justify-content: flex-end
    height: 100%
    position: relative
@media screen and (max-width: $bp-mb)
  #sec4
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
  margin-bottom: 3vw
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
    justify-content: center
    height: 100%
  .title
    margin-bottom: 1vw
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
    margin-bottom: 10vw

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
.dot4
  @include swiperCustomDot
@media screen and (min-width: $bp-pc)
  .dot4
    margin-bottom: 2vw
    // width: 100px
@media screen and (max-width: $bp-mb)
  .dot4
    margin-bottom: 12vw

// --------------------------------
// tree
.s4tree
  position: absolute
  z-index: 3
  right: 0
  img
    width: 100%
    @extend %treeAni

@media screen and (min-width: $bp-pc)
  .s4tree
    width: 12vw
    bottom: -4vw

@media screen and (max-width: $bp-mb)
  .s4tree
    width: 90vw
    bottom: -55vw
    right: -64vw

// butterfly
.butt
  position: absolute
  transform: rotateY(180deg) !important

@media screen and (min-width: $bp-pc)
  .b3
    left: 13vw
    top: 23vw
    width: 2.5vw
@media screen and (max-width: $bp-mb)
  .b3
    right: 9vw
    top: 18vw
    width: 9vw

// single pic
.single
  width: 100%
  height: 100%
  position: relative
  background:
    // color: red
    image: url(./S4/1.jpg)
    size: cover
    position: center

@media screen and (max-width: $bp-mb)
  .single
    height: 106vw
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

</style>
