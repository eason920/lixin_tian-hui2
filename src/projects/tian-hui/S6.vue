<template>
  <div class="relative">
    <section id="sec6">
      <div
        class="boxp"
        data-aos="fade-up"
        data-aos-duration="1000"
        data-aos-delay="0"
        data-aos-once="false"
      >
        <swiper v-if="hasSwiper" :options="swiperOptions6" ref="swipers6">
          <swiper-slide v-for="(item, i) in swipList" :key="'s6' + i">
            <div class="item">
              <div class="text">{{ item }}</div>
            </div>
          </swiper-slide>
          <template v-slot:button-prev>
            <div class="swiper-button-prev" @click="prevBtns6"></div>
          </template>
          <template v-slot:button-next>
            <div class="swiper-button-next" @click="nextBtns6"></div>
          </template>
          <template v-slot:pagination>
            <div class="swiper-pagination"></div>
          </template>
        </swiper>
        <div v-else class="single"></div>
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
            石牌中小學 高知識殿堂
          </div>
          <div
            class="content"
            data-aos="fade-up"
            data-aos-duration="1000"
            data-aos-delay="0"
            data-aos-once="false"
          >
            石牌中小學、美日學校、歐洲小學等名校林立科技菁英、榮總振興陽明醫界名人、外交官員為孩子一致選擇的聰慧環境
          </div>
          <tree2 class="tree" />
          <butterfly2 class="b2"/>
        </div>
        <ul class="dot6"
          v-if="hasSwiper"
          data-aos="fade-up"
          data-aos-duration="1000"
          data-aos-delay="0"
          data-aos-once="false"
        >
          <li
            v-for="item in 3"
            :key="'dot6' + item"
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
import butterfly2 from './butterfly2.vue'
import tree2 from './tree2.vue'

export default {
  components: {
    Swiper,
    SwiperSlide,
    butterfly2,
    tree2
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
        '台北美國學校',
        '石牌國中',
        '石牌國小',
      ],
      swiperOptions6: {
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
            $('.dot6 li')
              .removeClass('active')
              .eq(eq)
              .addClass('active')
          }
        }
      },
      hasSwiper: true
    }
  },
  methods: {
    prevBtns6() {
      this.$refs.swipers6.$swiper.slidePrev()
    },
    nextBtns6() {
      this.$refs.swipers6.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      // console.log(eq)
      if (eq >= 3) {
        eq = eq - 3
      }
      // console.log(eq)
      this.$refs.swipers6.$swiper.slideTo(eq)
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
    background-image: url('./S6/1.jpg')

  &:nth-child(2), &:nth-child(5), &:nth-child(8)
    background-image: url('./S6/2.jpg')

  &:nth-child(3), &:nth-child(6), &:nth-child(9)
    background-image: url('./S6/3.jpg')

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
// --------------------------------
// -- by case customize
// --------------------------------
#sec6

.boxp

.boxt
  display: flex
  flex-direction: column

@media screen and (min-width: $bp-pc)
  #sec6
    overflow: hidden
    padding: 7vw 0
  .boxp
    width: 60vw
    height: 38vw // w * 0.75 // height 2
    float: right
  .boxt
    height: 38vw
    justify-content: flex-end
    position: relative
@media screen and (max-width: $bp-mb)
  #sec6
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
  margin-bottom: 2em
  position: relative
  color: #fff
  display: flex
  align-items: flex-start
  flex-direction: column
  text-align: left
  line-height: 1.45
  width: 21em
  margin: auto 2em auto auto

.title
  color: $c_pink
  // margin: 20px 0 40px
  font:
    size: 1.59em
    weight: bold

.content
  color: #333

.bird
  position: absolute
  img
    width: 100%

@media screen and (min-width: $bp-pc)
  .deco
    margin-bottom: 1vw
    display: flex
    justify-content: flex-end
    height: 100%
    position: relative
  .title
    position: absolute
    left: 0
    top: 0vw
    width: 0
    line-height: 1.05

  .bird
    right: 8.5vw
    top: 230px
    width: 5vw
@media screen and (max-width: 1640px)  
  .boxt
  .deco
    width: 20em
@media screen and (max-width: 1360px)  
  .boxt
    font:
      size: 14px
@media screen and (max-width: 920px)  
  .boxp
    height: 47vw // w * 0.75 // height 2
  .boxt
    height: 47vw
  .deco
    width: 15em
@media screen and (max-width: $bp-mb)
  .boxp
    height: auto
  .boxt
    margin: 10vw 8vw 0
    height: auto

  .deco
    margin: auto auto 10vw auto
    width: auto

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
.dot6
  @include swiperCustomDot
  justify-content: flex-end
@media screen and (min-width: $bp-pc)
  .dot6
    margin: .8em 2em 1em auto
    // width: 100px
@media screen and (max-width: $bp-mb)
  .dot6
    margin: 1.5em 0 3em auto

// --------------------------------
// tree
.tree
  position: absolute
  z-index: 3
  right: 0

@media screen and (min-width: $bp-pc)
  .tree
    bottom: 14vw
    left: -7vw
    width: 10vw
@media screen and (max-width: 1640px)  
  .tree
    bottom: 8em
    left: -6em
@media screen and (max-width: 1490px)  
  .tree
    bottom: 7.3em
    left: -6.5em
@media screen and (max-width: 1360px)  
  .tree
    bottom: 13.3em
    left: -6.5em
@media screen and (max-width: 1180px)  
  .tree
    bottom: 9.3em
    left: -7em
@media screen and (max-width: 920px)  
  .tree
    bottom: 9.3em
    left: -6em
@media screen and (max-width: $bp-mb)
  .tree
    width: 32vw
    bottom: -28vw
    left: -13vw

// butterfly
.b2
  position: absolute

@media screen and (min-width: $bp-pc)
  .b2
    left: 2vw
    bottom: 12vw
    width: 4vw
@media screen and (max-width: $bp-mb)
  .b2
    left: 15vw
    top: 26vw
    width: 11vw

// single pic
.single
  width: 100%
  height: 100%
  background:
    // color: red
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
